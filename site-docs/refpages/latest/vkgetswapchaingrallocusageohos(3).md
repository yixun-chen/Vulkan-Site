# vkGetSwapchainGrallocUsageOHOS(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkGetSwapchainGrallocUsageOHOS.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkGetSwapchainGrallocUsageOHOS - Obtain the proper Gralloc usage flag according to the given Vulkan device, image format and image usage flag

To obtain the Gralloc usage flag of a swapchain, call:

// Provided by VK_OHOS_native_buffer
VkResult vkGetSwapchainGrallocUsageOHOS(
    VkDevice                                    device,
    VkFormat                                    format,
    VkImageUsageFlags                           imageUsage,
    uint64_t*                                   grallocUsage);

* 
`device` is a valid `VkDevice` object used to create the
swapchain image.

* 
`format` is a [VkFormat](VkFormat.html) value specifying the format of the
given image.

* 
`grallocUsage` is a bitmask for setting a mask of zero or more
`OH_NativeBuffer_Usage`, which is defined in the C APIs references
documentation of Open Harmony OS Graphics Module.

Valid Usage (Implicit)

* 
[](#VUID-vkGetSwapchainGrallocUsageOHOS-device-parameter) VUID-vkGetSwapchainGrallocUsageOHOS-device-parameter

 `device` **must** be a valid [VkDevice](VkDevice.html) handle

* 
[](#VUID-vkGetSwapchainGrallocUsageOHOS-format-parameter) VUID-vkGetSwapchainGrallocUsageOHOS-format-parameter

 `format` **must** be a valid [VkFormat](VkFormat.html) value

* 
[](#VUID-vkGetSwapchainGrallocUsageOHOS-imageUsage-parameter) VUID-vkGetSwapchainGrallocUsageOHOS-imageUsage-parameter

 `imageUsage` **must** be a valid combination of [VkImageUsageFlagBits](VkImageUsageFlagBits.html) values

* 
[](#VUID-vkGetSwapchainGrallocUsageOHOS-imageUsage-requiredbitmask) VUID-vkGetSwapchainGrallocUsageOHOS-imageUsage-requiredbitmask

 `imageUsage` **must** not be `0`

* 
[](#VUID-vkGetSwapchainGrallocUsageOHOS-grallocUsage-parameter) VUID-vkGetSwapchainGrallocUsageOHOS-grallocUsage-parameter

 `grallocUsage` **must** be a valid pointer to a `uint64_t` value

Return Codes

[Success](../../../../spec/latest/chapters/fundamentals.html#fundamentals-successcodes)

* 
`VK_SUCCESS`

[Failure](../../../../spec/latest/chapters/fundamentals.html#fundamentals-errorcodes)

* 
`VK_ERROR_INITIALIZATION_FAILED`

* 
`VK_ERROR_UNKNOWN`

* 
`VK_ERROR_VALIDATION_FAILED`

[VK_OHOS_native_buffer](VK_OHOS_native_buffer.html), [VkDevice](VkDevice.html), [VkFormat](VkFormat.html), [VkImageUsageFlags](VkImageUsageFlags.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/resources.html#vkGetSwapchainGrallocUsageOHOS).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
