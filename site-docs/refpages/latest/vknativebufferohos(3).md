# VkNativeBufferOHOS(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkNativeBufferOHOS.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkNativeBufferOHOS - Native buffer on Open Harmony OS platform

The `VkNativeBufferOHOS` structure is defined as:

// Provided by VK_OHOS_native_buffer
typedef struct VkNativeBufferOHOS {
    VkStructureType           sType;
    const void*               pNext;
    struct OHBufferHandle*    handle;
} VkNativeBufferOHOS;

* 
`sType` is a [VkStructureType](VkStructureType.html) value identifying this structure.

* 
`pNext` is `NULL` or a pointer to a structure extending this
structure.

* 
`handle` is a pointer to an `OHBufferHandle` object.

`OHBufferHandle` is exposed by the Open Harmony OS NDK.

Valid Usage (Implicit)

* 
[](#VUID-VkNativeBufferOHOS-sType-sType) VUID-VkNativeBufferOHOS-sType-sType

 `sType` **must** be `VK_STRUCTURE_TYPE_NATIVE_BUFFER_OHOS`

* 
[](#VUID-VkNativeBufferOHOS-handle-parameter) VUID-VkNativeBufferOHOS-handle-parameter

 `handle` **must** be a valid pointer to an `OHBufferHandle` value

[VK_OHOS_native_buffer](VK_OHOS_native_buffer.html), [VkStructureType](VkStructureType.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/resources.html#VkNativeBufferOHOS).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
