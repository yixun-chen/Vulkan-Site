# VkDescriptorBufferBindingPushDescriptorBufferHandleEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkDescriptorBufferBindingPushDescriptorBufferHandleEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkDescriptorBufferBindingPushDescriptorBufferHandleEXT - Structure specifying push descriptor buffer binding information

When the [`VkPhysicalDeviceDescriptorBufferPropertiesEXT`::`bufferlessPushDescriptors`](../../../../spec/latest/chapters/limits.html#limits-bufferlessPushDescriptors)
property is `VK_FALSE`, the `VkBuffer` handle of the buffer for push
descriptors is passed in a
`VkDescriptorBufferBindingPushDescriptorBufferHandleEXT` structure:

// Provided by VK_EXT_descriptor_buffer
typedef struct VkDescriptorBufferBindingPushDescriptorBufferHandleEXT {
    VkStructureType    sType;
    const void*        pNext;
    VkBuffer           buffer;
} VkDescriptorBufferBindingPushDescriptorBufferHandleEXT;

* 
`sType` is a [VkStructureType](VkStructureType.html) value identifying this structure.

* 
`pNext` is `NULL` or a pointer to a structure extending this
structure.

* 
`buffer` is the `VkBuffer` handle of the buffer for push
descriptors.

Valid Usage

* 
[](#VUID-VkDescriptorBufferBindingPushDescriptorBufferHandleEXT-bufferlessPushDescriptors-08059) VUID-VkDescriptorBufferBindingPushDescriptorBufferHandleEXT-bufferlessPushDescriptors-08059

[    `VkPhysicalDeviceDescriptorBufferPropertiesEXT`::`bufferlessPushDescriptors`](../../../../spec/latest/chapters/limits.html#limits-bufferlessPushDescriptors)
**must** be `VK_FALSE`

Valid Usage (Implicit)

* 
[](#VUID-VkDescriptorBufferBindingPushDescriptorBufferHandleEXT-sType-sType) VUID-VkDescriptorBufferBindingPushDescriptorBufferHandleEXT-sType-sType

 `sType` **must** be `VK_STRUCTURE_TYPE_DESCRIPTOR_BUFFER_BINDING_PUSH_DESCRIPTOR_BUFFER_HANDLE_EXT`

* 
[](#VUID-VkDescriptorBufferBindingPushDescriptorBufferHandleEXT-buffer-parameter) VUID-VkDescriptorBufferBindingPushDescriptorBufferHandleEXT-buffer-parameter

 `buffer` **must** be a valid [VkBuffer](VkBuffer.html) handle

[VK_EXT_descriptor_buffer](VK_EXT_descriptor_buffer.html), [VkBuffer](VkBuffer.html), [VkStructureType](VkStructureType.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/descriptorsets.html#VkDescriptorBufferBindingPushDescriptorBufferHandleEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
