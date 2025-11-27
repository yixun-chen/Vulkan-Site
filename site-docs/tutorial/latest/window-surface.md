# Window surface

## Metadata

- **Component**: tutorial
- **Version**: latest
- **URL**: /tutorial/latest/03_Drawing_a_triangle/01_Presentation/00_Window_surface.html

## Table of Contents

- [Window surface creation](#_window_surface_creation)
- [Window_surface_creation](#_window_surface_creation)
- [Querying for presentation support](#_querying_for_presentation_support)
- [Querying_for_presentation_support](#_querying_for_presentation_support)
- [Creating the presentation queue](#_creating_the_presentation_queue)
- [Creating_the_presentation_queue](#_creating_the_presentation_queue)

## Content

Since Vulkan is a platform-agnostic API, it is not designed to interface
directly with the window system on its own. To establish the connection
between Vulkan and the window system to present results to the screen, we
need to use the WSI (Window System Integration) extensions. In this chapter
we’ll discuss the first one, which is `VK_KHR_surface`. It exposes a
`VkSurfaceKHR` object that represents an abstract type of surface to
present rendered images to. The surface in our program will be backed by
the window that we’ve already opened with GLFW.

The `VK_KHR_surface` extension is an instance level extension, and we’ve actually
already enabled it, because it’s included in the list returned by
`glfwGetRequiredInstanceExtensions`. The list also includes some other WSI
extensions that we’ll use in the next couple of chapters.

The window surface needs to be created right after the instance creation,
because it can actually influence the physical device selection. The reason we
postponed this is that window surfaces are part of the larger topic of
render targets and presentation for which the explanation would have cluttered
the basic setup. It should also be noted that window surfaces are an entirely
optional component in Vulkan if you just need off-screen rendering. Vulkan
allows you to do that without hacks like creating an invisible window
(necessary for OpenGL).  Vulkan also allows you to remotely render from a
non-presenting GPU or remotely over the internet, or run compute
acceleration for AI without a render or presentation target.

While GLFW will be demonstrated here, the concept of Vulkan rendering to a
surface is repeated as a target for any other Windowing API. This concept
applies to mobile and to work with direct access to the windowing manager.
That said, let’s for now, concentrate on GLFW and see how it concretely
works in this tutorial.

Start by adding a `surface` class member right below the debug callback.

vk::raii::SurfaceKHR surface = nullptr;

Although the `VkSurfaceKHR` object and its usage is platform-agnostic, its
creation isn’t because it depends on window system details. For example, it
needs the `HWND` and `HMODULE` handles on Windows. Therefore, there is a
platform-specific addition to the extension, which on Windows is called
`VK_KHR_win32_surface` and is also automatically included in the list from
`glfwGetRequiredInstanceExtensions`.

I will demonstrate how this platform-specific extension can be used to create a
surface on Windows, but we won’t use it in this tutorial. It doesn’t
make any sense to use a library like GLFW and then proceed to use
platform-specific code anyway. GLFW actually has `glfwCreateWindowSurface` that
handles the platform differences for us. Still, it’s good to see what it does
behind the scenes before we start relying on it.

To access native platform functions, you need to update the includes at the top:

#define VK_USE_PLATFORM_WIN32_KHR
#define GLFW_INCLUDE_VULKAN
#include 
#define GLFW_EXPOSE_NATIVE_WIN32
#include 

Because a window surface is a Vulkan object, it comes with a
`VkWin32SurfaceCreateInfoKHR` struct that needs to be filled in. It has two
important parameters: `hwnd` and `hinstance`. These are the handles to the
window and the process.

VkWin32SurfaceCreateInfoKHR createInfo{};
createInfo.sType = VK_STRUCTURE_TYPE_WIN32_SURFACE_CREATE_INFO_KHR;
createInfo.hwnd = glfwGetWin32Window(window);
createInfo.hinstance = GetModuleHandle(nullptr);

The `glfwGetWin32Window` function is used to get the raw `HWND` from the GLFW
window object. The `GetModuleHandle` call returns the `HINSTANCE` handle of the
current process.

After that the surface can be created with `vkCreateWin32SurfaceKHR`, which
includes a parameter for the instance, surface creation details, custom
allocators and the variable for the surface handle to be stored in.
Technically, this is a WSI extension function, but it is so commonly used
that the standard Vulkan loader includes it, so unlike other extensions, you
don’t need to explicitly load it.

if (vkCreateWin32SurfaceKHR(instance, &createInfo, nullptr, &surface) != VK_SUCCESS) {
    throw std::runtime_error("failed to create window surface!");
}

The process is similar for other platforms like Linux, where
`vkCreateXcbSurfaceKHR` takes an XCB connection and window as creation details
with X11.

The `glfwCreateWindowSurface` function performs exactly this operation with a
different implementation for each platform. We’ll now integrate it into our
program. Add a function `createSurface` to be called from `initVulkan` right
after instance creation and `setupDebugMessenger`.

void initVulkan() {
    createInstance();
    setupDebugMessenger();
    createSurface();
    pickPhysicalDevice();
    createLogicalDevice();
}

void createSurface() {

}

The GLFW call takes simple parameters instead of a struct which makes the
implementation of the function very straightforward:

void createSurface() {
    VkSurfaceKHR       _surface;
    if (glfwCreateWindowSurface(*instance, window, nullptr, &_surface) != 0) {
        throw std::runtime_error("failed to create window surface!");
    }
    surface = vk::raii::SurfaceKHR(instance, _surface);
}

However, as you see in the above, GLFW only deals with the Vulkan C API.
The VkSurfaceKHR object is a C API object.  Thankfully, it can natively be
promoted to the C++ wrapper, and that’s what we do here.

The parameters are the `VkInstance`, GLFW window pointer, custom allocators and
pointer to `VkSurfaceKHR` variable. It simply passes through the `VkResult` from
the relevant platform call. GLFW doesn’t offer a special function for destroying
a surface, but wrapping it in our raii SurfaceKHR object will let Vulkan
RAII take care of that for us.

Although the Vulkan implementation may support window system integration, that
does not mean that every device in the system supports it. Therefore, we need to
extend `createLogicalDevice` to ensure that a device can present images to the
surface we created. Since the presentation is a queue-specific feature, the
problem is actually about finding a queue family that supports presenting to the
surface we created.

It’s actually possible that the queue families supporting drawing commands and
the queue families supporting presentation do not overlap. Therefore, we
have to take into account that there could be a distinct presentation queue.

Next, we’ll look for a queue family that has the capability of presenting
to our window surface. The function to check for that is
`vkGetPhysicalDeviceSurfaceSupportKHR`, which takes the  physical device,
queue family index and surface as parameters. Add a call to it
in the same loop as the `VK_QUEUE_GRAPHICS_BIT`:

VkBool32 presentSupport = physicalDevice.getSurfaceSupportKHR( graphicsIndex, *surface );

Then check the value of the boolean and store the presentation family
queue index:

if (presentSupport) {
    indices.presentFamily = i;
}

Note that it’s very likely that these end up being the same queue family after
all, but throughout the program we will treat them as if they were separate
queues for a uniform approach. Nevertheless, you could add logic to explicitly
prefer a physical device that supports drawing and presentation in the same
queue for improved performance.

The one thing that remains is modifying the logical device creation procedure to
create the presentation queue and retrieve the `VkQueue` handle. Add a member
variable for the handle:

vk::raii::Queue presentQueue;

std::vector deviceExtensions = {
    vk::KHRSwapchainExtensionName,
    vk::KHRSpirv14ExtensionName,
    vk::KHRSynchronization2ExtensionName,
    vk::KHRCreateRenderpass2ExtensionName
};

Next, we need to modify the filtering logic to find the best queue families
to use as we detect them.  Here’s how we do it in one function at the device
creation functions:

void createLogicalDevice() {
    // find the index of the first queue family that supports graphics
    std::vector queueFamilyProperties = physicalDevice.getQueueFamilyProperties();

    // get the first index into queueFamilyProperties which supports graphics
    auto graphicsQueueFamilyProperty = std::ranges::find_if( queueFamilyProperties, []( auto const & qfp )
                    { return (qfp.queueFlags & vk::QueueFlagBits::eGraphics) != static_cast(0); } );

    auto graphicsIndex = static_cast( std::distance( queueFamilyProperties.begin(), graphicsQueueFamilyProperty ) );

    // determine a queueFamilyIndex that supports present
    // first check if the graphicsIndex is good enough
    auto presentIndex = physicalDevice.getSurfaceSupportKHR( graphicsIndex, *surface )
                                       ? graphicsIndex
                                       : static_cast( queueFamilyProperties.size() );
    if ( presentIndex == queueFamilyProperties.size() )
    {
        // the graphicsIndex doesn't support present -> look for another family index that supports both
        // graphics and present
        for ( size_t i = 0; i ( i ), *surface ) )
            {
                graphicsIndex = static_cast( i );
                presentIndex  = graphicsIndex;
                break;
            }
        }
        if ( presentIndex == queueFamilyProperties.size() )
        {
            // there's nothing like a single family index that supports both graphics and present -> look for another
            // family index that supports present
            for ( size_t i = 0; i ( i ), *surface ) )
                {
                    presentIndex = static_cast( i );
                    break;
                }
            }
        }
    }
    if ( ( graphicsIndex == queueFamilyProperties.size() ) || ( presentIndex == queueFamilyProperties.size() ) )
    {
        throw std::runtime_error( "Could not find a queue for graphics or present -> terminating" );
    }

    // query for Vulkan 1.3 features
    auto features = physicalDevice.getFeatures2();
    vk::PhysicalDeviceVulkan13Features vulkan13Features;
    vk::PhysicalDeviceExtendedDynamicStateFeaturesEXT extendedDynamicStateFeatures;
    vulkan13Features.dynamicRendering = vk::True;
    extendedDynamicStateFeatures.extendedDynamicState = vk::True;
    vulkan13Features.pNext = &extendedDynamicStateFeatures;
    features.pNext = &vulkan13Features;
    // create a Device
    float                     queuePriority = 0.5f;
    vk::DeviceQueueCreateInfo deviceQueueCreateInfo { .queueFamilyIndex = graphicsIndex, .queueCount = 1, .pQueuePriorities = &queuePriority };
    vk::DeviceCreateInfo      deviceCreateInfo{ .pNext =  &features, .queueCreateInfoCount = 1, .pQueueCreateInfos = &deviceQueueCreateInfo };
    deviceCreateInfo.enabledExtensionCount = deviceExtensions.size();
    deviceCreateInfo.ppEnabledExtensionNames = deviceExtensions.data();

    device = vk::raii::Device( physicalDevice, deviceCreateInfo );
    graphicsQueue = vk::raii::Queue( device, graphicsIndex, 0 );
    presentQueue = vk::raii::Queue( device, presentIndex, 0 );
}

In case the queue families are the same, the two handles will most likely have
the same value now. In the [next chapter](01_Swap_chain.html), we’re going to look at swap chains and
how they allow us to present images to the surface.

[C++ code](../../_attachments/05_window_surface.cpp)
