# VkPhysicalDeviceSamplerFilterMinmaxProperties(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkPhysicalDeviceSamplerFilterMinmaxProperties.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkPhysicalDeviceSamplerFilterMinmaxProperties - Structure describing sampler filter minmax limits that can be supported by an implementation

The `VkPhysicalDeviceSamplerFilterMinmaxProperties` structure is defined
as:

// Provided by VK_VERSION_1_2
typedef struct VkPhysicalDeviceSamplerFilterMinmaxProperties {
    VkStructureType    sType;
    void*              pNext;
    VkBool32           filterMinmaxSingleComponentFormats;
    VkBool32           filterMinmaxImageComponentMapping;
} VkPhysicalDeviceSamplerFilterMinmaxProperties;

// Provided by VK_EXT_sampler_filter_minmax
// Equivalent to VkPhysicalDeviceSamplerFilterMinmaxProperties
typedef VkPhysicalDeviceSamplerFilterMinmaxProperties VkPhysicalDeviceSamplerFilterMinmaxPropertiesEXT;

* 
`sType` is a [VkStructureType](VkStructureType.html) value identifying this structure.

* 
`pNext` is `NULL` or a pointer to a structure extending this
structure.

* 

`filterMinmaxSingleComponentFormats` is a boolean value indicating
whether a minimum set of required formats support min/max filtering.

* 

`filterMinmaxImageComponentMapping` is a boolean value indicating
whether the implementation supports non-identity component mapping of
the image when doing min/max filtering.

If the `VkPhysicalDeviceSamplerFilterMinmaxProperties` structure is included in the `pNext` chain of the
[VkPhysicalDeviceProperties2](VkPhysicalDeviceProperties2.html) structure passed to
[vkGetPhysicalDeviceProperties2](vkGetPhysicalDeviceProperties2.html), it is filled in with each
corresponding implementation-dependent property.

If `filterMinmaxSingleComponentFormats` is `VK_TRUE`, the following
formats **must** support the
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_MINMAX_BIT` feature with
`VK_IMAGE_TILING_OPTIMAL`, if they support
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_BIT`:

* 
`VK_FORMAT_R8_UNORM`

* 
`VK_FORMAT_R8_SNORM`

* 
`VK_FORMAT_R16_UNORM`

* 
`VK_FORMAT_R16_SNORM`

* 
`VK_FORMAT_R16_SFLOAT`

* 
`VK_FORMAT_R32_SFLOAT`

* 
`VK_FORMAT_D16_UNORM`

* 
`VK_FORMAT_X8_D24_UNORM_PACK32`

* 
`VK_FORMAT_D32_SFLOAT`

* 
`VK_FORMAT_D16_UNORM_S8_UINT`

* 
`VK_FORMAT_D24_UNORM_S8_UINT`

* 
`VK_FORMAT_D32_SFLOAT_S8_UINT`

If the format is a depth/stencil format, this bit only specifies that the
depth aspect (not the stencil aspect) of an image of this format supports
min/max filtering, and that min/max filtering of the depth aspect is
supported when depth compare is disabled in the sampler.

If `filterMinmaxImageComponentMapping` is `VK_FALSE` the component
mapping of the image view used with min/max filtering **must** have been
created with the `r` component set to the
[identity swizzle](../../../../spec/latest/chapters/resources.html#resources-image-views-identity-mappings).
Only the `r` component of the sampled image value is defined and the
other component values are **undefined**.
If `filterMinmaxImageComponentMapping` is `VK_TRUE` this restriction
does not apply and image component mapping works as normal.

Valid Usage (Implicit)

* 
[](#VUID-VkPhysicalDeviceSamplerFilterMinmaxProperties-sType-sType) VUID-VkPhysicalDeviceSamplerFilterMinmaxProperties-sType-sType

 `sType` **must** be `VK_STRUCTURE_TYPE_PHYSICAL_DEVICE_SAMPLER_FILTER_MINMAX_PROPERTIES`

[VK_EXT_sampler_filter_minmax](VK_EXT_sampler_filter_minmax.html), [VK_VERSION_1_2](VK_VERSION_1_2.html), `VkBool32`, [VkStructureType](VkStructureType.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/limits.html#VkPhysicalDeviceSamplerFilterMinmaxProperties).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
