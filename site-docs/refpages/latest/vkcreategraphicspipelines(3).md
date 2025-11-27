# vkCreateGraphicsPipelines(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkCreateGraphicsPipelines.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkCreateGraphicsPipelines - Create graphics pipelines

To create graphics pipelines, call:

// Provided by VK_VERSION_1_0
VkResult vkCreateGraphicsPipelines(
    VkDevice                                    device,
    VkPipelineCache                             pipelineCache,
    uint32_t                                    createInfoCount,
    const VkGraphicsPipelineCreateInfo*         pCreateInfos,
    const VkAllocationCallbacks*                pAllocator,
    VkPipeline*                                 pPipelines);

* 
`device` is the logical device that creates the graphics pipelines.

* 
`pipelineCache` is
either [VK_NULL_HANDLE](VK_NULL_HANDLE.html), indicating that pipeline caching is
disabled, or to enable caching,
the handle of a valid [VkPipelineCache](VkPipelineCache.html) object.
The implementation **must** not access this object outside of the duration
of this command.

* 
`createInfoCount` is the length of the `pCreateInfos` and
`pPipelines` arrays.

* 
`pCreateInfos` is a pointer to an array of
[VkGraphicsPipelineCreateInfo](VkGraphicsPipelineCreateInfo.html) structures.

* 
`pAllocator` controls host memory allocation as described in the
[Memory Allocation](../../../../spec/latest/chapters/memory.html#memory-allocation) chapter.

* 
`pPipelines` is a pointer to an array of [VkPipeline](VkPipeline.html) handles in
which the resulting graphics pipeline objects are returned.

The [VkGraphicsPipelineCreateInfo](VkGraphicsPipelineCreateInfo.html) structure includes an array of
[VkPipelineShaderStageCreateInfo](VkPipelineShaderStageCreateInfo.html) structures for each of the desired
active shader stages, as well as creation information for all relevant
fixed-function stages, and a pipeline layout.

Pipelines are created and returned as described for [Multiple Pipeline Creation](../../../../spec/latest/chapters/pipelines.html#pipelines-multiple).

Valid Usage

* 
[](#VUID-vkCreateGraphicsPipelines-device-09662) VUID-vkCreateGraphicsPipelines-device-09662

`device` **must** support at least one queue family with the
`VK_QUEUE_GRAPHICS_BIT` capability

* 
[](#VUID-vkCreateGraphicsPipelines-flags-00720) VUID-vkCreateGraphicsPipelines-flags-00720

If the `flags` member of any element of `pCreateInfos` contains
the `VK_PIPELINE_CREATE_DERIVATIVE_BIT` flag, and the
`basePipelineIndex` member of that same element is not `-1`,
`basePipelineIndex` **must** be less than the index into
`pCreateInfos` that corresponds to that element

* 
[](#VUID-vkCreateGraphicsPipelines-flags-00721) VUID-vkCreateGraphicsPipelines-flags-00721

If the `flags` member of any element of `pCreateInfos` contains
the `VK_PIPELINE_CREATE_DERIVATIVE_BIT` flag, the base pipeline
**must** have been created with the
`VK_PIPELINE_CREATE_ALLOW_DERIVATIVES_BIT` flag set

* 
[](#VUID-vkCreateGraphicsPipelines-pipelineCache-02876) VUID-vkCreateGraphicsPipelines-pipelineCache-02876

If `pipelineCache` was created with
`VK_PIPELINE_CACHE_CREATE_EXTERNALLY_SYNCHRONIZED_BIT`, host access
to `pipelineCache` **must** be
[externally synchronized](../../../../spec/latest/chapters/fundamentals.html#fundamentals-threadingbehavior)

* 
[](#VUID-vkCreateGraphicsPipelines-pNext-09616) VUID-vkCreateGraphicsPipelines-pNext-09616

If [VkPipelineBinaryInfoKHR](VkPipelineBinaryInfoKHR.html)::`binaryCount` is not `0` for any
element of `pCreateInfos`, `pipelineCache` **must** be
[VK_NULL_HANDLE](VK_NULL_HANDLE.html)

* 
[](#VUID-vkCreateGraphicsPipelines-pNext-09617) VUID-vkCreateGraphicsPipelines-pNext-09617

If a [VkPipelineCreateFlags2CreateInfoKHR](VkPipelineCreateFlags2CreateInfo.html) structure with the
`VK_PIPELINE_CREATE_2_CAPTURE_DATA_BIT_KHR` flag set is included in
the `pNext` chain of any element of `pCreateInfos`,
`pipelineCache` **must** be [VK_NULL_HANDLE](VK_NULL_HANDLE.html)

* 
[](#VUID-vkCreateGraphicsPipelines-binaryCount-09620) VUID-vkCreateGraphicsPipelines-binaryCount-09620

If [VkPipelineBinaryInfoKHR](VkPipelineBinaryInfoKHR.html)::`binaryCount` is not `0` for any
element of `pCreateInfos`,
`VK_PIPELINE_CREATION_FEEDBACK_APPLICATION_PIPELINE_CACHE_HIT_BIT`
**must** not be set in the `flags` of that element

* 
[](#VUID-vkCreateGraphicsPipelines-binaryCount-09621) VUID-vkCreateGraphicsPipelines-binaryCount-09621

If [VkPipelineBinaryInfoKHR](VkPipelineBinaryInfoKHR.html)::`binaryCount` is not `0` for any
element of `pCreateInfos`,
`VK_PIPELINE_CREATION_FEEDBACK_BASE_PIPELINE_ACCELERATION_BIT` **must**
not be set in the `flags` of that element

* 
[](#VUID-vkCreateGraphicsPipelines-binaryCount-09622) VUID-vkCreateGraphicsPipelines-binaryCount-09622

If [VkPipelineBinaryInfoKHR](VkPipelineBinaryInfoKHR.html)::`binaryCount` is not `0` for any
element of `pCreateInfos`,
`VK_PIPELINE_CREATE_FAIL_ON_PIPELINE_COMPILE_REQUIRED_BIT_EXT` **must**
not be set in the `flags` of that element

|  | An implicit cache may be provided by the implementation or a layer.
| --- | --- |
For this reason, it is still valid to set
`VK_PIPELINE_CREATE_FAIL_ON_PIPELINE_COMPILE_REQUIRED_BIT` on
`flags` for any element of `pCreateInfos` while passing
[VK_NULL_HANDLE](VK_NULL_HANDLE.html) for `pipelineCache`. |

Valid Usage (Implicit)

* 
[](#VUID-vkCreateGraphicsPipelines-device-parameter) VUID-vkCreateGraphicsPipelines-device-parameter

 `device` **must** be a valid [VkDevice](VkDevice.html) handle

* 
[](#VUID-vkCreateGraphicsPipelines-pipelineCache-parameter) VUID-vkCreateGraphicsPipelines-pipelineCache-parameter

 If `pipelineCache` is not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), `pipelineCache` **must** be a valid [VkPipelineCache](VkPipelineCache.html) handle

* 
[](#VUID-vkCreateGraphicsPipelines-pCreateInfos-parameter) VUID-vkCreateGraphicsPipelines-pCreateInfos-parameter

 `pCreateInfos` **must** be a valid pointer to an array of `createInfoCount` valid [VkGraphicsPipelineCreateInfo](VkGraphicsPipelineCreateInfo.html) structures

* 
[](#VUID-vkCreateGraphicsPipelines-pAllocator-parameter) VUID-vkCreateGraphicsPipelines-pAllocator-parameter

 If `pAllocator` is not `NULL`, `pAllocator` **must** be a valid pointer to a valid [VkAllocationCallbacks](VkAllocationCallbacks.html) structure

* 
[](#VUID-vkCreateGraphicsPipelines-pPipelines-parameter) VUID-vkCreateGraphicsPipelines-pPipelines-parameter

 `pPipelines` **must** be a valid pointer to an array of `createInfoCount` [VkPipeline](VkPipeline.html) handles

* 
[](#VUID-vkCreateGraphicsPipelines-createInfoCount-arraylength) VUID-vkCreateGraphicsPipelines-createInfoCount-arraylength

 `createInfoCount` **must** be greater than `0`

* 
[](#VUID-vkCreateGraphicsPipelines-pipelineCache-parent) VUID-vkCreateGraphicsPipelines-pipelineCache-parent

 If `pipelineCache` is a valid handle, it **must** have been created, allocated, or retrieved from `device`

Return Codes

[Success](../../../../spec/latest/chapters/fundamentals.html#fundamentals-successcodes)

* 
`VK_PIPELINE_COMPILE_REQUIRED_EXT`

* 
`VK_SUCCESS`

[Failure](../../../../spec/latest/chapters/fundamentals.html#fundamentals-errorcodes)

* 
`VK_ERROR_INVALID_SHADER_NV`

* 
`VK_ERROR_OUT_OF_DEVICE_MEMORY`

* 
`VK_ERROR_OUT_OF_HOST_MEMORY`

* 
`VK_ERROR_UNKNOWN`

* 
`VK_ERROR_VALIDATION_FAILED`

[VK_VERSION_1_0](VK_VERSION_1_0.html), [VkAllocationCallbacks](VkAllocationCallbacks.html), [VkDevice](VkDevice.html), [VkGraphicsPipelineCreateInfo](VkGraphicsPipelineCreateInfo.html), [VkPipeline](VkPipeline.html), [VkPipelineCache](VkPipelineCache.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/pipelines.html#vkCreateGraphicsPipelines).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
