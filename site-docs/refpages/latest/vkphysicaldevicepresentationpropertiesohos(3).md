# VkPhysicalDevicePresentationPropertiesOHOS(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkPhysicalDevicePresentationPropertiesOHOS.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkPhysicalDevicePresentationPropertiesOHOS - The presentation properties of a physical device

The `VkPhysicalDevicePresentationPropertiesOHOS` structure is defined
as:

// Provided by VK_OHOS_native_buffer
typedef struct VkPhysicalDevicePresentationPropertiesOHOS {
    VkStructureType    sType;
    void*              pNext;
    VkBool32           sharedImage;
} VkPhysicalDevicePresentationPropertiesOHOS;

* 
`sType` is a [VkStructureType](VkStructureType.html) value identifying this structure.

* 
`pNext` is `NULL` or a pointer to a structure extending this
structure.

* 
`sharedImage` will be set to `VK_TRUE` if the driver can share
the ownership of a image with the display system.

Valid Usage (Implicit)

* 
[](#VUID-VkPhysicalDevicePresentationPropertiesOHOS-sType-sType) VUID-VkPhysicalDevicePresentationPropertiesOHOS-sType-sType

 `sType` **must** be `VK_STRUCTURE_TYPE_PHYSICAL_DEVICE_PRESENTATION_PROPERTIES_OHOS`

[VK_OHOS_native_buffer](VK_OHOS_native_buffer.html), `VkBool32`, [VkStructureType](VkStructureType.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/resources.html#VkPhysicalDevicePresentationPropertiesOHOS).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
