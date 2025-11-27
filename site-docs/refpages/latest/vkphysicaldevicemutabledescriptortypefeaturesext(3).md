# VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT - Structure describing whether the mutable descriptor type is supported

The `VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT` structure is
defined as:

// Provided by VK_EXT_mutable_descriptor_type
typedef struct VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT {
    VkStructureType    sType;
    void*              pNext;
    VkBool32           mutableDescriptorType;
} VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT;

// Provided by VK_VALVE_mutable_descriptor_type
// Equivalent to VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT
typedef VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT VkPhysicalDeviceMutableDescriptorTypeFeaturesVALVE;

This structure describes the following feature:

* 
`sType` is a [VkStructureType](VkStructureType.html) value identifying this structure.

* 
`pNext` is `NULL` or a pointer to a structure extending this
structure.

* 
 `mutableDescriptorType` indicates
that the implementation **must** support using the [VkDescriptorType](VkDescriptorType.html)
of `VK_DESCRIPTOR_TYPE_MUTABLE_EXT` with at least the following
descriptor types, where any combination of the types **must** be supported:

`VK_DESCRIPTOR_TYPE_SAMPLED_IMAGE`

* 
`VK_DESCRIPTOR_TYPE_STORAGE_IMAGE`

* 
`VK_DESCRIPTOR_TYPE_UNIFORM_TEXEL_BUFFER`

* 
`VK_DESCRIPTOR_TYPE_STORAGE_TEXEL_BUFFER`

* 
`VK_DESCRIPTOR_TYPE_UNIFORM_BUFFER`

* 
`VK_DESCRIPTOR_TYPE_STORAGE_BUFFER`

* 
Additionally, `mutableDescriptorType` indicates that:

Non-uniform descriptor indexing **must** be supported if all descriptor
types in a [VkMutableDescriptorTypeListEXT](VkMutableDescriptorTypeListEXT.html) for
`VK_DESCRIPTOR_TYPE_MUTABLE_EXT` have the corresponding non-uniform
indexing features enabled in
[VkPhysicalDeviceDescriptorIndexingFeatures](VkPhysicalDeviceDescriptorIndexingFeatures.html).

* 
`VK_DESCRIPTOR_BINDING_UPDATE_AFTER_BIND_BIT` with
`descriptorType` of `VK_DESCRIPTOR_TYPE_MUTABLE_EXT` relaxes
the list of required descriptor types to the descriptor types which
have the corresponding update-after-bind feature enabled in
[VkPhysicalDeviceDescriptorIndexingFeatures](VkPhysicalDeviceDescriptorIndexingFeatures.html).

* 
Dynamically uniform descriptor indexing **must** be supported if all
descriptor types in a [VkMutableDescriptorTypeListEXT](VkMutableDescriptorTypeListEXT.html) for
`VK_DESCRIPTOR_TYPE_MUTABLE_EXT` have the corresponding dynamic
indexing features enabled.

* 
`VK_DESCRIPTOR_SET_LAYOUT_CREATE_HOST_ONLY_POOL_BIT_EXT` **must** be
supported.

* 
`VK_DESCRIPTOR_POOL_CREATE_HOST_ONLY_BIT_EXT` **must** be supported.

If the `VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT` structure is included in the `pNext` chain of the
[VkPhysicalDeviceFeatures2](VkPhysicalDeviceFeatures2.html) structure passed to
[vkGetPhysicalDeviceFeatures2](vkGetPhysicalDeviceFeatures2.html), it is filled in to indicate whether each
corresponding feature is supported.
If the application wishes to use a [VkDevice](VkDevice.html) with any features
described by `VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT`, it **must** add an instance of the structure,
with the desired feature members set to `VK_TRUE`, to the `pNext`
chain of [VkDeviceCreateInfo](VkDeviceCreateInfo.html) when creating the [VkDevice](VkDevice.html).

Valid Usage (Implicit)

* 
[](#VUID-VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT-sType-sType) VUID-VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT-sType-sType

 `sType` **must** be `VK_STRUCTURE_TYPE_PHYSICAL_DEVICE_MUTABLE_DESCRIPTOR_TYPE_FEATURES_EXT`

[VK_EXT_mutable_descriptor_type](VK_EXT_mutable_descriptor_type.html), [VK_VALVE_mutable_descriptor_type](VK_VALVE_mutable_descriptor_type.html), `VkBool32`, [VkStructureType](VkStructureType.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/features.html#VkPhysicalDeviceMutableDescriptorTypeFeaturesEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
