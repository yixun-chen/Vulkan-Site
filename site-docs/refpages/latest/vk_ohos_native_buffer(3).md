# VK_OHOS_native_buffer(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VK_OHOS_native_buffer.html

## Table of Contents

- [Name](#_name)
- [VK_OHOS_native_buffer](#VK_OHOS_native_buffer)
- [Other Extension Metadata](#_other_extension_metadata)
- [Other_Extension_Metadata](#_other_extension_metadata)
- [Description](#_description)
- [New Base Types](#_new_base_types)
- [New_Base_Types](#_new_base_types)
- [New Commands](#_new_commands)
- [New Structures](#_new_structures)
- [New Enums](#_new_enums)
- [New Bitmasks](#_new_bitmasks)
- [New Enum Constants](#_new_enum_constants)
- [New_Enum_Constants](#_new_enum_constants)
- [Version History](#_version_history)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VK_OHOS_native_buffer - device extension

**Name String**

`VK_OHOS_native_buffer`

**Extension Type**

Device extension

**Registered Extension Number**

589

**Revision**

1

**Ratification Status**

Not ratified

**Extension and Version Dependencies**

None

**Contact**

* 
Weilan Chen [wchen-h](https://github.com/KhronosGroup/Vulkan-Docs/issues/new?body=[VK_OHOS_native_buffer] @wchen-h%0A*Here describe the issue or question you have about the VK_OHOS_native_buffer extension*)

**Last Modified Date**

2025-10-13

**IP Status**

No known IP claims.

**Contributors**

* 
Weilan Chen, Huawei

* 
Zehui Lin, Huawei

* 
Pan Gao, Huawei

* 
Yang Shi, Huawei

This extension allows an application to acquire the ownership of an image,
 use it and then release the ownership.
 It also supports an application
to import the external fence to sync the usage of the image.

* 
`OHBufferHandle`

* 
[vkAcquireImageOHOS](vkAcquireImageOHOS.html)

* 
[vkGetSwapchainGrallocUsageOHOS](vkGetSwapchainGrallocUsageOHOS.html)

* 
[vkQueueSignalReleaseImageOHOS](vkQueueSignalReleaseImageOHOS.html)

* 
Extending [VkImageCreateInfo](VkImageCreateInfo.html):

[VkSwapchainImageCreateInfoOHOS](VkSwapchainImageCreateInfoOHOS.html)

Extending [VkImageCreateInfo](VkImageCreateInfo.html), [VkBindImageMemoryInfo](VkBindImageMemoryInfo.html):

* 
[VkNativeBufferOHOS](VkNativeBufferOHOS.html)

Extending [VkPhysicalDeviceProperties2](VkPhysicalDeviceProperties2.html):

* 
[VkPhysicalDevicePresentationPropertiesOHOS](VkPhysicalDevicePresentationPropertiesOHOS.html)

* 
[VkSwapchainImageUsageFlagBitsOHOS](VkSwapchainImageUsageFlagBitsOHOS.html)

* 
[VkSwapchainImageUsageFlagsOHOS](VkSwapchainImageUsageFlagsOHOS.html)

* 
`VK_OHOS_NATIVE_BUFFER_EXTENSION_NAME`

* 
`VK_OHOS_NATIVE_BUFFER_SPEC_VERSION`

* 
Extending [VkStructureType](VkStructureType.html):

`VK_STRUCTURE_TYPE_NATIVE_BUFFER_OHOS`

* 
`VK_STRUCTURE_TYPE_PHYSICAL_DEVICE_PRESENTATION_PROPERTIES_OHOS`

* 
`VK_STRUCTURE_TYPE_SWAPCHAIN_IMAGE_CREATE_INFO_OHOS`

* 
Revision 1, 2025-10-13 (Weilan Chen)

Internal revisions

No cross-references are available

For more information, see the [Vulkan Specification](../../../../spec/latest/appendices/extensions.html#VK_OHOS_native_buffer).

This page is a generated document.
Fixes and changes should be made to the generator scripts, not directly.
