# VkPhysicalDeviceDescriptorBufferFeaturesEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkPhysicalDeviceDescriptorBufferFeaturesEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkPhysicalDeviceDescriptorBufferFeaturesEXT - Structure describing the descriptor buffer features that can be supported by an implementation

The `VkPhysicalDeviceDescriptorBufferFeaturesEXT` structure is defined
as:

// Provided by VK_EXT_descriptor_buffer
typedef struct VkPhysicalDeviceDescriptorBufferFeaturesEXT {
    VkStructureType    sType;
    void*              pNext;
    VkBool32           descriptorBuffer;
    VkBool32           descriptorBufferCaptureReplay;
    VkBool32           descriptorBufferImageLayoutIgnored;
    VkBool32           descriptorBufferPushDescriptors;
} VkPhysicalDeviceDescriptorBufferFeaturesEXT;

This structure describes the following feature:

* 
`sType` is a [VkStructureType](VkStructureType.html) value identifying this structure.

* 
`pNext` is `NULL` or a pointer to a structure extending this
structure.

* 
 `descriptorBuffer` indicates that the
implementation supports putting shader-accessible descriptors directly
in memory.

* 

`descriptorBufferCaptureReplay` indicates that the implementation
supports capture and replay when using descriptor buffers.
If this is `VK_TRUE`, all resources created with
`VK_BUFFER_CREATE_DESCRIPTOR_BUFFER_CAPTURE_REPLAY_BIT_EXT`,
`VK_IMAGE_CREATE_DESCRIPTOR_BUFFER_CAPTURE_REPLAY_BIT_EXT`,
`VK_IMAGE_VIEW_CREATE_DESCRIPTOR_BUFFER_CAPTURE_REPLAY_BIT_EXT`,
`VK_TENSOR_CREATE_DESCRIPTOR_BUFFER_CAPTURE_REPLAY_BIT_ARM`,
`VK_TENSOR_VIEW_CREATE_DESCRIPTOR_BUFFER_CAPTURE_REPLAY_BIT_ARM`,
`VK_SAMPLER_CREATE_DESCRIPTOR_BUFFER_CAPTURE_REPLAY_BIT_EXT`, or
`VK_ACCELERATION_STRUCTURE_CREATE_DESCRIPTOR_BUFFER_CAPTURE_REPLAY_BIT_EXT`
**must** be created before resources of the same types without those flags.

* 

`descriptorBufferImageLayoutIgnored` indicates that the
implementation will ignore `imageLayout` in
`VkDescriptorImageInfo` when calling [vkGetDescriptorEXT](vkGetDescriptorEXT.html).

* 

`descriptorBufferPushDescriptors` indicates that the implementation
supports using push descriptors with descriptor buffers.

If the `VkPhysicalDeviceDescriptorBufferFeaturesEXT` structure is included in the `pNext` chain of the
[VkPhysicalDeviceFeatures2](VkPhysicalDeviceFeatures2.html) structure passed to
[vkGetPhysicalDeviceFeatures2](vkGetPhysicalDeviceFeatures2.html), it is filled in to indicate whether each
corresponding feature is supported.
If the application wishes to use a [VkDevice](VkDevice.html) with any features
described by `VkPhysicalDeviceDescriptorBufferFeaturesEXT`, it **must** add an instance of the structure,
with the desired feature members set to `VK_TRUE`, to the `pNext`
chain of [VkDeviceCreateInfo](VkDeviceCreateInfo.html) when creating the [VkDevice](VkDevice.html).

Valid Usage (Implicit)

* 
[](#VUID-VkPhysicalDeviceDescriptorBufferFeaturesEXT-sType-sType) VUID-VkPhysicalDeviceDescriptorBufferFeaturesEXT-sType-sType

 `sType` **must** be `VK_STRUCTURE_TYPE_PHYSICAL_DEVICE_DESCRIPTOR_BUFFER_FEATURES_EXT`

[VK_EXT_descriptor_buffer](VK_EXT_descriptor_buffer.html), `VkBool32`, [VkStructureType](VkStructureType.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/features.html#VkPhysicalDeviceDescriptorBufferFeaturesEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
