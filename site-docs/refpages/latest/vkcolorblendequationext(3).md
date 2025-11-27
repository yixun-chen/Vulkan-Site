# VkColorBlendEquationEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkColorBlendEquationEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkColorBlendEquationEXT - Structure specifying the color blend factors and operations for an attachment

The `VkColorBlendEquationEXT` structure is defined as:

// Provided by VK_EXT_extended_dynamic_state3, VK_EXT_shader_object
typedef struct VkColorBlendEquationEXT {
    VkBlendFactor    srcColorBlendFactor;
    VkBlendFactor    dstColorBlendFactor;
    VkBlendOp        colorBlendOp;
    VkBlendFactor    srcAlphaBlendFactor;
    VkBlendFactor    dstAlphaBlendFactor;
    VkBlendOp        alphaBlendOp;
} VkColorBlendEquationEXT;

* 
`srcColorBlendFactor` selects which blend factor is used to
determine the source factors (Sr,Sg,Sb).

* 
`dstColorBlendFactor` selects which blend factor is used to
determine the destination factors (Dr,Dg,Db).

* 
`colorBlendOp` selects which blend operation is used to calculate
the RGB values to write to the color attachment.

* 
`srcAlphaBlendFactor` selects which blend factor is used to
determine the source factor Sa.

* 
`dstAlphaBlendFactor` selects which blend factor is used to
determine the destination factor Da.

* 
`alphaBlendOp` selects which blend operation is use to calculate the
alpha values to write to the color attachment.

Valid Usage

* 
[](#VUID-VkColorBlendEquationEXT-dualSrcBlend-07357) VUID-VkColorBlendEquationEXT-dualSrcBlend-07357

If the [`dualSrcBlend`](../../../../spec/latest/chapters/features.html#features-dualSrcBlend) feature is not
enabled, `srcColorBlendFactor` **must** not be
`VK_BLEND_FACTOR_SRC1_COLOR`,
`VK_BLEND_FACTOR_ONE_MINUS_SRC1_COLOR`,
`VK_BLEND_FACTOR_SRC1_ALPHA`, or
`VK_BLEND_FACTOR_ONE_MINUS_SRC1_ALPHA`

* 
[](#VUID-VkColorBlendEquationEXT-dualSrcBlend-07358) VUID-VkColorBlendEquationEXT-dualSrcBlend-07358

If the [`dualSrcBlend`](../../../../spec/latest/chapters/features.html#features-dualSrcBlend) feature is not
enabled, `dstColorBlendFactor` **must** not be
`VK_BLEND_FACTOR_SRC1_COLOR`,
`VK_BLEND_FACTOR_ONE_MINUS_SRC1_COLOR`,
`VK_BLEND_FACTOR_SRC1_ALPHA`, or
`VK_BLEND_FACTOR_ONE_MINUS_SRC1_ALPHA`

* 
[](#VUID-VkColorBlendEquationEXT-dualSrcBlend-07359) VUID-VkColorBlendEquationEXT-dualSrcBlend-07359

If the [`dualSrcBlend`](../../../../spec/latest/chapters/features.html#features-dualSrcBlend) feature is not
enabled, `srcAlphaBlendFactor` **must** not be
`VK_BLEND_FACTOR_SRC1_COLOR`,
`VK_BLEND_FACTOR_ONE_MINUS_SRC1_COLOR`,
`VK_BLEND_FACTOR_SRC1_ALPHA`, or
`VK_BLEND_FACTOR_ONE_MINUS_SRC1_ALPHA`

* 
[](#VUID-VkColorBlendEquationEXT-dualSrcBlend-07360) VUID-VkColorBlendEquationEXT-dualSrcBlend-07360

If the [`dualSrcBlend`](../../../../spec/latest/chapters/features.html#features-dualSrcBlend) feature is not
enabled, `dstAlphaBlendFactor` **must** not be
`VK_BLEND_FACTOR_SRC1_COLOR`,
`VK_BLEND_FACTOR_ONE_MINUS_SRC1_COLOR`,
`VK_BLEND_FACTOR_SRC1_ALPHA`, or
`VK_BLEND_FACTOR_ONE_MINUS_SRC1_ALPHA`

* 
[](#VUID-VkColorBlendEquationEXT-colorBlendOp-07361) VUID-VkColorBlendEquationEXT-colorBlendOp-07361

`colorBlendOp` and `alphaBlendOp` **must** not be
`VK_BLEND_OP_ZERO_EXT`, `VK_BLEND_OP_SRC_EXT`,
`VK_BLEND_OP_DST_EXT`, `VK_BLEND_OP_SRC_OVER_EXT`,
`VK_BLEND_OP_DST_OVER_EXT`, `VK_BLEND_OP_SRC_IN_EXT`,
`VK_BLEND_OP_DST_IN_EXT`, `VK_BLEND_OP_SRC_OUT_EXT`,
`VK_BLEND_OP_DST_OUT_EXT`, `VK_BLEND_OP_SRC_ATOP_EXT`,
`VK_BLEND_OP_DST_ATOP_EXT`, `VK_BLEND_OP_XOR_EXT`,
`VK_BLEND_OP_MULTIPLY_EXT`, `VK_BLEND_OP_SCREEN_EXT`,
`VK_BLEND_OP_OVERLAY_EXT`, `VK_BLEND_OP_DARKEN_EXT`,
`VK_BLEND_OP_LIGHTEN_EXT`, `VK_BLEND_OP_COLORDODGE_EXT`,
`VK_BLEND_OP_COLORBURN_EXT`, `VK_BLEND_OP_HARDLIGHT_EXT`,
`VK_BLEND_OP_SOFTLIGHT_EXT`, `VK_BLEND_OP_DIFFERENCE_EXT`,
`VK_BLEND_OP_EXCLUSION_EXT`, `VK_BLEND_OP_INVERT_EXT`,
`VK_BLEND_OP_INVERT_RGB_EXT`, `VK_BLEND_OP_LINEARDODGE_EXT`,
`VK_BLEND_OP_LINEARBURN_EXT`, `VK_BLEND_OP_VIVIDLIGHT_EXT`,
`VK_BLEND_OP_LINEARLIGHT_EXT`, `VK_BLEND_OP_PINLIGHT_EXT`,
`VK_BLEND_OP_HARDMIX_EXT`, `VK_BLEND_OP_HSL_HUE_EXT`,
`VK_BLEND_OP_HSL_SATURATION_EXT`, `VK_BLEND_OP_HSL_COLOR_EXT`,
`VK_BLEND_OP_HSL_LUMINOSITY_EXT`, `VK_BLEND_OP_PLUS_EXT`,
`VK_BLEND_OP_PLUS_CLAMPED_EXT`,
`VK_BLEND_OP_PLUS_CLAMPED_ALPHA_EXT`,
`VK_BLEND_OP_PLUS_DARKER_EXT`, `VK_BLEND_OP_MINUS_EXT`,
`VK_BLEND_OP_MINUS_CLAMPED_EXT`, `VK_BLEND_OP_CONTRAST_EXT`,
`VK_BLEND_OP_INVERT_OVG_EXT`, `VK_BLEND_OP_RED_EXT`,
`VK_BLEND_OP_GREEN_EXT`, or `VK_BLEND_OP_BLUE_EXT`

* 
[](#VUID-VkColorBlendEquationEXT-constantAlphaColorBlendFactors-07362) VUID-VkColorBlendEquationEXT-constantAlphaColorBlendFactors-07362

If the `[VK_KHR_portability_subset](VK_KHR_portability_subset.html)` extension is enabled, and
[VkPhysicalDevicePortabilitySubsetFeaturesKHR](VkPhysicalDevicePortabilitySubsetFeaturesKHR.html)::`constantAlphaColorBlendFactors`
is `VK_FALSE`, `srcColorBlendFactor` **must** not be
`VK_BLEND_FACTOR_CONSTANT_ALPHA` or
`VK_BLEND_FACTOR_ONE_MINUS_CONSTANT_ALPHA`

* 
[](#VUID-VkColorBlendEquationEXT-constantAlphaColorBlendFactors-07363) VUID-VkColorBlendEquationEXT-constantAlphaColorBlendFactors-07363

If the `[VK_KHR_portability_subset](VK_KHR_portability_subset.html)` extension is enabled, and
[VkPhysicalDevicePortabilitySubsetFeaturesKHR](VkPhysicalDevicePortabilitySubsetFeaturesKHR.html)::`constantAlphaColorBlendFactors`
is `VK_FALSE`, `dstColorBlendFactor` **must** not be
`VK_BLEND_FACTOR_CONSTANT_ALPHA` or
`VK_BLEND_FACTOR_ONE_MINUS_CONSTANT_ALPHA`

Valid Usage (Implicit)

* 
[](#VUID-VkColorBlendEquationEXT-srcColorBlendFactor-parameter) VUID-VkColorBlendEquationEXT-srcColorBlendFactor-parameter

 `srcColorBlendFactor` **must** be a valid [VkBlendFactor](VkBlendFactor.html) value

* 
[](#VUID-VkColorBlendEquationEXT-dstColorBlendFactor-parameter) VUID-VkColorBlendEquationEXT-dstColorBlendFactor-parameter

 `dstColorBlendFactor` **must** be a valid [VkBlendFactor](VkBlendFactor.html) value

* 
[](#VUID-VkColorBlendEquationEXT-colorBlendOp-parameter) VUID-VkColorBlendEquationEXT-colorBlendOp-parameter

 `colorBlendOp` **must** be a valid [VkBlendOp](VkBlendOp.html) value

* 
[](#VUID-VkColorBlendEquationEXT-srcAlphaBlendFactor-parameter) VUID-VkColorBlendEquationEXT-srcAlphaBlendFactor-parameter

 `srcAlphaBlendFactor` **must** be a valid [VkBlendFactor](VkBlendFactor.html) value

* 
[](#VUID-VkColorBlendEquationEXT-dstAlphaBlendFactor-parameter) VUID-VkColorBlendEquationEXT-dstAlphaBlendFactor-parameter

 `dstAlphaBlendFactor` **must** be a valid [VkBlendFactor](VkBlendFactor.html) value

* 
[](#VUID-VkColorBlendEquationEXT-alphaBlendOp-parameter) VUID-VkColorBlendEquationEXT-alphaBlendOp-parameter

 `alphaBlendOp` **must** be a valid [VkBlendOp](VkBlendOp.html) value

[VK_EXT_extended_dynamic_state3](VK_EXT_extended_dynamic_state3.html), [VK_EXT_shader_object](VK_EXT_shader_object.html), [VkBlendFactor](VkBlendFactor.html), [VkBlendOp](VkBlendOp.html), [vkCmdSetColorBlendEquationEXT](vkCmdSetColorBlendEquationEXT.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/framebuffer.html#VkColorBlendEquationEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
