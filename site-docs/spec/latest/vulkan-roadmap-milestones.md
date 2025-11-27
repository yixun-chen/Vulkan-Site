# Vulkan Roadmap Milestones

## Metadata

- **Component**: spec
- **Version**: latest
- **URL**: /spec/latest/appendices/roadmap.html

## Table of Contents

- [Roadmap 2022](#roadmap-2022)
- [Required API Versions](#_required_api_versions)
- [Required_API_Versions](#_required_api_versions)
- [Required Features](#_required_features)
- [Required Limits](#_required_limits)
- [Required Extensions](#_required_extensions)
- [Roadmap 2024](#roadmap-2024)
- [Required Profiles](#_required_profiles)
- [Required Features](#_required_features_2)
- [Required Limits](#_required_limits_2)
- [Required Extensions](#_required_extensions_2)

## Content

Roadmap milestones are intended to be supported by mid-to-high-end
smartphones, tablets, laptops, consoles, and desktop devices.

Each milestone indicates support for a set of extensions, features, limits,
and formats across these devices, and should be supported by all such new
hardware shipping by the end of the target year or shortly thereafter.

The Roadmap 2022 milestone is intended to be supported by newer
mid-to-high-end devices shipping in 2022 or shortly thereafter across
mainstream smartphone, tablet, laptops, console and desktop devices.

This profile requires Vulkan 1.3.

The following core optional features are required to be supported:

* 
Vulkan 1.0 Optional Features

[`fullDrawIndexUint32`](../chapters/features.html#features-fullDrawIndexUint32)

* 
[`imageCubeArray`](../chapters/features.html#features-imageCubeArray)

* 
[`independentBlend`](../chapters/features.html#features-independentBlend)

* 
[`sampleRateShading`](../chapters/features.html#features-sampleRateShading)

* 
[`drawIndirectFirstInstance`](../chapters/features.html#features-drawIndirectFirstInstance)

* 
[`depthClamp`](../chapters/features.html#features-depthClamp)

* 
[`depthBiasClamp`](../chapters/features.html#features-depthBiasClamp)

* 
[`samplerAnisotropy`](../chapters/features.html#features-samplerAnisotropy)

* 
[`occlusionQueryPrecise`](../chapters/features.html#features-occlusionQueryPrecise)

* 
[`fragmentStoresAndAtomics`](../chapters/features.html#features-fragmentStoresAndAtomics)

* 
[     `shaderStorageImageExtendedFormats`](../chapters/features.html#features-shaderStorageImageExtendedFormats)

* 
[     `shaderUniformBufferArrayDynamicIndexing`](../chapters/features.html#features-shaderUniformBufferArrayDynamicIndexing)

* 
[     `shaderSampledImageArrayDynamicIndexing`](../chapters/features.html#features-shaderSampledImageArrayDynamicIndexing)

* 
[     `shaderStorageBufferArrayDynamicIndexing`](../chapters/features.html#features-shaderStorageBufferArrayDynamicIndexing)

* 
[     `shaderStorageImageArrayDynamicIndexing`](../chapters/features.html#features-shaderStorageImageArrayDynamicIndexing)

Vulkan 1.1 Optional Features

* 
[`samplerYcbcrConversion`](../chapters/features.html#features-samplerYcbcrConversion)

Vulkan 1.2 Optional Features

* 
[`samplerMirrorClampToEdge`](../chapters/features.html#features-samplerMirrorClampToEdge)

* 
[`descriptorIndexing`](../chapters/features.html#features-descriptorIndexing)

* 
[     `shaderUniformTexelBufferArrayDynamicIndexing`](../chapters/features.html#features-shaderUniformTexelBufferArrayDynamicIndexing)

* 
[     `shaderStorageTexelBufferArrayDynamicIndexing`](../chapters/features.html#features-shaderStorageTexelBufferArrayDynamicIndexing)

* 
[     `shaderUniformBufferArrayNonUniformIndexing`](../chapters/features.html#features-shaderUniformBufferArrayNonUniformIndexing)

* 
[     `shaderSampledImageArrayNonUniformIndexing`](../chapters/features.html#features-shaderSampledImageArrayNonUniformIndexing)

* 
[     `shaderStorageBufferArrayNonUniformIndexing`](../chapters/features.html#features-shaderStorageBufferArrayNonUniformIndexing)

* 
[     `shaderStorageImageArrayNonUniformIndexing`](../chapters/features.html#features-shaderStorageImageArrayNonUniformIndexing)

* 
[     `shaderUniformTexelBufferArrayNonUniformIndexing`](../chapters/features.html#features-shaderUniformTexelBufferArrayNonUniformIndexing)

* 
[     `shaderStorageTexelBufferArrayNonUniformIndexing`](../chapters/features.html#features-shaderStorageTexelBufferArrayNonUniformIndexing)

* 
[     `descriptorBindingSampledImageUpdateAfterBind`](../chapters/features.html#features-descriptorBindingSampledImageUpdateAfterBind)

* 
[     `descriptorBindingStorageImageUpdateAfterBind`](../chapters/features.html#features-descriptorBindingStorageImageUpdateAfterBind)

* 
[     `descriptorBindingStorageBufferUpdateAfterBind`](../chapters/features.html#features-descriptorBindingStorageBufferUpdateAfterBind)

* 
[     `descriptorBindingUniformTexelBufferUpdateAfterBind`](../chapters/features.html#features-descriptorBindingUniformTexelBufferUpdateAfterBind)

* 
[     `descriptorBindingStorageTexelBufferUpdateAfterBind`](../chapters/features.html#features-descriptorBindingStorageTexelBufferUpdateAfterBind)

* 
[     `descriptorBindingUpdateUnusedWhilePending`](../chapters/features.html#features-descriptorBindingUpdateUnusedWhilePending)

* 
[     `descriptorBindingPartiallyBound`](../chapters/features.html#features-descriptorBindingPartiallyBound)

* 
[     `descriptorBindingVariableDescriptorCount`](../chapters/features.html#features-descriptorBindingVariableDescriptorCount)

* 
[`runtimeDescriptorArray`](../chapters/features.html#features-runtimeDescriptorArray)

* 
[`scalarBlockLayout`](../chapters/features.html#features-scalarBlockLayout)

The following core increased limits are **required**

| Limit Name | Unsupported Limit | Core Limit | Profile Limit | Limit Type1 |
| --- | --- | --- | --- | --- |
| `maxImageDimension1D` | - | 4096 | 8192 | min |
| `maxImageDimension2D` | - | 4096 | 8192 | min |
| `maxImageDimensionCube` | - | 4096 | 8192 | min |
| `maxImageArrayLayers` | - | 256 | 2048 | min |
| `maxUniformBufferRange` | - | 16384 | 65536 | min |
| `bufferImageGranularity` | - | 131072 | 4096 | max |
| `maxPerStageDescriptorSamplers` | - | 16 | 64 | min |
| `maxPerStageDescriptorUniformBuffers` | - | 12 | 15 | min |
| `maxPerStageDescriptorStorageBuffers` | - | 4 | 30 | min |
| `maxPerStageDescriptorSampledImages` | - | 16 | 200 | min |
| `maxPerStageDescriptorStorageImages` | - | 4 | 16 | min |
| `maxPerStageResources` | - | 128 | 200 | min |
| `maxDescriptorSetSamplers` | - | 96 | 576 | min, *n* × PerStage |
| `maxDescriptorSetUniformBuffers` | - | 72 | 90 | min, *n* × PerStage |
| `maxDescriptorSetStorageBuffers` | - | 24 | 96 | min, *n* × PerStage |
| `maxDescriptorSetSampledImages` | - | 96 | 1800 | min, *n* × PerStage |
| `maxDescriptorSetStorageImages` | - | 24 | 144 | min, *n* × PerStage |
| `maxFragmentCombinedOutputResources` | - | 4 | 16 | min |
| `maxComputeWorkGroupInvocations` | - | 128 | 256 | min |
| `maxComputeWorkGroupSize` | - | (128,128,64) | (256,256,64) | min |
| `subTexelPrecisionBits` | - | 4 | 8 | min |
| `mipmapPrecisionBits` | - | 4 | 6 | min |
| `maxSamplerLodBias` | - | 2 | 14 | min |
| `pointSizeGranularity` | 0.0 | 1.0 | 0.125 | max, fixed point increment |
| `lineWidthGranularity` | 0.0 | 1.0 | 0.5 | max, fixed point increment |
| `standardSampleLocations` | - | - | `VK_TRUE` | implementation-dependent |
| `maxColorAttachments` | - | 4 | 7 | min |

| Limit Name | Unsupported Limit | Core Limit | Profile Limit | Limit Type1 |
| --- | --- | --- | --- | --- |
| `subgroupSize` | - | 1/4 | 4 | implementation-dependent |
| `subgroupSupportedStages` | - | `VK_SHADER_STAGE_COMPUTE_BIT` | `VK_SHADER_STAGE_COMPUTE_BIT`

                                                   `VK_SHADER_STAGE_FRAGMENT_BIT` | implementation-dependent |
| `subgroupSupportedOperations` | - | `VK_SUBGROUP_FEATURE_BASIC_BIT` | `VK_SUBGROUP_FEATURE_BASIC_BIT`

                                                   `VK_SUBGROUP_FEATURE_VOTE_BIT`

                                                   `VK_SUBGROUP_FEATURE_ARITHMETIC_BIT`

                                                   `VK_SUBGROUP_FEATURE_BALLOT_BIT`

                                                   `VK_SUBGROUP_FEATURE_SHUFFLE_BIT`

                                                   `VK_SUBGROUP_FEATURE_SHUFFLE_RELATIVE_BIT`

                                                   `VK_SUBGROUP_FEATURE_QUAD_BIT` | implementation-dependent |

| Limit Name | Unsupported Limit | Core Limit | Profile Limit | Limit Type1 |
| --- | --- | --- | --- | --- |
| `shaderSignedZeroInfNanPreserveFloat16` | - | - | `VK_TRUE` | implementation-dependent |
| `shaderSignedZeroInfNanPreserveFloat32` | - | - | `VK_TRUE` | implementation-dependent |
| `maxPerStageDescriptorUpdateAfterBindInputAttachments` | 0 | 4 | 7 | min |

| Limit Name | Unsupported Limit | Core Limit | Profile Limit | Limit Type1 |
| --- | --- | --- | --- | --- |
| `maxSubgroupSize` | - | - | 4 | min |

The following extensions are **required**

[VK_KHR_global_priority](extensions.html#VK_KHR_global_priority)

The Roadmap 2024 milestone is intended to be supported by newer
mid-to-high-end devices shipping in 2024 or shortly thereafter across
mainstream smartphone, tablet, laptops, console and desktop devices.

Two of the core aims of this roadmap profile are to enable developers to
rely on a number of important rasterization and shader features have been
available for a long time, but until now have not enjoyed wide support.

Shader features required include smaller types
([8/16-bit integers](../chapters/features.html#features-shaderInt8) and
[16-bit floats](../chapters/features.html#features-shaderFloat16)), reconvergence guarantees for
subgroup ops ([VK_KHR_shader_maximal_reconvergence](extensions.html#VK_KHR_shader_maximal_reconvergence) and
[VK_KHR_shader_quad_control](extensions.html#VK_KHR_shader_quad_control)), and more consistent floating-point
handling ([VK_KHR_shader_float_controls2](extensions.html#VK_KHR_shader_float_controls2) and
[round-to-nearest-even for 32-/16-bit floats](../chapters/devsandqueues.html#limits-shaderRoundingModeRTEFloat32)).
Rasterization features include requiring support for multi-draw indirect,
shader draw parameters, 8-bit indices, better line rasterization
definitions, and local reads when using dynamic rendering.
A few other features have been added opportunistically, in lieu of shipping
a Vulkan 1.4 in the same time frame, such as [push descriptors](extensions.html#VK_KHR_push_descriptor) and the various minor improvements included in
[VK_KHR_maintenance5](extensions.html#VK_KHR_maintenance5).

This profile requires the Roadmap 2022 profile.

The following core optional features are required to be supported:

* 
Vulkan 1.0 Optional Features

[`multiDrawIndirect`](../chapters/features.html#features-multiDrawIndirect)

* 
[`shaderImageGatherExtended`](../chapters/features.html#features-shaderImageGatherExtended)

* 
[`shaderInt16`](../chapters/features.html#features-shaderInt16)

Vulkan 1.1 Optional Features

* 
[`shaderDrawParameters`](../chapters/features.html#features-shaderDrawParameters)

* 
[`storageBuffer16BitAccess`](../chapters/features.html#features-storageBuffer16BitAccess)

Vulkan 1.2 Optional Features

* 
[`shaderInt8`](../chapters/features.html#features-shaderInt8)

* 
[`shaderFloat16`](../chapters/features.html#features-shaderFloat16)

* 
[`storageBuffer8BitAccess`](../chapters/features.html#features-storageBuffer8BitAccess)

The following core increased limits are **required**

| Limit Name | Unsupported Limit | Core Limit | Profile Limit | Limit Type1 |
| --- | --- | --- | --- | --- |
| `maxBoundDescriptorSets` | - | 4 | 7 | min |
| `maxColorAttachments` | - | 4 | 8 | min |
| `timestampComputeAndGraphics` | - | FALSE | TRUE | Boolean |

| Limit Name | Unsupported Limit | Core Limit | Profile Limit | Limit Type1 |
| --- | --- | --- | --- | --- |
| `shaderRoundingModeRTEFloat16` | - | FALSE | TRUE | Boolean |
| `shaderRoundingModeRTEFloat32` | - | FALSE | TRUE | Boolean |

The following extensions are **required**

* 
[VK_KHR_dynamic_rendering_local_read](extensions.html#VK_KHR_dynamic_rendering_local_read)

* 
[VK_KHR_load_store_op_none](extensions.html#VK_KHR_load_store_op_none)

* 
[VK_KHR_shader_quad_control](extensions.html#VK_KHR_shader_quad_control)

* 
[VK_KHR_shader_maximal_reconvergence](extensions.html#VK_KHR_shader_maximal_reconvergence)

* 
[VK_KHR_shader_subgroup_uniform_control_flow](extensions.html#VK_KHR_shader_subgroup_uniform_control_flow)

* 
[VK_KHR_shader_subgroup_rotate](extensions.html#VK_KHR_shader_subgroup_rotate)

* 
[VK_KHR_shader_float_controls2](extensions.html#VK_KHR_shader_float_controls2)

* 
[VK_KHR_shader_expect_assume](extensions.html#VK_KHR_shader_expect_assume)

* 
[VK_KHR_line_rasterization](extensions.html#VK_KHR_line_rasterization)

* 
[VK_KHR_vertex_attribute_divisor](extensions.html#VK_KHR_vertex_attribute_divisor)

* 
[VK_KHR_index_type_uint8](extensions.html#VK_KHR_index_type_uint8)

* 
[VK_KHR_map_memory2](extensions.html#VK_KHR_map_memory2)

* 
[VK_KHR_maintenance5](extensions.html#VK_KHR_maintenance5)

* 
[VK_KHR_push_descriptor](extensions.html#VK_KHR_push_descriptor)
