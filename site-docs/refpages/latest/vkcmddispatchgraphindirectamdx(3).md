# vkCmdDispatchGraphIndirectAMDX(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkCmdDispatchGraphIndirectAMDX.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkCmdDispatchGraphIndirectAMDX - Dispatch an execution graph with node and payload parameters read on the device

To record an execution graph dispatch with node and payload parameters read
on device, call:

// Provided by VK_AMDX_shader_enqueue
void vkCmdDispatchGraphIndirectAMDX(
    VkCommandBuffer                             commandBuffer,
    VkDeviceAddress                             scratch,
    VkDeviceSize                                scratchSize,
    const VkDispatchGraphCountInfoAMDX*         pCountInfo);

* 
`commandBuffer` is the command buffer into which the command will be
recorded.

* 
`scratch` is the address of scratch memory to be used.

* 
`scratchSize` is a range in bytes of scratch memory to be used.

* 
`pCountInfo` is a host pointer to a
[VkDispatchGraphCountInfoAMDX](VkDispatchGraphCountInfoAMDX.html) structure defining the nodes which
will be initially executed.

When this command is executed, the nodes specified in `pCountInfo` are
executed.
Nodes executed as part of this command are not implicitly synchronized in
any way against each other once they are dispatched.
There are no rasterization order guarantees between separately dispatched
graphics nodes, though individual primitives within a single dispatch do
adhere to rasterization order.
Draw calls executed before or after the execution graph also execute
relative to each graphics node with respect to rasterization order.

For this command, all device/host pointers in substructures are treated as
device pointers and read during device execution of this command.
The allocation and contents of these pointers only needs to be valid during
device execution.
All of these addresses will be read in the
`VK_PIPELINE_STAGE_2_COMPUTE_SHADER_BIT` pipeline stage with the
`VK_ACCESS_2_SHADER_STORAGE_READ_BIT` access flag.

Execution of this command **may** modify any memory locations in the range
[`scratch`,`scratch` + `scratchSize`).
Accesses to this memory range are performed in the
`VK_PIPELINE_STAGE_2_COMPUTE_SHADER_BIT` pipeline stage with the
`VK_ACCESS_2_SHADER_STORAGE_READ_BIT` and
`VK_ACCESS_2_SHADER_STORAGE_WRITE_BIT` access flags.

This command [captures command buffer state](../../../../spec/latest/chapters/executiongraphs.html#executiongraphs-meshnodes-statecapture) for mesh nodes similarly to draw commands.

Valid Usage

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-magFilter-04553) VUID-vkCmdDispatchGraphIndirectAMDX-magFilter-04553

If a [VkSampler](VkSampler.html) created with `magFilter` or `minFilter`
equal to `VK_FILTER_LINEAR`,
`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE`,
and `compareEnable` equal to `VK_FALSE` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_LINEAR_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-magFilter-09598) VUID-vkCmdDispatchGraphIndirectAMDX-magFilter-09598

If a [VkSampler](VkSampler.html) created with `magFilter` or `minFilter`
equal to `VK_FILTER_LINEAR` and `reductionMode` equal to either
`VK_SAMPLER_REDUCTION_MODE_MIN` or
`VK_SAMPLER_REDUCTION_MODE_MAX` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_MINMAX_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-mipmapMode-04770) VUID-vkCmdDispatchGraphIndirectAMDX-mipmapMode-04770

If a [VkSampler](VkSampler.html) created with `mipmapMode` equal to
`VK_SAMPLER_MIPMAP_MODE_LINEAR`,
`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE`,
and `compareEnable` equal to `VK_FALSE` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_LINEAR_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-mipmapMode-09599) VUID-vkCmdDispatchGraphIndirectAMDX-mipmapMode-09599

If a [VkSampler](VkSampler.html) created with `mipmapMode` equal to
`VK_SAMPLER_MIPMAP_MODE_LINEAR` and `reductionMode` equal to
either `VK_SAMPLER_REDUCTION_MODE_MIN` or
`VK_SAMPLER_REDUCTION_MODE_MAX` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_MINMAX_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-unnormalizedCoordinates-09635) VUID-vkCmdDispatchGraphIndirectAMDX-unnormalizedCoordinates-09635

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the image view’s `levelCount` and `layerCount`
**must** be 1

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08609) VUID-vkCmdDispatchGraphIndirectAMDX-None-08609

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the image view’s `viewType` **must** be
`VK_IMAGE_VIEW_TYPE_1D` or `VK_IMAGE_VIEW_TYPE_2D`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08610) VUID-vkCmdDispatchGraphIndirectAMDX-None-08610

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the sampler **must** not be used with any of the SPIR-V
`OpImageSample*` or `OpImageSparseSample*` instructions with
`ImplicitLod`, `Dref` or `Proj` in their name

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08611) VUID-vkCmdDispatchGraphIndirectAMDX-None-08611

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the sampler **must** not be used with any of the SPIR-V
`OpImageSample*` or `OpImageSparseSample*` instructions that includes a
LOD bias or any offset values

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-06479) VUID-vkCmdDispatchGraphIndirectAMDX-None-06479

If a [VkImageView](VkImageView.html) is sampled with
[depth comparison](../../../../spec/latest/chapters/textures.html#textures-depth-compare-operation), the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_SAMPLED_IMAGE_DEPTH_COMPARISON_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-02691) VUID-vkCmdDispatchGraphIndirectAMDX-None-02691

If a [VkImageView](VkImageView.html) is accessed using atomic operations as a result
of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_STORAGE_IMAGE_ATOMIC_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-07888) VUID-vkCmdDispatchGraphIndirectAMDX-None-07888

If a `VK_DESCRIPTOR_TYPE_STORAGE_TEXEL_BUFFER` descriptor is
accessed using atomic operations as a result of this command, then the
storage texel buffer’s [format    features](../../../../spec/latest/chapters/resources.html#resources-buffer-view-format-features) **must** contain
`VK_FORMAT_FEATURE_STORAGE_TEXEL_BUFFER_ATOMIC_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-02692) VUID-vkCmdDispatchGraphIndirectAMDX-None-02692

If a [VkImageView](VkImageView.html) is sampled with `VK_FILTER_CUBIC_EXT` as a
result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_CUBIC_BIT_EXT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-02693) VUID-vkCmdDispatchGraphIndirectAMDX-None-02693

If
the [VK_EXT_filter_cubic](VK_EXT_filter_cubic.html) extension is not enabled and
any [VkImageView](VkImageView.html) is sampled with `VK_FILTER_CUBIC_EXT` as a
result of this command, it **must** not have a [VkImageViewType](VkImageViewType.html) of
`VK_IMAGE_VIEW_TYPE_3D`, `VK_IMAGE_VIEW_TYPE_CUBE`, or
`VK_IMAGE_VIEW_TYPE_CUBE_ARRAY`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-filterCubic-02694) VUID-vkCmdDispatchGraphIndirectAMDX-filterCubic-02694

Any [VkImageView](VkImageView.html) being sampled with `VK_FILTER_CUBIC_EXT` as a
result of this command **must** have a [VkImageViewType](VkImageViewType.html) and format
that supports cubic filtering, as specified by
[VkFilterCubicImageViewImageFormatPropertiesEXT](VkFilterCubicImageViewImageFormatPropertiesEXT.html)::`filterCubic`
returned by [vkGetPhysicalDeviceImageFormatProperties2](vkGetPhysicalDeviceImageFormatProperties2.html)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-filterCubicMinmax-02695) VUID-vkCmdDispatchGraphIndirectAMDX-filterCubicMinmax-02695

Any [VkImageView](VkImageView.html) being sampled with `VK_FILTER_CUBIC_EXT` with
a reduction mode of either `VK_SAMPLER_REDUCTION_MODE_MIN` or
`VK_SAMPLER_REDUCTION_MODE_MAX` as a result of this command **must**
have a [VkImageViewType](VkImageViewType.html) and format that supports cubic filtering
together with minmax filtering, as specified by
[VkFilterCubicImageViewImageFormatPropertiesEXT](VkFilterCubicImageViewImageFormatPropertiesEXT.html)::`filterCubicMinmax`
returned by [vkGetPhysicalDeviceImageFormatProperties2](vkGetPhysicalDeviceImageFormatProperties2.html)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-cubicRangeClamp-09212) VUID-vkCmdDispatchGraphIndirectAMDX-cubicRangeClamp-09212

If the [`cubicRangeClamp`](../../../../spec/latest/chapters/features.html#features-cubicRangeClamp) feature is
not enabled, then any [VkImageView](VkImageView.html) being sampled with
`VK_FILTER_CUBIC_EXT` as a result of this command **must** not have a
[VkSamplerReductionModeCreateInfo](VkSamplerReductionModeCreateInfo.html)::`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE_RANGECLAMP_QCOM`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-reductionMode-09213) VUID-vkCmdDispatchGraphIndirectAMDX-reductionMode-09213

Any [VkImageView](VkImageView.html) being sampled with a
[VkSamplerReductionModeCreateInfo](VkSamplerReductionModeCreateInfo.html)::`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE_RANGECLAMP_QCOM` as a
result of this command **must** sample with `VK_FILTER_CUBIC_EXT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-selectableCubicWeights-09214) VUID-vkCmdDispatchGraphIndirectAMDX-selectableCubicWeights-09214

If the [`selectableCubicWeights`](../../../../spec/latest/chapters/features.html#features-selectableCubicWeights)
feature is not enabled, then any [VkImageView](VkImageView.html) being sampled with
`VK_FILTER_CUBIC_EXT` as a result of this command **must** have
[VkSamplerCubicWeightsCreateInfoQCOM](VkSamplerCubicWeightsCreateInfoQCOM.html)::`cubicWeights` equal to
`VK_CUBIC_FILTER_WEIGHTS_CATMULL_ROM_QCOM`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-flags-02696) VUID-vkCmdDispatchGraphIndirectAMDX-flags-02696

Any [VkImage](VkImage.html) created with a [VkImageCreateInfo](VkImageCreateInfo.html)::`flags`
containing `VK_IMAGE_CREATE_CORNER_SAMPLED_BIT_NV` sampled as a
result of this command **must** only be sampled using a
[VkSamplerAddressMode](VkSamplerAddressMode.html) of
`VK_SAMPLER_ADDRESS_MODE_CLAMP_TO_EDGE`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpTypeImage-07027) VUID-vkCmdDispatchGraphIndirectAMDX-OpTypeImage-07027

For any [VkImageView](VkImageView.html) being written as a storage image where the
image format field of the `OpTypeImage` is `Unknown`, the view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_WRITE_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpTypeImage-07028) VUID-vkCmdDispatchGraphIndirectAMDX-OpTypeImage-07028

For any [VkImageView](VkImageView.html) being read as a storage image where the image
format field of the `OpTypeImage` is `Unknown`, the view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_READ_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpTypeImage-07029) VUID-vkCmdDispatchGraphIndirectAMDX-OpTypeImage-07029

For any [VkBufferView](VkBufferView.html) being written as a storage texel buffer where
the image format field of the `OpTypeImage` is `Unknown`, the
view’s [buffer features](../../../../spec/latest/chapters/formats.html#VkFormatProperties3) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_WRITE_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpTypeImage-07030) VUID-vkCmdDispatchGraphIndirectAMDX-OpTypeImage-07030

Any [VkBufferView](VkBufferView.html) being read as a storage texel buffer where the
image format field of the `OpTypeImage` is `Unknown` then the
view’s [buffer features](../../../../spec/latest/chapters/formats.html#VkFormatProperties3) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_READ_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08600) VUID-vkCmdDispatchGraphIndirectAMDX-None-08600

For each set *n* that is statically used by [a bound    shader](../../../../spec/latest/chapters/shaders.html#shaders-binding), a descriptor set **must** have been bound to *n* at the same
pipeline bind point, with a [VkPipelineLayout](VkPipelineLayout.html) that is compatible
for set *n*, with the [VkPipelineLayout](VkPipelineLayout.html) used to create the current
[VkPipeline](VkPipeline.html)
or the [VkDescriptorSetLayout](VkDescriptorSetLayout.html) array used to create the current
[VkShaderEXT](VkShaderEXT.html)
, as described in [Pipeline Layout Compatibility](../../../../spec/latest/chapters/descriptorsets.html#descriptorsets-compatibility)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08601) VUID-vkCmdDispatchGraphIndirectAMDX-None-08601

For each push constant that is statically used by [a    bound shader](../../../../spec/latest/chapters/shaders.html#shaders-binding), a push constant value **must** have been set for the same
pipeline bind point, with a [VkPipelineLayout](VkPipelineLayout.html) that is compatible
for push constants, with the [VkPipelineLayout](VkPipelineLayout.html) used to create the
current [VkPipeline](VkPipeline.html)
or the [VkDescriptorSetLayout](VkDescriptorSetLayout.html) array used to create the current
[VkShaderEXT](VkShaderEXT.html)
, as described in [Pipeline Layout Compatibility](../../../../spec/latest/chapters/descriptorsets.html#descriptorsets-compatibility)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-10068) VUID-vkCmdDispatchGraphIndirectAMDX-None-10068

For each array of resources that is used by [a bound    shader](../../../../spec/latest/chapters/shaders.html#shaders-binding), the indices used to access members of the array **must** be less
than the descriptor count for the identified binding in the descriptor
sets used by this command

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-maintenance4-08602) VUID-vkCmdDispatchGraphIndirectAMDX-maintenance4-08602

If the [`maintenance4`](../../../../spec/latest/chapters/features.html#features-maintenance4) feature is not
enabled, then for each push constant that is statically used by
[a bound shader](../../../../spec/latest/chapters/shaders.html#shaders-binding), a push constant value **must** have
been set for the same pipeline bind point, with a [VkPipelineLayout](VkPipelineLayout.html)
that is compatible for push constants, with the [VkPipelineLayout](VkPipelineLayout.html)
used to create the current [VkPipeline](VkPipeline.html)
or the [VkDescriptorSetLayout](VkDescriptorSetLayout.html) and [VkPushConstantRange](VkPushConstantRange.html) arrays
used to create the current [VkShaderEXT](VkShaderEXT.html)
, as described in [Pipeline Layout Compatibility](../../../../spec/latest/chapters/descriptorsets.html#descriptorsets-compatibility)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08114) VUID-vkCmdDispatchGraphIndirectAMDX-None-08114

Descriptors in each bound descriptor set, specified via
[vkCmdBindDescriptorSets](vkCmdBindDescriptorSets.html), **must** be valid as described by
[descriptor validity](../../../../spec/latest/chapters/descriptorsets.html#descriptor-validity) if they are statically used
by
the [VkPipeline](VkPipeline.html) bound to the pipeline bind point used by this
command and the bound [VkPipeline](VkPipeline.html) was not created with
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-imageLayout-00344) VUID-vkCmdDispatchGraphIndirectAMDX-imageLayout-00344

If an image descriptor is accessed by a shader, the [VkImageLayout](VkImageLayout.html)
**must** match the subresource accessible from the [VkImageView](VkImageView.html) as
defined by the [image layout    matching rules](../../../../spec/latest/chapters/resources.html#resources-image-layouts-matching-rule)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08115) VUID-vkCmdDispatchGraphIndirectAMDX-None-08115

If the descriptors used by the [VkPipeline](VkPipeline.html) bound to the pipeline
bind point were specified via [vkCmdBindDescriptorSets](vkCmdBindDescriptorSets.html), the bound
[VkPipeline](VkPipeline.html) **must** have been created without
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08116) VUID-vkCmdDispatchGraphIndirectAMDX-None-08116

Descriptors in bound descriptor buffers, specified via
[vkCmdSetDescriptorBufferOffsetsEXT](vkCmdSetDescriptorBufferOffsetsEXT.html), **must** be valid if they are
dynamically used by the [VkPipeline](VkPipeline.html) bound to the pipeline bind
point used by this command and the bound [VkPipeline](VkPipeline.html) was created
with `VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08604) VUID-vkCmdDispatchGraphIndirectAMDX-None-08604

Descriptors in bound descriptor buffers, specified via
[vkCmdSetDescriptorBufferOffsetsEXT](vkCmdSetDescriptorBufferOffsetsEXT.html), **must** be valid if they are
dynamically used by any [VkShaderEXT](VkShaderEXT.html) bound to a stage corresponding
to the pipeline bind point used by this command

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08117) VUID-vkCmdDispatchGraphIndirectAMDX-None-08117

If the descriptors used by the [VkPipeline](VkPipeline.html) bound to the pipeline
bind point were specified via [vkCmdSetDescriptorBufferOffsetsEXT](vkCmdSetDescriptorBufferOffsetsEXT.html),
the bound [VkPipeline](VkPipeline.html) **must** have been created with
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08119) VUID-vkCmdDispatchGraphIndirectAMDX-None-08119

If a descriptor is dynamically used with a [VkPipeline](VkPipeline.html) created with
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`, the descriptor
memory **must** be resident

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08605) VUID-vkCmdDispatchGraphIndirectAMDX-None-08605

If a descriptor is dynamically used with a [VkShaderEXT](VkShaderEXT.html) created
with a `VkDescriptorSetLayout` that was created with
`VK_DESCRIPTOR_SET_LAYOUT_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`, the
descriptor memory **must** be resident

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08606) VUID-vkCmdDispatchGraphIndirectAMDX-None-08606

If the [`shaderObject`](../../../../spec/latest/chapters/features.html#features-shaderObject) feature is not
enabled, a
valid pipeline **must** be bound to the pipeline bind point used by this
command

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08608) VUID-vkCmdDispatchGraphIndirectAMDX-None-08608

If a pipeline is bound to the pipeline bind point used by this command,
there
**must** not have been any calls to dynamic state setting commands for any
state specified statically in the [VkPipeline](VkPipeline.html) object bound to the
pipeline bind point used by this command, since that pipeline was bound

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-uniformBuffers-06935) VUID-vkCmdDispatchGraphIndirectAMDX-uniformBuffers-06935

If any stage of the [VkPipeline](VkPipeline.html) object bound to the pipeline bind
point used by this command accesses a uniform buffer,
and that stage was created without enabling either
`VK_PIPELINE_ROBUSTNESS_BUFFER_BEHAVIOR_ROBUST_BUFFER_ACCESS` or
`VK_PIPELINE_ROBUSTNESS_BUFFER_BEHAVIOR_ROBUST_BUFFER_ACCESS_2` for
`uniformBuffers`,
and the [`robustBufferAccess`](../../../../spec/latest/chapters/features.html#features-robustBufferAccess)
feature is not enabled, that stage **must** not access values outside of
the range of the buffer as specified in the descriptor set bound to the
same pipeline bind point

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08612) VUID-vkCmdDispatchGraphIndirectAMDX-None-08612

If the [`robustBufferAccess`](../../../../spec/latest/chapters/features.html#features-robustBufferAccess) feature
is not enabled, and any [VkShaderEXT](VkShaderEXT.html) bound to a stage corresponding
to the pipeline bind point used by this command accesses a uniform
buffer, it **must** not access values outside of the range of the buffer as
specified in the descriptor set bound to the same pipeline bind point

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-storageBuffers-06936) VUID-vkCmdDispatchGraphIndirectAMDX-storageBuffers-06936

If any stage of the [VkPipeline](VkPipeline.html) object bound to the pipeline bind
point used by this command accesses a storage buffer,
and that stage was created without enabling either
`VK_PIPELINE_ROBUSTNESS_BUFFER_BEHAVIOR_ROBUST_BUFFER_ACCESS` or
`VK_PIPELINE_ROBUSTNESS_BUFFER_BEHAVIOR_ROBUST_BUFFER_ACCESS_2` for
`storageBuffers`,
and the [`robustBufferAccess`](../../../../spec/latest/chapters/features.html#features-robustBufferAccess)
feature is not enabled, that stage **must** not access values outside of
the range of the buffer as specified in the descriptor set bound to the
same pipeline bind point

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-08613) VUID-vkCmdDispatchGraphIndirectAMDX-None-08613

If the [`robustBufferAccess`](../../../../spec/latest/chapters/features.html#features-robustBufferAccess) feature
is not enabled, and any [VkShaderEXT](VkShaderEXT.html) bound to a stage corresponding
to the pipeline bind point used by this command accesses a storage
buffer, it **must** not access values outside of the range of the buffer as
specified in the descriptor set bound to the same pipeline bind point

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-02707) VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-02707

If `commandBuffer` is an unprotected command buffer and
[`protectedNoFault`](../../../../spec/latest/chapters/devsandqueues.html#limits-protectedNoFault) is not supported,
any resource accessed by [bound shaders](../../../../spec/latest/chapters/shaders.html#shaders-binding) **must** not be
a protected resource

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-viewType-07752) VUID-vkCmdDispatchGraphIndirectAMDX-viewType-07752

If a [VkImageView](VkImageView.html) is accessed as a result of this command, then the
image view’s `viewType` **must** match the `Dim` operand of the
`OpTypeImage` as described in [Compatibility Between SPIR-V Image Dimensions and Vulkan ImageView Types](../../../../spec/latest/appendices/spirvenv.html#spirvenv-image-dimensions)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-format-07753) VUID-vkCmdDispatchGraphIndirectAMDX-format-07753

If a [VkImageView](VkImageView.html) or [VkBufferView](VkBufferView.html) is accessed as a result of
this command, then the [numeric type](../../../../spec/latest/chapters/formats.html#formats-numericformat) of the
view’s `format` and the `Sampled` `Type` operand of the
`OpTypeImage` **must** match

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWrite-08795) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWrite-08795

If a [VkImageView](VkImageView.html)
created with a format other than `VK_FORMAT_A8_UNORM`
is accessed using `OpImageWrite` as a result of this command, then
the `Type` of the `Texel` operand of that instruction **must** have
at least as many components as the image view’s format

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWrite-08796) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWrite-08796

If a [VkImageView](VkImageView.html) created with the format `VK_FORMAT_A8_UNORM`
is accessed using `OpImageWrite` as a result of this command, then
the `Type` of the `Texel` operand of that instruction **must** have
four components

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWrite-04469) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWrite-04469

If a [VkBufferView](VkBufferView.html) is accessed using `OpImageWrite` as a result
of this command, then the `Type` of the `Texel` operand of that
instruction **must** have at least as many components as the buffer view’s
format

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-SampledType-04470) VUID-vkCmdDispatchGraphIndirectAMDX-SampledType-04470

If a [VkImageView](VkImageView.html) with a [VkFormat](VkFormat.html) that has a 64-bit component
width is accessed as a result of this command, the `SampledType` of
the `OpTypeImage` operand of that instruction **must** have a `Width`
of 64

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-SampledType-04471) VUID-vkCmdDispatchGraphIndirectAMDX-SampledType-04471

If a [VkImageView](VkImageView.html) with a [VkFormat](VkFormat.html) that has a component width
less than 64-bit is accessed as a result of this command, the
`SampledType` of the `OpTypeImage` operand of that instruction
**must** have a `Width` of 32

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-SampledType-04472) VUID-vkCmdDispatchGraphIndirectAMDX-SampledType-04472

If a [VkBufferView](VkBufferView.html) with a [VkFormat](VkFormat.html) that has a 64-bit
component width is accessed as a result of this command, the
`SampledType` of the `OpTypeImage` operand of that instruction
**must** have a `Width` of 64

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-SampledType-04473) VUID-vkCmdDispatchGraphIndirectAMDX-SampledType-04473

If a [VkBufferView](VkBufferView.html) with a [VkFormat](VkFormat.html) that has a component width
less than 64-bit is accessed as a result of this command, the
`SampledType` of the `OpTypeImage` operand of that instruction
**must** have a `Width` of 32

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-sparseImageInt64Atomics-04474) VUID-vkCmdDispatchGraphIndirectAMDX-sparseImageInt64Atomics-04474

If the [    `sparseImageInt64Atomics`](../../../../spec/latest/chapters/features.html#features-sparseImageInt64Atomics) feature is not enabled, [VkImage](VkImage.html)
objects created with the `VK_IMAGE_CREATE_SPARSE_RESIDENCY_BIT` flag
**must** not be accessed by atomic instructions through an `OpTypeImage`
with a `SampledType` with a `Width` of 64 by this command

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-sparseImageInt64Atomics-04475) VUID-vkCmdDispatchGraphIndirectAMDX-sparseImageInt64Atomics-04475

If the [    `sparseImageInt64Atomics`](../../../../spec/latest/chapters/features.html#features-sparseImageInt64Atomics) feature is not enabled, [VkBuffer](VkBuffer.html)
objects created with the `VK_BUFFER_CREATE_SPARSE_RESIDENCY_BIT`
flag **must** not be accessed by atomic instructions through an
`OpTypeImage` with a `SampledType` with a `Width` of 64 by this
command

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWeightedSampleQCOM-06971) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWeightedSampleQCOM-06971

If `OpImageWeightedSampleQCOM` is used to sample a [VkImageView](VkImageView.html)
as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_WEIGHT_SAMPLED_IMAGE_BIT_QCOM`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWeightedSampleQCOM-06972) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWeightedSampleQCOM-06972

If `OpImageWeightedSampleQCOM` uses a [VkImageView](VkImageView.html) as a sample
weight image as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_WEIGHT_IMAGE_BIT_QCOM`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBoxFilterQCOM-06973) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBoxFilterQCOM-06973

If `OpImageBoxFilterQCOM` is used to sample a [VkImageView](VkImageView.html) as a
result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BOX_FILTER_SAMPLED_BIT_QCOM`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchSSDQCOM-06974) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchSSDQCOM-06974

If `OpImageBlockMatchSSDQCOM` is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BLOCK_MATCHING_BIT_QCOM`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchSADQCOM-06975) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchSADQCOM-06975

If `OpImageBlockMatchSADQCOM` is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BLOCK_MATCHING_BIT_QCOM`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchSADQCOM-06976) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchSADQCOM-06976

If `OpImageBlockMatchSADQCOM` or OpImageBlockMatchSSDQCOM is used to
read from a reference image as result of this command, then the
specified reference coordinates **must** not fail
[integer texel coordinate    validation](../../../../spec/latest/chapters/textures.html#textures-integer-coordinate-validation)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWeightedSampleQCOM-06977) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWeightedSampleQCOM-06977

If `OpImageWeightedSampleQCOM`, `OpImageBoxFilterQCOM`,
`OpImageBlockMatchWindowSSDQCOM`,
`OpImageBlockMatchWindowSADQCOM`,
`OpImageBlockMatchGatherSSDQCOM`,
`OpImageBlockMatchGatherSADQCOM`,
`OpImageBlockMatchSSDQCOM`, or `OpImageBlockMatchSADQCOM` uses a
[VkSampler](VkSampler.html) as a result of this command, then the sampler **must** have
been created with `VK_SAMPLER_CREATE_IMAGE_PROCESSING_BIT_QCOM`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWeightedSampleQCOM-06978) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageWeightedSampleQCOM-06978

If any command other than `OpImageWeightedSampleQCOM`,
`OpImageBoxFilterQCOM`,
`OpImageBlockMatchWindowSSDQCOM`,
`OpImageBlockMatchWindowSADQCOM`,
`OpImageBlockMatchGatherSSDQCOM`,
`OpImageBlockMatchGatherSADQCOM`,
`OpImageBlockMatchSSDQCOM`, or `OpImageBlockMatchSADQCOM` uses a
[VkSampler](VkSampler.html) as a result of this command, then the sampler **must** not
have been created with `VK_SAMPLER_CREATE_IMAGE_PROCESSING_BIT_QCOM`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchWindow-09215) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchWindow-09215

If a `OpImageBlockMatchWindow*QCOM` or
`OpImageBlockMatchGather*QCOM` instruction is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BLOCK_MATCHING_BIT_QCOM`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchWindow-09216) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchWindow-09216

If a `OpImageBlockMatchWindow*QCOM` or
`OpImageBlockMatchGather*QCOM` instruction is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
format **must** be a single-component format

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchWindow-09217) VUID-vkCmdDispatchGraphIndirectAMDX-OpImageBlockMatchWindow-09217

If a `OpImageBlockMatchWindow*QCOM` or
`OpImageBlockMatchGather*QCOM` read from a reference image as result
of this command, then the specified reference coordinates **must** not fail
[integer texel coordinate    validation](../../../../spec/latest/chapters/textures.html#textures-integer-coordinate-validation)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-07288) VUID-vkCmdDispatchGraphIndirectAMDX-None-07288

Any shader invocation executed by this command **must**
[terminate](../../../../spec/latest/chapters/shaders.html#shaders-termination)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-09600) VUID-vkCmdDispatchGraphIndirectAMDX-None-09600

If a descriptor with type equal to any of
`VK_DESCRIPTOR_TYPE_SAMPLE_WEIGHT_IMAGE_QCOM`,
`VK_DESCRIPTOR_TYPE_BLOCK_MATCH_IMAGE_QCOM`,
`VK_DESCRIPTOR_TYPE_SAMPLED_IMAGE`,
`VK_DESCRIPTOR_TYPE_STORAGE_IMAGE`, or
`VK_DESCRIPTOR_TYPE_INPUT_ATTACHMENT` is accessed as a result of
this command, all image subresources identified by that descriptor **must**
be in the image layout identified when the descriptor was written

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-10746) VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-10746

The `VkDeviceMemory` object allocated from a `VkMemoryHeap` with
the `VK_MEMORY_HEAP_TILE_MEMORY_BIT_QCOM` property that is bound to
a resource accessed as a result of this command **must** be the active
bound [bound tile memory object](../../../../spec/latest/chapters/memory.html#memory-bind-tile-memory) in
`commandBuffer`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-10678) VUID-vkCmdDispatchGraphIndirectAMDX-None-10678

If this command is recorded inside a [tile    shading render pass](../../../../spec/latest/chapters/renderpass.html#renderpass-tile-shading) instance, the stages corresponding to the pipeline
bind point used by this command **must** only include
`VK_SHADER_STAGE_VERTEX_BIT`, `VK_SHADER_STAGE_FRAGMENT_BIT`,
and/or `VK_SHADER_STAGE_COMPUTE_BIT`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-10679) VUID-vkCmdDispatchGraphIndirectAMDX-None-10679

If this command is recorded where
[per-tile execution model](../../../../spec/latest/chapters/renderpass.html#renderpass-per-tile-execution-model) is
enabled, there **must** be no access to any image while the image was be
transitioned to the
`VK_IMAGE_LAYOUT_ATTACHMENT_FEEDBACK_LOOP_OPTIMAL_EXT` layout

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-pDescription-09900) VUID-vkCmdDispatchGraphIndirectAMDX-pDescription-09900

If a `VK_DESCRIPTOR_TYPE_TENSOR_ARM` descriptor is accessed as a
result of this command, then the underlying [VkTensorARM](VkTensorARM.html) object
**must** have been created with a
[VkTensorCreateInfoARM](VkTensorCreateInfoARM.html)::`pDescription` whose `usage` member
contained `VK_TENSOR_USAGE_SHADER_BIT_ARM`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-dimensionCount-09905) VUID-vkCmdDispatchGraphIndirectAMDX-dimensionCount-09905

If a `VK_DESCRIPTOR_TYPE_TENSOR_ARM` descriptor is accessed as a
result of this command, then the `Rank` of the `OpTypeTensorARM`
of the tensor resource variable **must** be equal to the
`dimensionCount` provided via
[VkTensorCreateInfoARM](VkTensorCreateInfoARM.html)::`pDescription` when creating the
underlying [VkTensorARM](VkTensorARM.html) object

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-OpTypeTensorARM-09906) VUID-vkCmdDispatchGraphIndirectAMDX-OpTypeTensorARM-09906

If a `VK_DESCRIPTOR_TYPE_TENSOR_ARM` descriptor is accessed as a
result of this command, then the element type of the
`OpTypeTensorARM` of the tensor resource variable **must** be
[compatible](../../../../spec/latest/appendices/spirvenv.html#spirvenv-tensor-formats) with the [VkFormat](VkFormat.html) of the
[VkTensorViewARM](VkTensorViewARM.html) used for the access

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-09181) VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-09181

`commandBuffer` **must** not be a protected command buffer

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-09182) VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-09182

`commandBuffer` **must** be a primary command buffer

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-scratch-10192) VUID-vkCmdDispatchGraphIndirectAMDX-scratch-10192

`scratch` **must** be the device address of an allocated memory range
at least as large as `scratchSize`

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-scratchSize-10193) VUID-vkCmdDispatchGraphIndirectAMDX-scratchSize-10193

`scratchSize` **must** be greater than or equal to
[VkExecutionGraphPipelineScratchSizeAMDX](VkExecutionGraphPipelineScratchSizeAMDX.html)::`minSize` returned by
[vkGetExecutionGraphPipelineScratchSizeAMDX](vkGetExecutionGraphPipelineScratchSizeAMDX.html) for the bound execution
graph pipeline

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-scratch-09184) VUID-vkCmdDispatchGraphIndirectAMDX-scratch-09184

`scratch` **must** be a device address within a [VkBuffer](VkBuffer.html) created
with the `VK_BUFFER_USAGE_EXECUTION_GRAPH_SCRATCH_BIT_AMDX`
or `VK_BUFFER_USAGE_2_EXECUTION_GRAPH_SCRATCH_BIT_AMDX`
usage flags set

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-scratch-10194) VUID-vkCmdDispatchGraphIndirectAMDX-scratch-10194

The device memory range [`scratch`,`scratch`

`scratchSize`] **must** have been initialized with
[vkCmdInitializeGraphScratchMemoryAMDX](vkCmdInitializeGraphScratchMemoryAMDX.html) using the bound execution
graph pipeline, and not modified after that by anything other than
another execution graph dispatch command

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-maxComputeWorkGroupCount-09186) VUID-vkCmdDispatchGraphIndirectAMDX-maxComputeWorkGroupCount-09186

Execution of this command **must** not cause a node to be dispatched with a
larger number of workgroups than that specified by either a
`MaxNumWorkgroupsAMDX` decoration in the dispatched node or
[`maxComputeWorkGroupCount`](../../../../spec/latest/chapters/limits.html#limits-maxComputeWorkGroupCount)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-maxExecutionGraphShaderPayloadCount-09187) VUID-vkCmdDispatchGraphIndirectAMDX-maxExecutionGraphShaderPayloadCount-09187

Execution of this command **must** not cause any shader to initialize more
than [    `maxExecutionGraphShaderPayloadCount`](../../../../spec/latest/chapters/limits.html#limits-maxExecutionGraphShaderPayloadCount) output payloads

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-NodeMaxPayloadsAMDX-09188) VUID-vkCmdDispatchGraphIndirectAMDX-NodeMaxPayloadsAMDX-09188

Execution of this command **must** not cause any shader that declares
`NodeMaxPayloadsAMDX` to initialize more output payloads than
specified by the max number of payloads for that decoration.
This requirement applies to each `NodeMaxPayloadsAMDX` decoration
separately

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-None-10195) VUID-vkCmdDispatchGraphIndirectAMDX-None-10195

   If the bound execution graph pipeline includes draw nodes, this command
   **must** be called within a render pass instance that is
compatible with the graphics pipeline used to create each of those nodes

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09150) VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09150

`pCountInfo->infos` **must** be a device pointer to a memory allocation
at least as large as the product of `count` and `stride` when
this command is executed on the device

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09151) VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09151

`pCountInfo->infos` **must** be a device address within a
[VkBuffer](VkBuffer.html) created with the
`VK_BUFFER_USAGE_INDIRECT_BUFFER_BIT` usage flag set

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09152) VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09152

`pCountInfo->infos` **must** be a multiple of
[    `executionGraphDispatchAddressAlignment`](../../../../spec/latest/chapters/limits.html#limits-executionGraphDispatchAddressAlignment)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-infos-09153) VUID-vkCmdDispatchGraphIndirectAMDX-infos-09153

Device memory locations at indexes in the range [`infos`,
`infos` + (`count`*`stride`)), at a granularity of
`stride` **must** contain valid [VkDispatchGraphInfoAMDX](VkDispatchGraphInfoAMDX.html)
structures in the first 24 bytes when this command is executed on the
device

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09154) VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09154

For each [VkDispatchGraphInfoAMDX](VkDispatchGraphInfoAMDX.html) structure in
`pCountInfo->infos`, `payloads` **must** be a device pointer to a
memory allocation at least as large as the product of `payloadCount`
and `payloadStride` when this command is executed on the device

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09155) VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09155

For each [VkDispatchGraphInfoAMDX](VkDispatchGraphInfoAMDX.html) structure in
`pCountInfo->infos`, `payloads` **must** be a device address within
a [VkBuffer](VkBuffer.html) created with the
`VK_BUFFER_USAGE_INDIRECT_BUFFER_BIT` usage flag set

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09156) VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09156

For each [VkDispatchGraphInfoAMDX](VkDispatchGraphInfoAMDX.html) structure in
`pCountInfo->infos`, `payloads` **must** be a multiple of
[    `executionGraphDispatchAddressAlignment`](../../../../spec/latest/chapters/limits.html#limits-executionGraphDispatchAddressAlignment)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09157) VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09157

For each [VkDispatchGraphInfoAMDX](VkDispatchGraphInfoAMDX.html) structure in
`pCountInfo->infos`, `nodeIndex` **must** be a valid node index in
the bound execution graph pipeline, as returned by
[vkGetExecutionGraphPipelineNodeIndexAMDX](vkGetExecutionGraphPipelineNodeIndexAMDX.html) when this command is
executed on the device

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09158) VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-09158

For each [VkDispatchGraphInfoAMDX](VkDispatchGraphInfoAMDX.html) structure in
`pCountInfo->infos`, device memory locations at indexes in the range
[`payloads`, `payloads` + (`payloadCount` *
`payloadStride`)), at a granularity of `payloadStride` **must**
contain a payload matching the size of the input payload expected by the
node in `nodeIndex` in the first bytes when this command is executed
on the device

Valid Usage (Implicit)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-parameter) VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-parameter

 `commandBuffer` **must** be a valid [VkCommandBuffer](VkCommandBuffer.html) handle

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-scratch-parameter) VUID-vkCmdDispatchGraphIndirectAMDX-scratch-parameter

 `scratch` **must** be a valid `VkDeviceAddress` value

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-parameter) VUID-vkCmdDispatchGraphIndirectAMDX-pCountInfo-parameter

 `pCountInfo` **must** be a valid pointer to a valid [VkDispatchGraphCountInfoAMDX](VkDispatchGraphCountInfoAMDX.html) structure

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-recording) VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-recording

 `commandBuffer` **must** be in the [recording state](../../../../spec/latest/chapters/cmdbuffers.html#commandbuffers-lifecycle)

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-cmdpool) VUID-vkCmdDispatchGraphIndirectAMDX-commandBuffer-cmdpool

 The `VkCommandPool` that `commandBuffer` was allocated from **must** support `VK_QUEUE_COMPUTE_BIT`, or `VK_QUEUE_GRAPHICS_BIT` operations

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-suspended) VUID-vkCmdDispatchGraphIndirectAMDX-suspended

 This command **must** not be called between suspended render pass instances

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-videocoding) VUID-vkCmdDispatchGraphIndirectAMDX-videocoding

 This command **must** only be called outside of a video coding scope

* 
[](#VUID-vkCmdDispatchGraphIndirectAMDX-bufferlevel) VUID-vkCmdDispatchGraphIndirectAMDX-bufferlevel

 `commandBuffer` **must** be a primary `VkCommandBuffer`

Host Synchronization

* 
Host access to the `VkCommandPool` that `commandBuffer` was allocated from **must** be externally synchronized

Command Properties
| [Command Buffer Levels](../../../../spec/latest/chapters/cmdbuffers.html#VkCommandBufferLevel) | [Render Pass Scope](../../../../spec/latest/chapters/renderpass.html#vkCmdBeginRenderPass) | [Video Coding Scope](../../../../spec/latest/chapters/videocoding.html#vkCmdBeginVideoCodingKHR) | [Supported Queue Types](../../../../spec/latest/chapters/devsandqueues.html#VkQueueFlagBits) | [Command Type](../../../../spec/latest/chapters/fundamentals.html#fundamentals-queueoperation-command-types) |
| --- | --- | --- | --- | --- |
| Primary | Both | Outside | VK_QUEUE_COMPUTE_BIT

VK_QUEUE_GRAPHICS_BIT | Action |

Conditional Rendering

vkCmdDispatchGraphIndirectAMDX is affected by [conditional rendering](../../../../spec/latest/chapters/drawing.html#drawing-conditional-rendering)

[VK_AMDX_shader_enqueue](VK_AMDX_shader_enqueue.html), [VkCommandBuffer](VkCommandBuffer.html), `VkDeviceAddress`, `VkDeviceSize`, [VkDispatchGraphCountInfoAMDX](VkDispatchGraphCountInfoAMDX.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/executiongraphs.html#vkCmdDispatchGraphIndirectAMDX).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
