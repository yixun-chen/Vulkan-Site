# VkSwapchainImageUsageFlagBitsOHOS(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkSwapchainImageUsageFlagBitsOHOS.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkSwapchainImageUsageFlagBitsOHOS - Bitmask specifying the usage of a swapchain image on Open Harmony OS platform

Bits which **can** be set in [VkSwapchainImageCreateInfoOHOS](VkSwapchainImageCreateInfoOHOS.html)::`usage`
specifying the usage of swapchain image on Open Harmony OS platform are:

// Provided by VK_OHOS_native_buffer
typedef enum VkSwapchainImageUsageFlagBitsOHOS {
    VK_SWAPCHAIN_IMAGE_USAGE_SHARED_BIT_OHOS = 0x00000001,
} VkSwapchainImageUsageFlagBitsOHOS;

* 
`VK_SWAPCHAIN_IMAGE_USAGE_SHARED_BIT_OHOS` specifies that
[VkSwapchainImageCreateInfoOHOS](VkSwapchainImageCreateInfoOHOS.html) is used for creating a swapchain
image whose internal native buffer can be shared for access by other
applications.

[VK_OHOS_native_buffer](VK_OHOS_native_buffer.html), [VkSwapchainImageUsageFlagsOHOS](VkSwapchainImageUsageFlagsOHOS.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/resources.html#VkSwapchainImageUsageFlagBitsOHOS).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
