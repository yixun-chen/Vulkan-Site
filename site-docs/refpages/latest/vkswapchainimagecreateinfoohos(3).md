# VkSwapchainImageCreateInfoOHOS(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkSwapchainImageCreateInfoOHOS.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkSwapchainImageCreateInfoOHOS - The parameters needed to create a swapchain image on Open Harmony OS platform

The `VkSwapchainImageCreateInfoOHOS` structure is defined as:

// Provided by VK_OHOS_native_buffer
typedef struct VkSwapchainImageCreateInfoOHOS {
    VkStructureType                   sType;
    const void*                       pNext;
    VkSwapchainImageUsageFlagsOHOS    usage;
} VkSwapchainImageCreateInfoOHOS;

* 
`sType` is a [VkStructureType](VkStructureType.html) value identifying this structure.

* 
`pNext` is `NULL` or a pointer to a structure extending this
structure.

* 
`usage` is a bitmask of [VkSwapchainImageUsageFlagBitsOHOS](VkSwapchainImageUsageFlagBitsOHOS.html)
specifying the usage of swapchain image.

Valid Usage (Implicit)

* 
[](#VUID-VkSwapchainImageCreateInfoOHOS-sType-sType) VUID-VkSwapchainImageCreateInfoOHOS-sType-sType

 `sType` **must** be `VK_STRUCTURE_TYPE_SWAPCHAIN_IMAGE_CREATE_INFO_OHOS`

* 
[](#VUID-VkSwapchainImageCreateInfoOHOS-usage-parameter) VUID-VkSwapchainImageCreateInfoOHOS-usage-parameter

 `usage` **must** be a valid combination of [VkSwapchainImageUsageFlagBitsOHOS](VkSwapchainImageUsageFlagBitsOHOS.html) values

* 
[](#VUID-VkSwapchainImageCreateInfoOHOS-usage-requiredbitmask) VUID-VkSwapchainImageCreateInfoOHOS-usage-requiredbitmask

 `usage` **must** not be `0`

[VK_OHOS_native_buffer](VK_OHOS_native_buffer.html), [VkStructureType](VkStructureType.html), [VkSwapchainImageUsageFlagsOHOS](VkSwapchainImageUsageFlagsOHOS.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/resources.html#VkSwapchainImageCreateInfoOHOS).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
