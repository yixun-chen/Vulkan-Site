# vkGetPhysicalDeviceFormatProperties(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkGetPhysicalDeviceFormatProperties.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkGetPhysicalDeviceFormatProperties - Lists physical device’s format capabilities

To query supported format features which are properties of the physical
device, call:

|  | This functionality is superseded by [Vulkan Version 1.1](../../../../spec/latest/appendices/versions.html#versions-1.1). See [Legacy Functionality](../../../../spec/latest/appendices/legacy.html#legacy-gpdp2) for more information. |
| --- | --- |

// Provided by VK_VERSION_1_0
void vkGetPhysicalDeviceFormatProperties(
    VkPhysicalDevice                            physicalDevice,
    VkFormat                                    format,
    VkFormatProperties*                         pFormatProperties);

* 
`physicalDevice` is the physical device from which to query the
format properties.

* 
`format` is the format whose properties are queried.

* 
`pFormatProperties` is a pointer to a [VkFormatProperties](VkFormatProperties.html)
structure in which physical device properties for `format` are
returned.

Valid Usage (Implicit)

* 
[](#VUID-vkGetPhysicalDeviceFormatProperties-physicalDevice-parameter) VUID-vkGetPhysicalDeviceFormatProperties-physicalDevice-parameter

 `physicalDevice` **must** be a valid [VkPhysicalDevice](VkPhysicalDevice.html) handle

* 
[](#VUID-vkGetPhysicalDeviceFormatProperties-format-parameter) VUID-vkGetPhysicalDeviceFormatProperties-format-parameter

 `format` **must** be a valid [VkFormat](VkFormat.html) value

* 
[](#VUID-vkGetPhysicalDeviceFormatProperties-pFormatProperties-parameter) VUID-vkGetPhysicalDeviceFormatProperties-pFormatProperties-parameter

 `pFormatProperties` **must** be a valid pointer to a [VkFormatProperties](VkFormatProperties.html) structure

[VK_VERSION_1_0](VK_VERSION_1_0.html), [VkFormat](VkFormat.html), [VkFormatProperties](VkFormatProperties.html), [VkPhysicalDevice](VkPhysicalDevice.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/formats.html#vkGetPhysicalDeviceFormatProperties).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
