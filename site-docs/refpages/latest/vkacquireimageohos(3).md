# vkAcquireImageOHOS(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkAcquireImageOHOS.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkAcquireImageOHOS - Obtain the ownership of a swapchain image, and push the external Fence into the [VkSemaphore](VkSemaphore.html) object and the [VkFence](VkFence.html) object

To obtain the ownership of a swapchain image, call:

// Provided by VK_OHOS_native_buffer
VkResult vkAcquireImageOHOS(
    VkDevice                                    device,
    VkImage                                     image,
    int32_t                                     nativeFenceFd,
    VkSemaphore                                 semaphore,
    VkFence                                     fence);

* 
`device` is a valid `VkDevice` object used to create the
swapchain image.

* 
`image` is the target image.

* 
`nativeFenceFd` is a file descriptor of the native fence.

* 
`semaphore` is [VK_NULL_HANDLE](VK_NULL_HANDLE.html) or a [VkSemaphore](VkSemaphore.html) that will
be signaled when the nativeFenceFd is signaled.

* 
`fence` is [VK_NULL_HANDLE](VK_NULL_HANDLE.html) or [VkFence](VkFence.html) that will be
signaled when the nativeFenceFd is signaled.

Valid Usage (Implicit)

* 
[](#VUID-vkAcquireImageOHOS-device-parameter) VUID-vkAcquireImageOHOS-device-parameter

 `device` **must** be a valid [VkDevice](VkDevice.html) handle

* 
[](#VUID-vkAcquireImageOHOS-image-parameter) VUID-vkAcquireImageOHOS-image-parameter

 `image` **must** be a valid [VkImage](VkImage.html) handle

* 
[](#VUID-vkAcquireImageOHOS-semaphore-parameter) VUID-vkAcquireImageOHOS-semaphore-parameter

 If `semaphore` is not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), `semaphore` **must** be a valid [VkSemaphore](VkSemaphore.html) handle

* 
[](#VUID-vkAcquireImageOHOS-fence-parameter) VUID-vkAcquireImageOHOS-fence-parameter

 If `fence` is not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), `fence` **must** be a valid [VkFence](VkFence.html) handle

* 
[](#VUID-vkAcquireImageOHOS-image-parent) VUID-vkAcquireImageOHOS-image-parent

 `image` **must** have been created, allocated, or retrieved from `device`

* 
[](#VUID-vkAcquireImageOHOS-semaphore-parent) VUID-vkAcquireImageOHOS-semaphore-parent

 If `semaphore` is a valid handle, it **must** have been created, allocated, or retrieved from `device`

* 
[](#VUID-vkAcquireImageOHOS-fence-parent) VUID-vkAcquireImageOHOS-fence-parent

 If `fence` is a valid handle, it **must** have been created, allocated, or retrieved from `device`

Return Codes

[Success](../../../../spec/latest/chapters/fundamentals.html#fundamentals-successcodes)

* 
`VK_SUCCESS`

[Failure](../../../../spec/latest/chapters/fundamentals.html#fundamentals-errorcodes)

* 
`VK_ERROR_OUT_OF_HOST_MEMORY`

* 
`VK_ERROR_UNKNOWN`

* 
`VK_ERROR_VALIDATION_FAILED`

[VK_OHOS_native_buffer](VK_OHOS_native_buffer.html), [VkDevice](VkDevice.html), [VkFence](VkFence.html), [VkImage](VkImage.html), [VkSemaphore](VkSemaphore.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/resources.html#vkAcquireImageOHOS).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
