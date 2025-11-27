# vkCreateShadersEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkCreateShadersEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkCreateShadersEXT - Create one or more new shaders

To create one or more shader objects, call:

// Provided by VK_EXT_shader_object
VkResult vkCreateShadersEXT(
    VkDevice                                    device,
    uint32_t                                    createInfoCount,
    const VkShaderCreateInfoEXT*                pCreateInfos,
    const VkAllocationCallbacks*                pAllocator,
    VkShaderEXT*                                pShaders);

* 
`device` is the logical device that creates the shader objects.

* 
`createInfoCount` is the length of the `pCreateInfos` and
`pShaders` arrays.

* 
`pCreateInfos` is a pointer to an array of
[VkShaderCreateInfoEXT](VkShaderCreateInfoEXT.html) structures.

* 
`pAllocator` controls host memory allocation as described in the
[Memory Allocation](../../../../spec/latest/chapters/memory.html#memory-allocation) chapter.

* 
`pShaders` is a pointer to an array of [VkShaderEXT](VkShaderEXT.html) handles in
which the resulting shader objects are returned.

When this function returns, whether or not it succeeds, it is guaranteed
that every element of `pShaders` will have been overwritten by either
[VK_NULL_HANDLE](VK_NULL_HANDLE.html) or a valid `VkShaderEXT` handle.

This means that whenever shader creation fails, the application **can**
determine which shader the returned error pertains to by locating the first
[VK_NULL_HANDLE](VK_NULL_HANDLE.html) element in `pShaders`.
It also means that an application **can** reliably clean up from a failed call
by iterating over the `pShaders` array and destroying every element that
is not [VK_NULL_HANDLE](VK_NULL_HANDLE.html).

Valid Usage

* 
[](#VUID-vkCreateShadersEXT-stage-09670) VUID-vkCreateShadersEXT-stage-09670

If the `stage` member of any element of `pCreateInfos` is
`VK_SHADER_STAGE_COMPUTE_BIT`, `device` **must** support at least
one queue family with the `VK_QUEUE_COMPUTE_BIT` capability

* 
[](#VUID-vkCreateShadersEXT-stage-09671) VUID-vkCreateShadersEXT-stage-09671

If the `stage` member of any element of `pCreateInfos` is
`VK_SHADER_STAGE_TASK_BIT_EXT`, `VK_SHADER_STAGE_MESH_BIT_EXT`,
`VK_SHADER_STAGE_VERTEX_BIT`,
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT`,
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT`,
`VK_SHADER_STAGE_GEOMETRY_BIT`, or
`VK_SHADER_STAGE_FRAGMENT_BIT`, `device` **must** support at least
one queue family with the `VK_QUEUE_GRAPHICS_BIT` capability

* 
[](#VUID-vkCreateShadersEXT-None-08400) VUID-vkCreateShadersEXT-None-08400

The [`shaderObject`](../../../../spec/latest/chapters/features.html#features-shaderObject) feature **must** be
enabled

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-08402) VUID-vkCreateShadersEXT-pCreateInfos-08402

If the `flags` member of any element of `pCreateInfos` includes
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`, the `flags` member of all
other elements of `pCreateInfos` whose `stage` is
`VK_SHADER_STAGE_VERTEX_BIT`,
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT`,
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT`,
`VK_SHADER_STAGE_GEOMETRY_BIT`, or
`VK_SHADER_STAGE_FRAGMENT_BIT` **must** also include
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-08403) VUID-vkCreateShadersEXT-pCreateInfos-08403

If the `flags` member of any element of `pCreateInfos` includes
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`, the `flags` member of all
other elements of `pCreateInfos` whose `stage` is
`VK_SHADER_STAGE_TASK_BIT_EXT` or `VK_SHADER_STAGE_MESH_BIT_EXT`
**must** also include `VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-08404) VUID-vkCreateShadersEXT-pCreateInfos-08404

If the `flags` member of any element of `pCreateInfos` whose
`stage` is `VK_SHADER_STAGE_TASK_BIT_EXT` or
`VK_SHADER_STAGE_MESH_BIT_EXT` includes
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`, there **must** be no member of
`pCreateInfos` whose `stage` is `VK_SHADER_STAGE_VERTEX_BIT`
and whose `flags` member includes
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-08405) VUID-vkCreateShadersEXT-pCreateInfos-08405

If there is any element of `pCreateInfos` whose `stage` is
`VK_SHADER_STAGE_MESH_BIT_EXT` and whose `flags` member includes
both `VK_SHADER_CREATE_LINK_STAGE_BIT_EXT` and
`VK_SHADER_CREATE_NO_TASK_SHADER_BIT_EXT`, there **must** be no element
of `pCreateInfos` whose `stage` is
`VK_SHADER_STAGE_TASK_BIT_EXT` and whose `flags` member includes
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-08409) VUID-vkCreateShadersEXT-pCreateInfos-08409

For each element of `pCreateInfos` whose `flags` member includes
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`, if there is any other element
of `pCreateInfos` whose `stage` is logically later than the
`stage` of the former and whose `flags` member also includes
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`, the `nextStage` of the
former **must** be equal to the `stage` of the element with the
logically earliest `stage` following the `stage` of the former
whose `flags` member also includes
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-08410) VUID-vkCreateShadersEXT-pCreateInfos-08410

The `stage` member of each element of `pCreateInfos` whose
`flags` member includes `VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`
**must** be unique

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-08411) VUID-vkCreateShadersEXT-pCreateInfos-08411

The `codeType` member of all elements of `pCreateInfos` whose
`flags` member includes `VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`
**must** be the same

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-12224) VUID-vkCreateShadersEXT-pCreateInfos-12224

If `pCreateInfos` contains elements with both
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` and
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT`, both elements'
`flags` include `VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`, both
elements' `codeType` is `VK_SHADER_CODE_TYPE_SPIRV_EXT`, at
least one **must** contain an `OpExecutionMode` instruction specifying
the orientation of triangles generated by the tessellator

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-12225) VUID-vkCreateShadersEXT-pCreateInfos-12225

If `pCreateInfos` contains elements with both
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` and
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT`, both elements'
`flags` include `VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`, both
elements' `codeType` is `VK_SHADER_CODE_TYPE_SPIRV_EXT`, at
least one **must** contain an `OpExecutionMode` instruction specifying
the spacing of segments on the edges of tessellated primitives

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-08867) VUID-vkCreateShadersEXT-pCreateInfos-08867

If `pCreateInfos` contains elements with both
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` and
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT`, both elements'
`flags` include `VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`, both
elements' `codeType` is `VK_SHADER_CODE_TYPE_SPIRV_EXT`, and
both stages contains an `OpExecutionMode` instruction specifying the
type of subdivision, they **must** be the same

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-08868) VUID-vkCreateShadersEXT-pCreateInfos-08868

If `pCreateInfos` contains elements with both
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` and
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT`, both elements'
`flags` include `VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`, both
elements' `codeType` is `VK_SHADER_CODE_TYPE_SPIRV_EXT`, and
both stages contains an `OpExecutionMode` instruction specifying the
orientation of triangles, they **must** be the same

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-08870) VUID-vkCreateShadersEXT-pCreateInfos-08870

If `pCreateInfos` contains elements with both
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` and
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT`, both elements'
`flags` include `VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`, both
elements' `codeType` is `VK_SHADER_CODE_TYPE_SPIRV_EXT`, and
both stages contains an `OpExecutionMode` instruction specifying the
spacing of segments on the edges of tessellated primitives, they **must**
be the same

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-08871) VUID-vkCreateShadersEXT-pCreateInfos-08871

If `pCreateInfos` contains elements with both
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` and
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT`, both elements'
`flags` include `VK_SHADER_CREATE_LINK_STAGE_BIT_EXT`, both
elements' `codeType` is `VK_SHADER_CODE_TYPE_SPIRV_EXT`, and
both stages contains an `OpExecutionMode` instruction specifying the
output patch size, they **must** be the same

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-09632) VUID-vkCreateShadersEXT-pCreateInfos-09632

If `pCreateInfos` contains a `VK_SHADER_STAGE_MESH_BIT_EXT` with
`codeType` of `VK_SHADER_CODE_TYPE_SPIRV_EXT` and
`VK_SHADER_CREATE_NO_TASK_SHADER_BIT_EXT` is not set, then the mesh
shader’s entry point **must** not declare a variable with a `DrawIndex`
`BuiltIn` decoration

Valid Usage (Implicit)

* 
[](#VUID-vkCreateShadersEXT-device-parameter) VUID-vkCreateShadersEXT-device-parameter

 `device` **must** be a valid [VkDevice](VkDevice.html) handle

* 
[](#VUID-vkCreateShadersEXT-pCreateInfos-parameter) VUID-vkCreateShadersEXT-pCreateInfos-parameter

 `pCreateInfos` **must** be a valid pointer to an array of `createInfoCount` valid [VkShaderCreateInfoEXT](VkShaderCreateInfoEXT.html) structures

* 
[](#VUID-vkCreateShadersEXT-pAllocator-parameter) VUID-vkCreateShadersEXT-pAllocator-parameter

 If `pAllocator` is not `NULL`, `pAllocator` **must** be a valid pointer to a valid [VkAllocationCallbacks](VkAllocationCallbacks.html) structure

* 
[](#VUID-vkCreateShadersEXT-pShaders-parameter) VUID-vkCreateShadersEXT-pShaders-parameter

 `pShaders` **must** be a valid pointer to an array of `createInfoCount` [VkShaderEXT](VkShaderEXT.html) handles

* 
[](#VUID-vkCreateShadersEXT-createInfoCount-arraylength) VUID-vkCreateShadersEXT-createInfoCount-arraylength

 `createInfoCount` **must** be greater than `0`

Return Codes

[Success](../../../../spec/latest/chapters/fundamentals.html#fundamentals-successcodes)

* 
`VK_INCOMPATIBLE_SHADER_BINARY_EXT`

* 
`VK_SUCCESS`

[Failure](../../../../spec/latest/chapters/fundamentals.html#fundamentals-errorcodes)

* 
`VK_ERROR_INITIALIZATION_FAILED`

* 
`VK_ERROR_OUT_OF_DEVICE_MEMORY`

* 
`VK_ERROR_OUT_OF_HOST_MEMORY`

* 
`VK_ERROR_UNKNOWN`

* 
`VK_ERROR_VALIDATION_FAILED`

[VK_EXT_shader_object](VK_EXT_shader_object.html), [VkAllocationCallbacks](VkAllocationCallbacks.html), [VkDevice](VkDevice.html), [VkShaderCreateInfoEXT](VkShaderCreateInfoEXT.html), [VkShaderEXT](VkShaderEXT.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/shaders.html#vkCreateShadersEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
