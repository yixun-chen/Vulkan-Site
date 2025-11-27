# VkRayTracingShaderGroupCreateInfoKHR(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkRayTracingShaderGroupCreateInfoKHR.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkRayTracingShaderGroupCreateInfoKHR - Structure specifying shaders in a shader group

The `VkRayTracingShaderGroupCreateInfoKHR` structure is defined as:

// Provided by VK_KHR_ray_tracing_pipeline
typedef struct VkRayTracingShaderGroupCreateInfoKHR {
    VkStructureType                   sType;
    const void*                       pNext;
    VkRayTracingShaderGroupTypeKHR    type;
    uint32_t                          generalShader;
    uint32_t                          closestHitShader;
    uint32_t                          anyHitShader;
    uint32_t                          intersectionShader;
    const void*                       pShaderGroupCaptureReplayHandle;
} VkRayTracingShaderGroupCreateInfoKHR;

* 
`sType` is a [VkStructureType](VkStructureType.html) value identifying this structure.

* 
`pNext` is `NULL` or a pointer to a structure extending this
structure.

* 
`type` is the type of hit group specified in this structure.

* 
`generalShader` is the index of the ray generation, miss, or
callable shader from
[VkRayTracingPipelineCreateInfoKHR](VkRayTracingPipelineCreateInfoKHR.html)::`pStages` in the group if
the shader group has `type` of
`VK_RAY_TRACING_SHADER_GROUP_TYPE_GENERAL_KHR`, and
`VK_SHADER_UNUSED_KHR` otherwise.

* 
`closestHitShader` is the optional index of the closest hit shader
from [VkRayTracingPipelineCreateInfoKHR](VkRayTracingPipelineCreateInfoKHR.html)::`pStages` in the group
if the shader group has `type` of
`VK_RAY_TRACING_SHADER_GROUP_TYPE_TRIANGLES_HIT_GROUP_KHR` or
`VK_RAY_TRACING_SHADER_GROUP_TYPE_PROCEDURAL_HIT_GROUP_KHR`, and
`VK_SHADER_UNUSED_KHR` otherwise.

* 
`anyHitShader` is the optional index of the any-hit shader from
[VkRayTracingPipelineCreateInfoKHR](VkRayTracingPipelineCreateInfoKHR.html)::`pStages` in the group if
the shader group has `type` of
`VK_RAY_TRACING_SHADER_GROUP_TYPE_TRIANGLES_HIT_GROUP_KHR` or
`VK_RAY_TRACING_SHADER_GROUP_TYPE_PROCEDURAL_HIT_GROUP_KHR`, and
`VK_SHADER_UNUSED_KHR` otherwise.

* 
`intersectionShader` is the index of the intersection shader from
[VkRayTracingPipelineCreateInfoKHR](VkRayTracingPipelineCreateInfoKHR.html)::`pStages` in the group if
the shader group has `type` of
`VK_RAY_TRACING_SHADER_GROUP_TYPE_PROCEDURAL_HIT_GROUP_KHR`, and
`VK_SHADER_UNUSED_KHR` otherwise.

* 
`pShaderGroupCaptureReplayHandle` is `NULL` or a pointer to replay
information for this shader group queried from
[vkGetRayTracingCaptureReplayShaderGroupHandlesKHR](vkGetRayTracingCaptureReplayShaderGroupHandlesKHR.html), as described in
[Ray Tracing Capture Replay](../../../../spec/latest/chapters/raytracing.html#ray-tracing-capture-replay).
Ignored if
[VkPhysicalDeviceRayTracingPipelineFeaturesKHR](VkPhysicalDeviceRayTracingPipelineFeaturesKHR.html)::`rayTracingPipelineShaderGroupHandleCaptureReplay`
is `VK_FALSE`.

If the pipeline is created with `VK_PIPELINE_CREATE_LIBRARY_BIT_KHR` and
the [pipelineLibraryGroupHandles](../../../../spec/latest/chapters/features.html#features-pipelineLibraryGroupHandles)
feature is enabled, `pShaderGroupCaptureReplayHandle` is inherited by
all pipelines which link against this pipeline and remains bitwise identical
for any pipeline which references this pipeline library.

Valid Usage

* 
[](#VUID-VkRayTracingShaderGroupCreateInfoKHR-type-03474) VUID-VkRayTracingShaderGroupCreateInfoKHR-type-03474

If `type` is `VK_RAY_TRACING_SHADER_GROUP_TYPE_GENERAL_KHR` then
`generalShader` **must** be a valid index into
[VkRayTracingPipelineCreateInfoKHR](VkRayTracingPipelineCreateInfoKHR.html)::`pStages` referring to a
shader of `VK_SHADER_STAGE_RAYGEN_BIT_KHR`,
`VK_SHADER_STAGE_MISS_BIT_KHR`, or
`VK_SHADER_STAGE_CALLABLE_BIT_KHR`

* 
[](#VUID-VkRayTracingShaderGroupCreateInfoKHR-type-03475) VUID-VkRayTracingShaderGroupCreateInfoKHR-type-03475

If `type` is `VK_RAY_TRACING_SHADER_GROUP_TYPE_GENERAL_KHR` then
`closestHitShader`, `anyHitShader`, and `intersectionShader`
**must** be `VK_SHADER_UNUSED_KHR`

* 
[](#VUID-VkRayTracingShaderGroupCreateInfoKHR-type-03476) VUID-VkRayTracingShaderGroupCreateInfoKHR-type-03476

If `type` is
`VK_RAY_TRACING_SHADER_GROUP_TYPE_PROCEDURAL_HIT_GROUP_KHR` then
`intersectionShader` **must** be a valid index into
[VkRayTracingPipelineCreateInfoKHR](VkRayTracingPipelineCreateInfoKHR.html)::`pStages` referring to a
shader of `VK_SHADER_STAGE_INTERSECTION_BIT_KHR`

* 
[](#VUID-VkRayTracingShaderGroupCreateInfoKHR-type-03477) VUID-VkRayTracingShaderGroupCreateInfoKHR-type-03477

If `type` is
`VK_RAY_TRACING_SHADER_GROUP_TYPE_TRIANGLES_HIT_GROUP_KHR` then
`intersectionShader` **must** be `VK_SHADER_UNUSED_KHR`

* 
[](#VUID-VkRayTracingShaderGroupCreateInfoKHR-closestHitShader-03478) VUID-VkRayTracingShaderGroupCreateInfoKHR-closestHitShader-03478

`closestHitShader` **must** be either `VK_SHADER_UNUSED_KHR` or a
valid index into [VkRayTracingPipelineCreateInfoKHR](VkRayTracingPipelineCreateInfoKHR.html)::`pStages`
referring to a shader of `VK_SHADER_STAGE_CLOSEST_HIT_BIT_KHR`

* 
[](#VUID-VkRayTracingShaderGroupCreateInfoKHR-anyHitShader-03479) VUID-VkRayTracingShaderGroupCreateInfoKHR-anyHitShader-03479

`anyHitShader` **must** be either `VK_SHADER_UNUSED_KHR` or a valid
index into [VkRayTracingPipelineCreateInfoKHR](VkRayTracingPipelineCreateInfoKHR.html)::`pStages`
referring to a shader of `VK_SHADER_STAGE_ANY_HIT_BIT_KHR`

* 
[](#VUID-VkRayTracingShaderGroupCreateInfoKHR-rayTracingPipelineShaderGroupHandleCaptureReplayMixed-03603) VUID-VkRayTracingShaderGroupCreateInfoKHR-rayTracingPipelineShaderGroupHandleCaptureReplayMixed-03603

If
[VkPhysicalDeviceRayTracingPipelineFeaturesKHR](VkPhysicalDeviceRayTracingPipelineFeaturesKHR.html)::`rayTracingPipelineShaderGroupHandleCaptureReplayMixed`
is `VK_FALSE` then `pShaderGroupCaptureReplayHandle` **must** not
be provided if it has not been provided on a previous call to ray
tracing pipeline creation

* 
[](#VUID-VkRayTracingShaderGroupCreateInfoKHR-rayTracingPipelineShaderGroupHandleCaptureReplayMixed-03604) VUID-VkRayTracingShaderGroupCreateInfoKHR-rayTracingPipelineShaderGroupHandleCaptureReplayMixed-03604

If
[VkPhysicalDeviceRayTracingPipelineFeaturesKHR](VkPhysicalDeviceRayTracingPipelineFeaturesKHR.html)::`rayTracingPipelineShaderGroupHandleCaptureReplayMixed`
is `VK_FALSE` then the caller **must** guarantee that no ray tracing
pipeline creation commands with `pShaderGroupCaptureReplayHandle`
provided execute simultaneously with ray tracing pipeline creation
commands without `pShaderGroupCaptureReplayHandle` provided

Valid Usage (Implicit)

* 
[](#VUID-VkRayTracingShaderGroupCreateInfoKHR-sType-sType) VUID-VkRayTracingShaderGroupCreateInfoKHR-sType-sType

 `sType` **must** be `VK_STRUCTURE_TYPE_RAY_TRACING_SHADER_GROUP_CREATE_INFO_KHR`

* 
[](#VUID-VkRayTracingShaderGroupCreateInfoKHR-pNext-pNext) VUID-VkRayTracingShaderGroupCreateInfoKHR-pNext-pNext

 `pNext` **must** be `NULL`

* 
[](#VUID-VkRayTracingShaderGroupCreateInfoKHR-type-parameter) VUID-VkRayTracingShaderGroupCreateInfoKHR-type-parameter

 `type` **must** be a valid [VkRayTracingShaderGroupTypeKHR](VkRayTracingShaderGroupTypeKHR.html) value

[VK_KHR_ray_tracing_pipeline](VK_KHR_ray_tracing_pipeline.html), [VkRayTracingPipelineCreateInfoKHR](VkRayTracingPipelineCreateInfoKHR.html), [VkRayTracingShaderGroupTypeKHR](VkRayTracingShaderGroupTypeKHR.html), [VkStructureType](VkStructureType.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/pipelines.html#VkRayTracingShaderGroupCreateInfoKHR).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
