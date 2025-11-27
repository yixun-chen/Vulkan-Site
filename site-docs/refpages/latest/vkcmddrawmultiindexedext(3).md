# vkCmdDrawMultiIndexedEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkCmdDrawMultiIndexedEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkCmdDrawMultiIndexedEXT - Draw primitives

To record an ordered sequence of indexed draws which have no state changes
between them, call:

// Provided by VK_EXT_multi_draw
void vkCmdDrawMultiIndexedEXT(
    VkCommandBuffer                             commandBuffer,
    uint32_t                                    drawCount,
    const VkMultiDrawIndexedInfoEXT*            pIndexInfo,
    uint32_t                                    instanceCount,
    uint32_t                                    firstInstance,
    uint32_t                                    stride,
    const int32_t*                              pVertexOffset);

* 
`commandBuffer` is the command buffer into which the command is
recorded.

* 
`drawCount` is the number of draws to execute, and **can** be zero.

* 
`pIndexInfo` is a pointer to an array of
[VkMultiDrawIndexedInfoEXT](VkMultiDrawIndexedInfoEXT.html) with index information to be drawn.

* 
`instanceCount` is the number of instances per draw.

* 
`firstInstance` is the instance ID of the first instance in each
draw.

* 
`stride` is the byte stride between consecutive elements of
`pIndexInfo`.

* 
`pVertexOffset` is `NULL` or a pointer to the value added to the
vertex index before indexing into the vertex buffer.
When specified, `VkMultiDrawIndexedInfoEXT`::`offset` is
ignored.

The number of draws recorded is `drawCount`, with each draw reading,
sequentially, a `firstIndex` and an `indexCount` from
`pIndexInfo`.
For each recorded draw, primitives are assembled as for
[vkCmdDrawIndexed](vkCmdDrawIndexed.html), and drawn `instanceCount` times with
`instanceIndex` starting with `firstInstance` and sequentially for
each instance.
If `pVertexOffset` is `NULL`, a `vertexOffset` is also read from
`pIndexInfo`, otherwise the value from dereferencing `pVertexOffset`
is used.

Valid Usage

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-magFilter-04553) VUID-vkCmdDrawMultiIndexedEXT-magFilter-04553

If a [VkSampler](VkSampler.html) created with `magFilter` or `minFilter`
equal to `VK_FILTER_LINEAR`,
`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE`,
and `compareEnable` equal to `VK_FALSE` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_LINEAR_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-magFilter-09598) VUID-vkCmdDrawMultiIndexedEXT-magFilter-09598

If a [VkSampler](VkSampler.html) created with `magFilter` or `minFilter`
equal to `VK_FILTER_LINEAR` and `reductionMode` equal to either
`VK_SAMPLER_REDUCTION_MODE_MIN` or
`VK_SAMPLER_REDUCTION_MODE_MAX` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_MINMAX_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-mipmapMode-04770) VUID-vkCmdDrawMultiIndexedEXT-mipmapMode-04770

If a [VkSampler](VkSampler.html) created with `mipmapMode` equal to
`VK_SAMPLER_MIPMAP_MODE_LINEAR`,
`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE`,
and `compareEnable` equal to `VK_FALSE` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_LINEAR_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-mipmapMode-09599) VUID-vkCmdDrawMultiIndexedEXT-mipmapMode-09599

If a [VkSampler](VkSampler.html) created with `mipmapMode` equal to
`VK_SAMPLER_MIPMAP_MODE_LINEAR` and `reductionMode` equal to
either `VK_SAMPLER_REDUCTION_MODE_MIN` or
`VK_SAMPLER_REDUCTION_MODE_MAX` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_MINMAX_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-unnormalizedCoordinates-09635) VUID-vkCmdDrawMultiIndexedEXT-unnormalizedCoordinates-09635

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the image view’s `levelCount` and `layerCount`
**must** be 1

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08609) VUID-vkCmdDrawMultiIndexedEXT-None-08609

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the image view’s `viewType` **must** be
`VK_IMAGE_VIEW_TYPE_1D` or `VK_IMAGE_VIEW_TYPE_2D`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08610) VUID-vkCmdDrawMultiIndexedEXT-None-08610

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the sampler **must** not be used with any of the SPIR-V
`OpImageSample*` or `OpImageSparseSample*` instructions with
`ImplicitLod`, `Dref` or `Proj` in their name

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08611) VUID-vkCmdDrawMultiIndexedEXT-None-08611

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the sampler **must** not be used with any of the SPIR-V
`OpImageSample*` or `OpImageSparseSample*` instructions that includes a
LOD bias or any offset values

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-06479) VUID-vkCmdDrawMultiIndexedEXT-None-06479

If a [VkImageView](VkImageView.html) is sampled with
[depth comparison](../../../../spec/latest/chapters/textures.html#textures-depth-compare-operation), the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_SAMPLED_IMAGE_DEPTH_COMPARISON_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-02691) VUID-vkCmdDrawMultiIndexedEXT-None-02691

If a [VkImageView](VkImageView.html) is accessed using atomic operations as a result
of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_STORAGE_IMAGE_ATOMIC_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-07888) VUID-vkCmdDrawMultiIndexedEXT-None-07888

If a `VK_DESCRIPTOR_TYPE_STORAGE_TEXEL_BUFFER` descriptor is
accessed using atomic operations as a result of this command, then the
storage texel buffer’s [format    features](../../../../spec/latest/chapters/resources.html#resources-buffer-view-format-features) **must** contain
`VK_FORMAT_FEATURE_STORAGE_TEXEL_BUFFER_ATOMIC_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-02692) VUID-vkCmdDrawMultiIndexedEXT-None-02692

If a [VkImageView](VkImageView.html) is sampled with `VK_FILTER_CUBIC_EXT` as a
result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_CUBIC_BIT_EXT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-02693) VUID-vkCmdDrawMultiIndexedEXT-None-02693

If
the [VK_EXT_filter_cubic](VK_EXT_filter_cubic.html) extension is not enabled and
any [VkImageView](VkImageView.html) is sampled with `VK_FILTER_CUBIC_EXT` as a
result of this command, it **must** not have a [VkImageViewType](VkImageViewType.html) of
`VK_IMAGE_VIEW_TYPE_3D`, `VK_IMAGE_VIEW_TYPE_CUBE`, or
`VK_IMAGE_VIEW_TYPE_CUBE_ARRAY`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-filterCubic-02694) VUID-vkCmdDrawMultiIndexedEXT-filterCubic-02694

Any [VkImageView](VkImageView.html) being sampled with `VK_FILTER_CUBIC_EXT` as a
result of this command **must** have a [VkImageViewType](VkImageViewType.html) and format
that supports cubic filtering, as specified by
[VkFilterCubicImageViewImageFormatPropertiesEXT](VkFilterCubicImageViewImageFormatPropertiesEXT.html)::`filterCubic`
returned by [vkGetPhysicalDeviceImageFormatProperties2](vkGetPhysicalDeviceImageFormatProperties2.html)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-filterCubicMinmax-02695) VUID-vkCmdDrawMultiIndexedEXT-filterCubicMinmax-02695

Any [VkImageView](VkImageView.html) being sampled with `VK_FILTER_CUBIC_EXT` with
a reduction mode of either `VK_SAMPLER_REDUCTION_MODE_MIN` or
`VK_SAMPLER_REDUCTION_MODE_MAX` as a result of this command **must**
have a [VkImageViewType](VkImageViewType.html) and format that supports cubic filtering
together with minmax filtering, as specified by
[VkFilterCubicImageViewImageFormatPropertiesEXT](VkFilterCubicImageViewImageFormatPropertiesEXT.html)::`filterCubicMinmax`
returned by [vkGetPhysicalDeviceImageFormatProperties2](vkGetPhysicalDeviceImageFormatProperties2.html)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-cubicRangeClamp-09212) VUID-vkCmdDrawMultiIndexedEXT-cubicRangeClamp-09212

If the [`cubicRangeClamp`](../../../../spec/latest/chapters/features.html#features-cubicRangeClamp) feature is
not enabled, then any [VkImageView](VkImageView.html) being sampled with
`VK_FILTER_CUBIC_EXT` as a result of this command **must** not have a
[VkSamplerReductionModeCreateInfo](VkSamplerReductionModeCreateInfo.html)::`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE_RANGECLAMP_QCOM`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-reductionMode-09213) VUID-vkCmdDrawMultiIndexedEXT-reductionMode-09213

Any [VkImageView](VkImageView.html) being sampled with a
[VkSamplerReductionModeCreateInfo](VkSamplerReductionModeCreateInfo.html)::`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE_RANGECLAMP_QCOM` as a
result of this command **must** sample with `VK_FILTER_CUBIC_EXT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-selectableCubicWeights-09214) VUID-vkCmdDrawMultiIndexedEXT-selectableCubicWeights-09214

If the [`selectableCubicWeights`](../../../../spec/latest/chapters/features.html#features-selectableCubicWeights)
feature is not enabled, then any [VkImageView](VkImageView.html) being sampled with
`VK_FILTER_CUBIC_EXT` as a result of this command **must** have
[VkSamplerCubicWeightsCreateInfoQCOM](VkSamplerCubicWeightsCreateInfoQCOM.html)::`cubicWeights` equal to
`VK_CUBIC_FILTER_WEIGHTS_CATMULL_ROM_QCOM`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-flags-02696) VUID-vkCmdDrawMultiIndexedEXT-flags-02696

Any [VkImage](VkImage.html) created with a [VkImageCreateInfo](VkImageCreateInfo.html)::`flags`
containing `VK_IMAGE_CREATE_CORNER_SAMPLED_BIT_NV` sampled as a
result of this command **must** only be sampled using a
[VkSamplerAddressMode](VkSamplerAddressMode.html) of
`VK_SAMPLER_ADDRESS_MODE_CLAMP_TO_EDGE`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpTypeImage-07027) VUID-vkCmdDrawMultiIndexedEXT-OpTypeImage-07027

For any [VkImageView](VkImageView.html) being written as a storage image where the
image format field of the `OpTypeImage` is `Unknown`, the view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_WRITE_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpTypeImage-07028) VUID-vkCmdDrawMultiIndexedEXT-OpTypeImage-07028

For any [VkImageView](VkImageView.html) being read as a storage image where the image
format field of the `OpTypeImage` is `Unknown`, the view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_READ_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpTypeImage-07029) VUID-vkCmdDrawMultiIndexedEXT-OpTypeImage-07029

For any [VkBufferView](VkBufferView.html) being written as a storage texel buffer where
the image format field of the `OpTypeImage` is `Unknown`, the
view’s [buffer features](../../../../spec/latest/chapters/formats.html#VkFormatProperties3) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_WRITE_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpTypeImage-07030) VUID-vkCmdDrawMultiIndexedEXT-OpTypeImage-07030

Any [VkBufferView](VkBufferView.html) being read as a storage texel buffer where the
image format field of the `OpTypeImage` is `Unknown` then the
view’s [buffer features](../../../../spec/latest/chapters/formats.html#VkFormatProperties3) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_READ_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08600) VUID-vkCmdDrawMultiIndexedEXT-None-08600

For each set *n* that is statically used by [a bound    shader](../../../../spec/latest/chapters/shaders.html#shaders-binding), a descriptor set **must** have been bound to *n* at the same
pipeline bind point, with a [VkPipelineLayout](VkPipelineLayout.html) that is compatible
for set *n*, with the [VkPipelineLayout](VkPipelineLayout.html) used to create the current
[VkPipeline](VkPipeline.html)
or the [VkDescriptorSetLayout](VkDescriptorSetLayout.html) array used to create the current
[VkShaderEXT](VkShaderEXT.html)
, as described in [Pipeline Layout Compatibility](../../../../spec/latest/chapters/descriptorsets.html#descriptorsets-compatibility)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08601) VUID-vkCmdDrawMultiIndexedEXT-None-08601

For each push constant that is statically used by [a    bound shader](../../../../spec/latest/chapters/shaders.html#shaders-binding), a push constant value **must** have been set for the same
pipeline bind point, with a [VkPipelineLayout](VkPipelineLayout.html) that is compatible
for push constants, with the [VkPipelineLayout](VkPipelineLayout.html) used to create the
current [VkPipeline](VkPipeline.html)
or the [VkDescriptorSetLayout](VkDescriptorSetLayout.html) array used to create the current
[VkShaderEXT](VkShaderEXT.html)
, as described in [Pipeline Layout Compatibility](../../../../spec/latest/chapters/descriptorsets.html#descriptorsets-compatibility)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-10068) VUID-vkCmdDrawMultiIndexedEXT-None-10068

For each array of resources that is used by [a bound    shader](../../../../spec/latest/chapters/shaders.html#shaders-binding), the indices used to access members of the array **must** be less
than the descriptor count for the identified binding in the descriptor
sets used by this command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-maintenance4-08602) VUID-vkCmdDrawMultiIndexedEXT-maintenance4-08602

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
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08114) VUID-vkCmdDrawMultiIndexedEXT-None-08114

Descriptors in each bound descriptor set, specified via
[vkCmdBindDescriptorSets](vkCmdBindDescriptorSets.html), **must** be valid as described by
[descriptor validity](../../../../spec/latest/chapters/descriptorsets.html#descriptor-validity) if they are statically used
by
the [VkPipeline](VkPipeline.html) bound to the pipeline bind point used by this
command and the bound [VkPipeline](VkPipeline.html) was not created with
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-imageLayout-00344) VUID-vkCmdDrawMultiIndexedEXT-imageLayout-00344

If an image descriptor is accessed by a shader, the [VkImageLayout](VkImageLayout.html)
**must** match the subresource accessible from the [VkImageView](VkImageView.html) as
defined by the [image layout    matching rules](../../../../spec/latest/chapters/resources.html#resources-image-layouts-matching-rule)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08115) VUID-vkCmdDrawMultiIndexedEXT-None-08115

If the descriptors used by the [VkPipeline](VkPipeline.html) bound to the pipeline
bind point were specified via [vkCmdBindDescriptorSets](vkCmdBindDescriptorSets.html), the bound
[VkPipeline](VkPipeline.html) **must** have been created without
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08116) VUID-vkCmdDrawMultiIndexedEXT-None-08116

Descriptors in bound descriptor buffers, specified via
[vkCmdSetDescriptorBufferOffsetsEXT](vkCmdSetDescriptorBufferOffsetsEXT.html), **must** be valid if they are
dynamically used by the [VkPipeline](VkPipeline.html) bound to the pipeline bind
point used by this command and the bound [VkPipeline](VkPipeline.html) was created
with `VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08604) VUID-vkCmdDrawMultiIndexedEXT-None-08604

Descriptors in bound descriptor buffers, specified via
[vkCmdSetDescriptorBufferOffsetsEXT](vkCmdSetDescriptorBufferOffsetsEXT.html), **must** be valid if they are
dynamically used by any [VkShaderEXT](VkShaderEXT.html) bound to a stage corresponding
to the pipeline bind point used by this command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08117) VUID-vkCmdDrawMultiIndexedEXT-None-08117

If the descriptors used by the [VkPipeline](VkPipeline.html) bound to the pipeline
bind point were specified via [vkCmdSetDescriptorBufferOffsetsEXT](vkCmdSetDescriptorBufferOffsetsEXT.html),
the bound [VkPipeline](VkPipeline.html) **must** have been created with
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08119) VUID-vkCmdDrawMultiIndexedEXT-None-08119

If a descriptor is dynamically used with a [VkPipeline](VkPipeline.html) created with
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`, the descriptor
memory **must** be resident

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08605) VUID-vkCmdDrawMultiIndexedEXT-None-08605

If a descriptor is dynamically used with a [VkShaderEXT](VkShaderEXT.html) created
with a `VkDescriptorSetLayout` that was created with
`VK_DESCRIPTOR_SET_LAYOUT_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`, the
descriptor memory **must** be resident

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08606) VUID-vkCmdDrawMultiIndexedEXT-None-08606

If the [`shaderObject`](../../../../spec/latest/chapters/features.html#features-shaderObject) feature is not
enabled, a
valid pipeline **must** be bound to the pipeline bind point used by this
command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08608) VUID-vkCmdDrawMultiIndexedEXT-None-08608

If a pipeline is bound to the pipeline bind point used by this command,
there
**must** not have been any calls to dynamic state setting commands for any
state specified statically in the [VkPipeline](VkPipeline.html) object bound to the
pipeline bind point used by this command, since that pipeline was bound

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-uniformBuffers-06935) VUID-vkCmdDrawMultiIndexedEXT-uniformBuffers-06935

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
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08612) VUID-vkCmdDrawMultiIndexedEXT-None-08612

If the [`robustBufferAccess`](../../../../spec/latest/chapters/features.html#features-robustBufferAccess) feature
is not enabled, and any [VkShaderEXT](VkShaderEXT.html) bound to a stage corresponding
to the pipeline bind point used by this command accesses a uniform
buffer, it **must** not access values outside of the range of the buffer as
specified in the descriptor set bound to the same pipeline bind point

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-storageBuffers-06936) VUID-vkCmdDrawMultiIndexedEXT-storageBuffers-06936

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
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08613) VUID-vkCmdDrawMultiIndexedEXT-None-08613

If the [`robustBufferAccess`](../../../../spec/latest/chapters/features.html#features-robustBufferAccess) feature
is not enabled, and any [VkShaderEXT](VkShaderEXT.html) bound to a stage corresponding
to the pipeline bind point used by this command accesses a storage
buffer, it **must** not access values outside of the range of the buffer as
specified in the descriptor set bound to the same pipeline bind point

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-02707) VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-02707

If `commandBuffer` is an unprotected command buffer and
[`protectedNoFault`](../../../../spec/latest/chapters/devsandqueues.html#limits-protectedNoFault) is not supported,
any resource accessed by [bound shaders](../../../../spec/latest/chapters/shaders.html#shaders-binding) **must** not be
a protected resource

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-viewType-07752) VUID-vkCmdDrawMultiIndexedEXT-viewType-07752

If a [VkImageView](VkImageView.html) is accessed as a result of this command, then the
image view’s `viewType` **must** match the `Dim` operand of the
`OpTypeImage` as described in [Compatibility Between SPIR-V Image Dimensions and Vulkan ImageView Types](../../../../spec/latest/appendices/spirvenv.html#spirvenv-image-dimensions)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-format-07753) VUID-vkCmdDrawMultiIndexedEXT-format-07753

If a [VkImageView](VkImageView.html) or [VkBufferView](VkBufferView.html) is accessed as a result of
this command, then the [numeric type](../../../../spec/latest/chapters/formats.html#formats-numericformat) of the
view’s `format` and the `Sampled` `Type` operand of the
`OpTypeImage` **must** match

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageWrite-08795) VUID-vkCmdDrawMultiIndexedEXT-OpImageWrite-08795

If a [VkImageView](VkImageView.html)
created with a format other than `VK_FORMAT_A8_UNORM`
is accessed using `OpImageWrite` as a result of this command, then
the `Type` of the `Texel` operand of that instruction **must** have
at least as many components as the image view’s format

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageWrite-08796) VUID-vkCmdDrawMultiIndexedEXT-OpImageWrite-08796

If a [VkImageView](VkImageView.html) created with the format `VK_FORMAT_A8_UNORM`
is accessed using `OpImageWrite` as a result of this command, then
the `Type` of the `Texel` operand of that instruction **must** have
four components

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageWrite-04469) VUID-vkCmdDrawMultiIndexedEXT-OpImageWrite-04469

If a [VkBufferView](VkBufferView.html) is accessed using `OpImageWrite` as a result
of this command, then the `Type` of the `Texel` operand of that
instruction **must** have at least as many components as the buffer view’s
format

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-SampledType-04470) VUID-vkCmdDrawMultiIndexedEXT-SampledType-04470

If a [VkImageView](VkImageView.html) with a [VkFormat](VkFormat.html) that has a 64-bit component
width is accessed as a result of this command, the `SampledType` of
the `OpTypeImage` operand of that instruction **must** have a `Width`
of 64

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-SampledType-04471) VUID-vkCmdDrawMultiIndexedEXT-SampledType-04471

If a [VkImageView](VkImageView.html) with a [VkFormat](VkFormat.html) that has a component width
less than 64-bit is accessed as a result of this command, the
`SampledType` of the `OpTypeImage` operand of that instruction
**must** have a `Width` of 32

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-SampledType-04472) VUID-vkCmdDrawMultiIndexedEXT-SampledType-04472

If a [VkBufferView](VkBufferView.html) with a [VkFormat](VkFormat.html) that has a 64-bit
component width is accessed as a result of this command, the
`SampledType` of the `OpTypeImage` operand of that instruction
**must** have a `Width` of 64

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-SampledType-04473) VUID-vkCmdDrawMultiIndexedEXT-SampledType-04473

If a [VkBufferView](VkBufferView.html) with a [VkFormat](VkFormat.html) that has a component width
less than 64-bit is accessed as a result of this command, the
`SampledType` of the `OpTypeImage` operand of that instruction
**must** have a `Width` of 32

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-sparseImageInt64Atomics-04474) VUID-vkCmdDrawMultiIndexedEXT-sparseImageInt64Atomics-04474

If the [    `sparseImageInt64Atomics`](../../../../spec/latest/chapters/features.html#features-sparseImageInt64Atomics) feature is not enabled, [VkImage](VkImage.html)
objects created with the `VK_IMAGE_CREATE_SPARSE_RESIDENCY_BIT` flag
**must** not be accessed by atomic instructions through an `OpTypeImage`
with a `SampledType` with a `Width` of 64 by this command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-sparseImageInt64Atomics-04475) VUID-vkCmdDrawMultiIndexedEXT-sparseImageInt64Atomics-04475

If the [    `sparseImageInt64Atomics`](../../../../spec/latest/chapters/features.html#features-sparseImageInt64Atomics) feature is not enabled, [VkBuffer](VkBuffer.html)
objects created with the `VK_BUFFER_CREATE_SPARSE_RESIDENCY_BIT`
flag **must** not be accessed by atomic instructions through an
`OpTypeImage` with a `SampledType` with a `Width` of 64 by this
command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageWeightedSampleQCOM-06971) VUID-vkCmdDrawMultiIndexedEXT-OpImageWeightedSampleQCOM-06971

If `OpImageWeightedSampleQCOM` is used to sample a [VkImageView](VkImageView.html)
as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_WEIGHT_SAMPLED_IMAGE_BIT_QCOM`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageWeightedSampleQCOM-06972) VUID-vkCmdDrawMultiIndexedEXT-OpImageWeightedSampleQCOM-06972

If `OpImageWeightedSampleQCOM` uses a [VkImageView](VkImageView.html) as a sample
weight image as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_WEIGHT_IMAGE_BIT_QCOM`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageBoxFilterQCOM-06973) VUID-vkCmdDrawMultiIndexedEXT-OpImageBoxFilterQCOM-06973

If `OpImageBoxFilterQCOM` is used to sample a [VkImageView](VkImageView.html) as a
result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BOX_FILTER_SAMPLED_BIT_QCOM`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchSSDQCOM-06974) VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchSSDQCOM-06974

If `OpImageBlockMatchSSDQCOM` is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BLOCK_MATCHING_BIT_QCOM`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchSADQCOM-06975) VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchSADQCOM-06975

If `OpImageBlockMatchSADQCOM` is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BLOCK_MATCHING_BIT_QCOM`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchSADQCOM-06976) VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchSADQCOM-06976

If `OpImageBlockMatchSADQCOM` or OpImageBlockMatchSSDQCOM is used to
read from a reference image as result of this command, then the
specified reference coordinates **must** not fail
[integer texel coordinate    validation](../../../../spec/latest/chapters/textures.html#textures-integer-coordinate-validation)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageWeightedSampleQCOM-06977) VUID-vkCmdDrawMultiIndexedEXT-OpImageWeightedSampleQCOM-06977

If `OpImageWeightedSampleQCOM`, `OpImageBoxFilterQCOM`,
`OpImageBlockMatchWindowSSDQCOM`,
`OpImageBlockMatchWindowSADQCOM`,
`OpImageBlockMatchGatherSSDQCOM`,
`OpImageBlockMatchGatherSADQCOM`,
`OpImageBlockMatchSSDQCOM`, or `OpImageBlockMatchSADQCOM` uses a
[VkSampler](VkSampler.html) as a result of this command, then the sampler **must** have
been created with `VK_SAMPLER_CREATE_IMAGE_PROCESSING_BIT_QCOM`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageWeightedSampleQCOM-06978) VUID-vkCmdDrawMultiIndexedEXT-OpImageWeightedSampleQCOM-06978

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
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchWindow-09215) VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchWindow-09215

If a `OpImageBlockMatchWindow*QCOM` or
`OpImageBlockMatchGather*QCOM` instruction is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BLOCK_MATCHING_BIT_QCOM`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchWindow-09216) VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchWindow-09216

If a `OpImageBlockMatchWindow*QCOM` or
`OpImageBlockMatchGather*QCOM` instruction is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
format **must** be a single-component format

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchWindow-09217) VUID-vkCmdDrawMultiIndexedEXT-OpImageBlockMatchWindow-09217

If a `OpImageBlockMatchWindow*QCOM` or
`OpImageBlockMatchGather*QCOM` read from a reference image as result
of this command, then the specified reference coordinates **must** not fail
[integer texel coordinate    validation](../../../../spec/latest/chapters/textures.html#textures-integer-coordinate-validation)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-07288) VUID-vkCmdDrawMultiIndexedEXT-None-07288

Any shader invocation executed by this command **must**
[terminate](../../../../spec/latest/chapters/shaders.html#shaders-termination)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-09600) VUID-vkCmdDrawMultiIndexedEXT-None-09600

If a descriptor with type equal to any of
`VK_DESCRIPTOR_TYPE_SAMPLE_WEIGHT_IMAGE_QCOM`,
`VK_DESCRIPTOR_TYPE_BLOCK_MATCH_IMAGE_QCOM`,
`VK_DESCRIPTOR_TYPE_SAMPLED_IMAGE`,
`VK_DESCRIPTOR_TYPE_STORAGE_IMAGE`, or
`VK_DESCRIPTOR_TYPE_INPUT_ATTACHMENT` is accessed as a result of
this command, all image subresources identified by that descriptor **must**
be in the image layout identified when the descriptor was written

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-10746) VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-10746

The `VkDeviceMemory` object allocated from a `VkMemoryHeap` with
the `VK_MEMORY_HEAP_TILE_MEMORY_BIT_QCOM` property that is bound to
a resource accessed as a result of this command **must** be the active
bound [bound tile memory object](../../../../spec/latest/chapters/memory.html#memory-bind-tile-memory) in
`commandBuffer`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-10678) VUID-vkCmdDrawMultiIndexedEXT-None-10678

If this command is recorded inside a [tile    shading render pass](../../../../spec/latest/chapters/renderpass.html#renderpass-tile-shading) instance, the stages corresponding to the pipeline
bind point used by this command **must** only include
`VK_SHADER_STAGE_VERTEX_BIT`, `VK_SHADER_STAGE_FRAGMENT_BIT`,
and/or `VK_SHADER_STAGE_COMPUTE_BIT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-10679) VUID-vkCmdDrawMultiIndexedEXT-None-10679

If this command is recorded where
[per-tile execution model](../../../../spec/latest/chapters/renderpass.html#renderpass-per-tile-execution-model) is
enabled, there **must** be no access to any image while the image was be
transitioned to the
`VK_IMAGE_LAYOUT_ATTACHMENT_FEEDBACK_LOOP_OPTIMAL_EXT` layout

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-pDescription-09900) VUID-vkCmdDrawMultiIndexedEXT-pDescription-09900

If a `VK_DESCRIPTOR_TYPE_TENSOR_ARM` descriptor is accessed as a
result of this command, then the underlying [VkTensorARM](VkTensorARM.html) object
**must** have been created with a
[VkTensorCreateInfoARM](VkTensorCreateInfoARM.html)::`pDescription` whose `usage` member
contained `VK_TENSOR_USAGE_SHADER_BIT_ARM`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-dimensionCount-09905) VUID-vkCmdDrawMultiIndexedEXT-dimensionCount-09905

If a `VK_DESCRIPTOR_TYPE_TENSOR_ARM` descriptor is accessed as a
result of this command, then the `Rank` of the `OpTypeTensorARM`
of the tensor resource variable **must** be equal to the
`dimensionCount` provided via
[VkTensorCreateInfoARM](VkTensorCreateInfoARM.html)::`pDescription` when creating the
underlying [VkTensorARM](VkTensorARM.html) object

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpTypeTensorARM-09906) VUID-vkCmdDrawMultiIndexedEXT-OpTypeTensorARM-09906

If a `VK_DESCRIPTOR_TYPE_TENSOR_ARM` descriptor is accessed as a
result of this command, then the element type of the
`OpTypeTensorARM` of the tensor resource variable **must** be
[compatible](../../../../spec/latest/appendices/spirvenv.html#spirvenv-tensor-formats) with the [VkFormat](VkFormat.html) of the
[VkTensorViewARM](VkTensorViewARM.html) used for the access

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-renderPass-02684) VUID-vkCmdDrawMultiIndexedEXT-renderPass-02684

The current render pass **must** be [compatible](../../../../spec/latest/chapters/renderpass.html#renderpass-compatibility)
with the `renderPass` member of the
`VkGraphicsPipelineCreateInfo` structure specified when creating the
`VkPipeline` bound to `VK_PIPELINE_BIND_POINT_GRAPHICS`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-subpass-02685) VUID-vkCmdDrawMultiIndexedEXT-subpass-02685

The subpass index of the current render pass **must** be equal to the
`subpass` member of the `VkGraphicsPipelineCreateInfo` structure
specified when creating the `VkPipeline` bound to
`VK_PIPELINE_BIND_POINT_GRAPHICS`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-07748) VUID-vkCmdDrawMultiIndexedEXT-None-07748

If any shader statically accesses an input attachment, a valid
descriptor **must** be bound to the pipeline via a descriptor set

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpTypeImage-07468) VUID-vkCmdDrawMultiIndexedEXT-OpTypeImage-07468

If any shader executed by this pipeline accesses an `OpTypeImage`
variable with a `Dim` operand of `SubpassData`, it **must** be
decorated with an `InputAttachmentIndex` that corresponds to a valid
input attachment in the current subpass

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-07469) VUID-vkCmdDrawMultiIndexedEXT-None-07469

Input attachment views accessed in a subpass **must** be created with the
same [VkFormat](VkFormat.html) as the corresponding subpass definition, and be
created with a [VkImageView](VkImageView.html) that is compatible with the attachment
referenced by the subpass'
`pInputAttachments`[`InputAttachmentIndex`] in the bound
[VkFramebuffer](VkFramebuffer.html) as specified by
[Fragment Input Attachment    Compatibility](../../../../spec/latest/chapters/interfaces.html#compatibility-inputattachment)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-pDepthInputAttachmentIndex-09595) VUID-vkCmdDrawMultiIndexedEXT-pDepthInputAttachmentIndex-09595

Input attachment views accessed in a dynamic render pass with a
`InputAttachmentIndex` referenced by
[VkRenderingInputAttachmentIndexInfo](VkRenderingInputAttachmentIndexInfo.html), or no
`InputAttachmentIndex` if
[VkRenderingInputAttachmentIndexInfo](VkRenderingInputAttachmentIndexInfo.html):`pDepthInputAttachmentIndex`
or
[VkRenderingInputAttachmentIndexInfo](VkRenderingInputAttachmentIndexInfo.html):`pStencilInputAttachmentIndex`
are `NULL`, **must** be created with a [VkImageView](VkImageView.html) that is compatible
with the corresponding color, depth, or stencil attachment in
[VkRenderingInfo](VkRenderingInfo.html)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-pDepthInputAttachmentIndex-09596) VUID-vkCmdDrawMultiIndexedEXT-pDepthInputAttachmentIndex-09596

Input attachment views accessed in a dynamic render pass via a shader
object **must** have an `InputAttachmentIndex` if both
[VkRenderingInputAttachmentIndexInfo](VkRenderingInputAttachmentIndexInfo.html):`pDepthInputAttachmentIndex`
and
[VkRenderingInputAttachmentIndexInfo](VkRenderingInputAttachmentIndexInfo.html):`pStencilInputAttachmentIndex`
are non-`NULL`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-InputAttachmentIndex-09597) VUID-vkCmdDrawMultiIndexedEXT-InputAttachmentIndex-09597

If an input attachment view accessed in a dynamic render pass via a
shader object has an `InputAttachmentIndex`, the
`InputAttachmentIndex` **must** match an index in
[VkRenderingInputAttachmentIndexInfo](VkRenderingInputAttachmentIndexInfo.html)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-06537) VUID-vkCmdDrawMultiIndexedEXT-None-06537

Memory backing image subresources used as attachments in the current
render pass **must** not be written in any way other than as an attachment
by this command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-10795) VUID-vkCmdDrawMultiIndexedEXT-None-10795

If a color attachment is written by any prior command in this subpass or
by the load, store, or resolve operations for this subpass,
[feedback loop](../../../../spec/latest/chapters/renderpass.html#renderpass-feedbackloop) is not enabled for it, and
either:

the `VK_PIPELINE_CREATE_COLOR_ATTACHMENT_FEEDBACK_LOOP_BIT_EXT` is
set on the bound pipeline
or

* 
the last call to [vkCmdSetAttachmentFeedbackLoopEnableEXT](vkCmdSetAttachmentFeedbackLoopEnableEXT.html) included
`VK_IMAGE_ASPECT_COLOR_BIT` and

there is no bound graphics pipeline or

* 
the bound graphics pipeline was created with
`VK_DYNAMIC_STATE_ATTACHMENT_FEEDBACK_LOOP_ENABLE_EXT`

it **must** not be accessed in any way other than as an attachment by this
command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-10796) VUID-vkCmdDrawMultiIndexedEXT-None-10796

If a depth attachment is written by any prior command in this subpass or
by the load, store, or resolve operations for this subpass,
[feedback loop](../../../../spec/latest/chapters/renderpass.html#renderpass-feedbackloop) is not enabled for it, and
either:

* 

the
`VK_PIPELINE_CREATE_DEPTH_STENCIL_ATTACHMENT_FEEDBACK_LOOP_BIT_EXT`
is set on the bound pipeline
or

* 
the last call to [vkCmdSetAttachmentFeedbackLoopEnableEXT](vkCmdSetAttachmentFeedbackLoopEnableEXT.html) included
`VK_IMAGE_ASPECT_DEPTH_BIT` and

there is no bound graphics pipeline or

* 
the bound graphics pipeline was created with
`VK_DYNAMIC_STATE_ATTACHMENT_FEEDBACK_LOOP_ENABLE_EXT`

it **must** not be accessed in any way other than as an attachment by this
command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-10797) VUID-vkCmdDrawMultiIndexedEXT-None-10797

If a stencil attachment is written by any prior command in this subpass
or by the load, store, or resolve operations for this subpass,
[feedback loop](../../../../spec/latest/chapters/renderpass.html#renderpass-feedbackloop) is not enabled for it, and
either:

* 

the
`VK_PIPELINE_CREATE_DEPTH_STENCIL_ATTACHMENT_FEEDBACK_LOOP_BIT_EXT`
is set on the bound pipeline
or

* 
the last call to [vkCmdSetAttachmentFeedbackLoopEnableEXT](vkCmdSetAttachmentFeedbackLoopEnableEXT.html) included
`VK_IMAGE_ASPECT_STENCIL_BIT` and

there is no bound graphics pipeline or

* 
the bound graphics pipeline was created with
`VK_DYNAMIC_STATE_ATTACHMENT_FEEDBACK_LOOP_ENABLE_EXT`

it **must** not be accessed in any way other than as an attachment by this
command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09003) VUID-vkCmdDrawMultiIndexedEXT-None-09003

If an attachment is written by any prior command in this subpass or by
the load, store, or resolve operations for this subpass, it **must** not be
accessed in any way other than as an attachment, storage image, or
sampled image by this command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-06539) VUID-vkCmdDrawMultiIndexedEXT-None-06539

If any previously recorded command in the current subpass accessed an
image subresource used as an attachment in this subpass in any way other
than as an attachment, this command **must** not write to that image
subresource as an attachment

[](#VUID-vkCmdDrawMultiIndexedEXT-None-06886) VUID-vkCmdDrawMultiIndexedEXT-None-06886

If the current render pass instance uses a depth/stencil attachment with
a read-only layout for the depth aspect, [depth    writes](../../../../spec/latest/chapters/fragops.html#fragops-depth-write) **must** be disabled

[](#VUID-vkCmdDrawMultiIndexedEXT-None-06887) VUID-vkCmdDrawMultiIndexedEXT-None-06887

If the current render pass instance uses a depth/stencil attachment with
a read-only layout for the stencil aspect, both front and back
`writeMask` are not zero, and stencil test is enabled,
[all stencil ops](../../../../spec/latest/chapters/fragops.html#fragops-stencil) **must** be `VK_STENCIL_OP_KEEP`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07831) VUID-vkCmdDrawMultiIndexedEXT-None-07831

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_VIEWPORT` dynamic state enabled then
[vkCmdSetViewport](vkCmdSetViewport.html) **must** have been called and not subsequently
[invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer
prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07832) VUID-vkCmdDrawMultiIndexedEXT-None-07832

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_SCISSOR` dynamic state enabled then
[vkCmdSetScissor](vkCmdSetScissor.html) **must** have been called and not subsequently
[invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer
prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08617) VUID-vkCmdDrawMultiIndexedEXT-None-08617

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_LINE_WIDTH` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[effective rasterization input    topology](../../../../spec/latest/chapters/drawing.html#drawing-rasterization-input-topology) is in line topology class, then [vkCmdSetLineWidth](vkCmdSetLineWidth.html) **must**
have been called and not subsequently [    invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer prior to this drawing
command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07834) VUID-vkCmdDrawMultiIndexedEXT-None-07834

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DEPTH_BIAS` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `depthBiasEnable`
is `VK_TRUE`, then [vkCmdSetDepthBias](vkCmdSetDepthBias.html)
or [vkCmdSetDepthBias2EXT](vkCmdSetDepthBias2EXT.html)
**must** have been called and not subsequently [    invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer prior to this drawing
command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07835) VUID-vkCmdDrawMultiIndexedEXT-None-07835

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_BLEND_CONSTANTS` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and an active color
attachment [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`blendEnable` is `VK_TRUE` with a blend equations where any
[VkBlendFactor](VkBlendFactor.html) member is `VK_BLEND_FACTOR_CONSTANT_COLOR`,
`VK_BLEND_FACTOR_ONE_MINUS_CONSTANT_COLOR`,
`VK_BLEND_FACTOR_CONSTANT_ALPHA`, or
`VK_BLEND_FACTOR_ONE_MINUS_CONSTANT_ALPHA`, then
[vkCmdSetBlendConstants](vkCmdSetBlendConstants.html) **must** have been called and not subsequently
[invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer
prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07836) VUID-vkCmdDrawMultiIndexedEXT-None-07836

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DEPTH_BOUNDS` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`depthBoundsTestEnable` is `VK_TRUE`, then
[vkCmdSetDepthBounds](vkCmdSetDepthBounds.html) **must** have been called and not subsequently
[invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer
prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07837) VUID-vkCmdDrawMultiIndexedEXT-None-07837

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_STENCIL_COMPARE_MASK` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`stencilTestEnable` is `VK_TRUE`, then
[vkCmdSetStencilCompareMask](vkCmdSetStencilCompareMask.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07838) VUID-vkCmdDrawMultiIndexedEXT-None-07838

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_STENCIL_WRITE_MASK` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`stencilTestEnable` is `VK_TRUE`, then
[vkCmdSetStencilWriteMask](vkCmdSetStencilWriteMask.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07839) VUID-vkCmdDrawMultiIndexedEXT-None-07839

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_STENCIL_REFERENCE` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of and
`rasterizerDiscardEnable` is `VK_FALSE`, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`stencilTestEnable` is `VK_TRUE`, then
[vkCmdSetStencilReference](vkCmdSetStencilReference.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-maxMultiviewInstanceIndex-02688) VUID-vkCmdDrawMultiIndexedEXT-maxMultiviewInstanceIndex-02688

If the draw is recorded in a render pass instance with multiview
enabled, the maximum instance index **must** be less than or equal to
[VkPhysicalDeviceMultiviewProperties](VkPhysicalDeviceMultiviewProperties.html)::`maxMultiviewInstanceIndex`

[](#VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-02689) VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-02689

If the bound graphics pipeline was created with
[VkPipelineSampleLocationsStateCreateInfoEXT](VkPipelineSampleLocationsStateCreateInfoEXT.html)::`sampleLocationsEnable`
set to `VK_TRUE`, then the active depth attachment **must** have been
created with the
`VK_IMAGE_CREATE_SAMPLE_LOCATIONS_COMPATIBLE_DEPTH_BIT_EXT` bit set

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07634) VUID-vkCmdDrawMultiIndexedEXT-None-07634

If the `[VK_EXT_sample_locations](VK_EXT_sample_locations.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_ENABLE_EXT` dynamic state
enabled, and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetSampleLocationsEnableEXT](vkCmdSetSampleLocationsEnableEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-06666) VUID-vkCmdDrawMultiIndexedEXT-None-06666

If the `[VK_EXT_sample_locations](VK_EXT_sample_locations.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_EXT` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`sampleLocationsEnable` is `VK_TRUE`, then
[vkCmdSetSampleLocationsEXT](vkCmdSetSampleLocationsEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07840) VUID-vkCmdDrawMultiIndexedEXT-None-07840

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_CULL_MODE` dynamic state enabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetCullMode](vkCmdSetCullMode.html) **must** have been called and not subsequently
[invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer
prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07841) VUID-vkCmdDrawMultiIndexedEXT-None-07841

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_FRONT_FACE` dynamic state enabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetFrontFace](vkCmdSetFrontFace.html) **must** have been called and not subsequently
[invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer
prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07843) VUID-vkCmdDrawMultiIndexedEXT-None-07843

 If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DEPTH_TEST_ENABLE` dynamic state enabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`,
[vkCmdSetDepthTestEnable](vkCmdSetDepthTestEnable.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07844) VUID-vkCmdDrawMultiIndexedEXT-None-07844

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DEPTH_WRITE_ENABLE` dynamic state enabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `depthTestEnable`
is `VK_TRUE`, then [vkCmdSetDepthWriteEnable](vkCmdSetDepthWriteEnable.html) **must** have been
called and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in
the current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07845) VUID-vkCmdDrawMultiIndexedEXT-None-07845

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DEPTH_COMPARE_OP` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `depthTestEnable`
is `VK_TRUE`, then [vkCmdSetDepthCompareOp](vkCmdSetDepthCompareOp.html) **must** have been
called and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in
the current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07846) VUID-vkCmdDrawMultiIndexedEXT-None-07846

If the [`depthBounds`](../../../../spec/latest/chapters/features.html#features-depthBounds) feature is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DEPTH_BOUNDS_TEST_ENABLE` dynamic state enabled,
and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetDepthBoundsTestEnable](vkCmdSetDepthBoundsTestEnable.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07847) VUID-vkCmdDrawMultiIndexedEXT-None-07847

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_STENCIL_TEST_ENABLE` dynamic state enabled, and
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetStencilTestEnable](vkCmdSetStencilTestEnable.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07848) VUID-vkCmdDrawMultiIndexedEXT-None-07848

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_STENCIL_OP` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`stencilTestEnable` is `VK_TRUE`, then [vkCmdSetStencilOp](vkCmdSetStencilOp.html)
**must** have been called and not subsequently [    invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer prior to this drawing
command

[](#VUID-vkCmdDrawMultiIndexedEXT-viewportCount-03417) VUID-vkCmdDrawMultiIndexedEXT-viewportCount-03417

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` dynamic state enabled,
and the state is not inherited,
then [vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-scissorCount-03418) VUID-vkCmdDrawMultiIndexedEXT-scissorCount-03418

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_SCISSOR_WITH_COUNT` dynamic state enabled,
and the state is not inherited,
then [vkCmdSetScissorWithCount](vkCmdSetScissorWithCount.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing

[](#VUID-vkCmdDrawMultiIndexedEXT-viewportCount-03419) VUID-vkCmdDrawMultiIndexedEXT-viewportCount-03419

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with both the
`VK_DYNAMIC_STATE_SCISSOR_WITH_COUNT` and
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` dynamic states enabled,
and the state is not inherited,
then the `viewportCount` parameter of
`vkCmdSetViewportWithCount` **must** match the `scissorCount`
parameter of `vkCmdSetScissorWithCount`

[](#VUID-vkCmdDrawMultiIndexedEXT-viewportCount-04137) VUID-vkCmdDrawMultiIndexedEXT-viewportCount-04137

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` dynamic state enabled, but
not the `VK_DYNAMIC_STATE_VIEWPORT_W_SCALING_NV` dynamic state
enabled, then the bound graphics pipeline **must** have been created with
[VkPipelineViewportWScalingStateCreateInfoNV](VkPipelineViewportWScalingStateCreateInfoNV.html)::`viewportCount`
greater or equal to the `viewportCount` parameter in the last call
to [vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-viewportCount-04138) VUID-vkCmdDrawMultiIndexedEXT-viewportCount-04138

If the `[VK_NV_clip_space_w_scaling](VK_NV_clip_space_w_scaling.html)` extension is enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` and
`VK_DYNAMIC_STATE_VIEWPORT_W_SCALING_NV` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`viewportWScalingEnable` is `VK_TRUE`, then
[vkCmdSetViewportWScalingNV](vkCmdSetViewportWScalingNV.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08636) VUID-vkCmdDrawMultiIndexedEXT-None-08636

If the `[VK_NV_clip_space_w_scaling](VK_NV_clip_space_w_scaling.html)` extension is enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` and
`VK_DYNAMIC_STATE_VIEWPORT_W_SCALING_NV` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`viewportWScalingEnable` is `VK_TRUE`, then the
`viewportCount` parameter in the last call to
[vkCmdSetViewportWScalingNV](vkCmdSetViewportWScalingNV.html) **must** be greater than or equal to the
`viewportCount` parameter in the last call to
[vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-viewportCount-04139) VUID-vkCmdDrawMultiIndexedEXT-viewportCount-04139

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` dynamic state enabled, but
not the `VK_DYNAMIC_STATE_VIEWPORT_SHADING_RATE_PALETTE_NV` dynamic
state enabled, then the bound graphics pipeline **must** have been created
with
[VkPipelineViewportShadingRateImageStateCreateInfoNV](VkPipelineViewportShadingRateImageStateCreateInfoNV.html)::`viewportCount`
greater or equal to the `viewportCount` parameter in the last call
to [vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-shadingRateImage-09233) VUID-vkCmdDrawMultiIndexedEXT-shadingRateImage-09233

If the [`shadingRateImage`](../../../../spec/latest/chapters/features.html#features-shadingRateImage) feature is
enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_VIEWPORT_COARSE_SAMPLE_ORDER_NV` and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetCoarseSampleOrderNV](vkCmdSetCoarseSampleOrderNV.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-shadingRateImage-09234) VUID-vkCmdDrawMultiIndexedEXT-shadingRateImage-09234

If the [`shadingRateImage`](../../../../spec/latest/chapters/features.html#features-shadingRateImage) feature is
enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` and
`VK_DYNAMIC_STATE_VIEWPORT_SHADING_RATE_PALETTE_NV` dynamic state
enabled, the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`shadingRateImageEnable` is `VK_TRUE`, then
[vkCmdSetViewportShadingRatePaletteNV](vkCmdSetViewportShadingRatePaletteNV.html) **must** have been called and
not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08637) VUID-vkCmdDrawMultiIndexedEXT-None-08637

If the [`shadingRateImage`](../../../../spec/latest/chapters/features.html#features-shadingRateImage) feature is
enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` and
`VK_DYNAMIC_STATE_VIEWPORT_SHADING_RATE_PALETTE_NV` dynamic state
enabled, the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`shadingRateImageEnable` is `VK_TRUE`, then the
`viewportCount` parameter in the last call to
[vkCmdSetViewportShadingRatePaletteNV](vkCmdSetViewportShadingRatePaletteNV.html) **must** be greater than or
equal to the `viewportCount` parameter in the last call to
[vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-VkPipelineVieportCreateInfo-04141) VUID-vkCmdDrawMultiIndexedEXT-VkPipelineVieportCreateInfo-04141

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` dynamic state enabled and a
[VkPipelineViewportSwizzleStateCreateInfoNV](VkPipelineViewportSwizzleStateCreateInfoNV.html) structure chained from
[VkPipelineViewportStateCreateInfo](VkPipelineViewportStateCreateInfo.html), then the bound graphics
pipeline **must** have been created with
[VkPipelineViewportSwizzleStateCreateInfoNV](VkPipelineViewportSwizzleStateCreateInfoNV.html)::`viewportCount`
greater or equal to the `viewportCount` parameter in the last call
to [vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-VkPipelineVieportCreateInfo-04142) VUID-vkCmdDrawMultiIndexedEXT-VkPipelineVieportCreateInfo-04142

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` dynamic state enabled and a
[VkPipelineViewportExclusiveScissorStateCreateInfoNV](VkPipelineViewportExclusiveScissorStateCreateInfoNV.html) structure
chained from [VkPipelineViewportStateCreateInfo](VkPipelineViewportStateCreateInfo.html), then the bound
graphics pipeline **must** have been created with
[VkPipelineViewportExclusiveScissorStateCreateInfoNV](VkPipelineViewportExclusiveScissorStateCreateInfoNV.html)::`exclusiveScissorCount`
greater or equal to the `viewportCount` parameter in the last call
to [vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07878) VUID-vkCmdDrawMultiIndexedEXT-None-07878

If the [`exclusiveScissor`](../../../../spec/latest/chapters/features.html#features-exclusiveScissor) feature is
enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_EXCLUSIVE_SCISSOR_ENABLE_NV` dynamic state
enabled, then [vkCmdSetExclusiveScissorEnableNV](vkCmdSetExclusiveScissorEnableNV.html) **must** have been
called and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in
the current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07879) VUID-vkCmdDrawMultiIndexedEXT-None-07879

If the [`exclusiveScissor`](../../../../spec/latest/chapters/features.html#features-exclusiveScissor) feature is
enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_EXCLUSIVE_SCISSOR_NV` dynamic state enabled, and
the most recent call to [vkCmdSetExclusiveScissorEnableNV](vkCmdSetExclusiveScissorEnableNV.html) in the
current command buffer set any element of `pExclusiveScissorEnables`
to `VK_TRUE`, then [vkCmdSetExclusiveScissorNV](vkCmdSetExclusiveScissorNV.html) **must** have been
called and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in
the current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-04876) VUID-vkCmdDrawMultiIndexedEXT-None-04876

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_RASTERIZER_DISCARD_ENABLE` dynamic state enabled,
then [vkCmdSetRasterizerDiscardEnable](vkCmdSetRasterizerDiscardEnable.html) **must** have been called and
not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-04877) VUID-vkCmdDrawMultiIndexedEXT-None-04877

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DEPTH_BIAS_ENABLE` dynamic state enabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetDepthBiasEnable](vkCmdSetDepthBiasEnable.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-logicOp-04878) VUID-vkCmdDrawMultiIndexedEXT-logicOp-04878

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_LOGIC_OP_EXT` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `logicOpEnable` is
`VK_TRUE`, then [vkCmdSetLogicOpEXT](vkCmdSetLogicOpEXT.html) **must** have been called and
not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-primitiveFragmentShadingRateWithMultipleViewports-04552) VUID-vkCmdDrawMultiIndexedEXT-primitiveFragmentShadingRateWithMultipleViewports-04552

If the [    `primitiveFragmentShadingRateWithMultipleViewports`](../../../../spec/latest/chapters/limits.html#limits-primitiveFragmentShadingRateWithMultipleViewports) limit is not
supported, the bound graphics pipeline was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` dynamic state enabled, and
any of the shader stages of the bound graphics pipeline write to the
`PrimitiveShadingRateKHR` built-in, then
[vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html) **must** have been called in the current
command buffer prior to this drawing command, and the
`viewportCount` parameter of `vkCmdSetViewportWithCount` **must**
be `1`

[](#VUID-vkCmdDrawMultiIndexedEXT-primitiveFragmentShadingRateWithMultipleViewports-08642) VUID-vkCmdDrawMultiIndexedEXT-primitiveFragmentShadingRateWithMultipleViewports-08642

If the [    `primitiveFragmentShadingRateWithMultipleViewports`](../../../../spec/latest/chapters/limits.html#limits-primitiveFragmentShadingRateWithMultipleViewports) limit is not
supported, and any shader object bound to a graphics stage writes to the
`PrimitiveShadingRateKHR` built-in, then
[vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html) **must** have been called in the current
command buffer prior to this drawing command, and the
`viewportCount` parameter of `vkCmdSetViewportWithCount` **must**
be `1`

[](#VUID-vkCmdDrawMultiIndexedEXT-blendEnable-04727) VUID-vkCmdDrawMultiIndexedEXT-blendEnable-04727

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound which was created with
`VK_DYNAMIC_STATE_COLOR_BLEND_ENABLE_EXT` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then for each color
attachment, if the corresponding image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) do not contain
`VK_FORMAT_FEATURE_COLOR_ATTACHMENT_BLEND_BIT`, then the
corresponding [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`blendEnable` **must** be `VK_FALSE`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08644) VUID-vkCmdDrawMultiIndexedEXT-None-08644

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound, the [current    value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `rasterizerDiscardEnable` is `VK_FALSE`,
and none of the following is enabled:

* 
the `[VK_AMD_mixed_attachment_samples](VK_AMD_mixed_attachment_samples.html)` extension

* 
the `[VK_NV_framebuffer_mixed_samples](VK_NV_framebuffer_mixed_samples.html)` extension

* 
the [     `multisampledRenderToSingleSampled`](../../../../spec/latest/chapters/features.html#features-multisampledRenderToSingleSampled) feature

then the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizationSamples` **must** be the same as the current color and/or
depth/stencil attachments

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08876) VUID-vkCmdDrawMultiIndexedEXT-None-08876

If a shader object is bound to any graphics stage, the current render
pass instance **must** have been begun with [vkCmdBeginRendering](vkCmdBeginRendering.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-imageView-06172) VUID-vkCmdDrawMultiIndexedEXT-imageView-06172

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the `imageView` member of
`pDepthAttachment` is not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), and the `layout`
member of `pDepthAttachment` is
`VK_IMAGE_LAYOUT_DEPTH_STENCIL_READ_ONLY_OPTIMAL`, this command
**must** not write any values to the depth attachment

[](#VUID-vkCmdDrawMultiIndexedEXT-imageView-06173) VUID-vkCmdDrawMultiIndexedEXT-imageView-06173

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the `imageView` member of
`pStencilAttachment` is not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), and the
`layout` member of `pStencilAttachment` is
`VK_IMAGE_LAYOUT_DEPTH_STENCIL_READ_ONLY_OPTIMAL`, this command
**must** not write any values to the stencil attachment

[](#VUID-vkCmdDrawMultiIndexedEXT-imageView-06174) VUID-vkCmdDrawMultiIndexedEXT-imageView-06174

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the `imageView` member of
`pDepthAttachment` is not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), and the `layout`
member of `pDepthAttachment` is
`VK_IMAGE_LAYOUT_DEPTH_READ_ONLY_STENCIL_ATTACHMENT_OPTIMAL`, this
command **must** not write any values to the depth attachment

[](#VUID-vkCmdDrawMultiIndexedEXT-imageView-06175) VUID-vkCmdDrawMultiIndexedEXT-imageView-06175

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the `imageView` member of
`pStencilAttachment` is not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), and the
`layout` member of `pStencilAttachment` is
`VK_IMAGE_LAYOUT_DEPTH_ATTACHMENT_STENCIL_READ_ONLY_OPTIMAL`, this
command **must** not write any values to the stencil attachment

[](#VUID-vkCmdDrawMultiIndexedEXT-imageView-06176) VUID-vkCmdDrawMultiIndexedEXT-imageView-06176

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the `imageView` member of
`pDepthAttachment` is not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), and the `layout`
member of `pDepthAttachment` is
`VK_IMAGE_LAYOUT_DEPTH_READ_ONLY_OPTIMAL`, this command **must** not
write any values to the depth attachment

[](#VUID-vkCmdDrawMultiIndexedEXT-imageView-06177) VUID-vkCmdDrawMultiIndexedEXT-imageView-06177

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the `imageView` member of
`pStencilAttachment` is not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), and the
`layout` member of `pStencilAttachment` is
`VK_IMAGE_LAYOUT_STENCIL_READ_ONLY_OPTIMAL`, this command **must** not
write any values to the stencil attachment

[](#VUID-vkCmdDrawMultiIndexedEXT-viewMask-06178) VUID-vkCmdDrawMultiIndexedEXT-viewMask-06178

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the bound graphics pipeline **must** have been
created with a [VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`viewMask` equal
to [VkRenderingInfo](VkRenderingInfo.html)::`viewMask`

[](#VUID-vkCmdDrawMultiIndexedEXT-colorAttachmentCount-06179) VUID-vkCmdDrawMultiIndexedEXT-colorAttachmentCount-06179

If
the [    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is not enabled and
the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the bound graphics pipeline **must** have been
created with a
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`colorAttachmentCount` equal to
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount`

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08910) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08910

If
the [    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is not enabled, and
the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html) and
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` greater than `0`, then
each element of the [VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments` array
with an `imageView` not equal to [VK_NULL_HANDLE](VK_NULL_HANDLE.html) **must** have
been created with a [VkFormat](VkFormat.html) equal to the corresponding element of
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`pColorAttachmentFormats` used
to create the bound graphics pipeline

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08912) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08912

If
the [    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is not enabled, and
the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html) and
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` greater than `0`, then
each element of the [VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments` array
with an `imageView` equal to [VK_NULL_HANDLE](VK_NULL_HANDLE.html) **must** have the
corresponding element of
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`pColorAttachmentFormats` used
to create the bound pipeline equal to `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08911) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08911

If the [    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is enabled, and the
current render pass instance was begun with [vkCmdBeginRendering](vkCmdBeginRendering.html)
and [VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` greater than `0`,
then each element of the [VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments`
array with an `imageView` not equal to [VK_NULL_HANDLE](VK_NULL_HANDLE.html) **must**
have been created with a [VkFormat](VkFormat.html) equal to the corresponding
element of
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`pColorAttachmentFormats` used
to create the bound graphics pipeline, or the corresponding element of
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`pColorAttachmentFormats`, if
it exists, **must** be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-colorAttachmentCount-09362) VUID-vkCmdDrawMultiIndexedEXT-colorAttachmentCount-09362

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), with a
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` equal to `1`,
there is no shader object bound to any graphics stage,
and a color attachment with a resolve mode of
`VK_RESOLVE_MODE_EXTERNAL_FORMAT_DOWNSAMPLE_BIT_ANDROID`, each
element of the [VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments` array with
a `resolveImageView` not equal to [VK_NULL_HANDLE](VK_NULL_HANDLE.html) **must** have
been created with an image created with a
[VkExternalFormatANDROID](VkExternalFormatANDROID.html)::`externalFormat` value equal to the
[VkExternalFormatANDROID](VkExternalFormatANDROID.html)::`externalFormat` value used to create
the bound graphics pipeline

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09363) VUID-vkCmdDrawMultiIndexedEXT-None-09363

If
there is no shader object bound to any graphics stage,
the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html) and a
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` equal to `1`, and a
color attachment with a resolve mode of
`VK_RESOLVE_MODE_EXTERNAL_FORMAT_DOWNSAMPLE_BIT_ANDROID`, each
element of the [VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments` array with
a `imageView` not equal to [VK_NULL_HANDLE](VK_NULL_HANDLE.html) **must** have been
created with an image created with a
[VkExternalFormatANDROID](VkExternalFormatANDROID.html)::`externalFormat` value equal to the
[VkExternalFormatANDROID](VkExternalFormatANDROID.html)::`externalFormat` value used to create
the bound graphics pipeline

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09364) VUID-vkCmdDrawMultiIndexedEXT-None-09364

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html),
there is no shader object bound to any graphics stage,
and the bound graphics pipeline was created with a non-zero
[VkExternalFormatANDROID](VkExternalFormatANDROID.html)::`externalFormat` value and with the
`VK_DYNAMIC_STATE_COLOR_BLEND_ENABLE_EXT` dynamic state enabled,
then [vkCmdSetColorBlendEnableEXT](vkCmdSetColorBlendEnableEXT.html) **must** have set the blend enable
to `VK_FALSE` prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09365) VUID-vkCmdDrawMultiIndexedEXT-None-09365

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html),
there is no shader object bound to any graphics stage,
and the bound graphics pipeline was created with a non-zero
[VkExternalFormatANDROID](VkExternalFormatANDROID.html)::`externalFormat` value and with the
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` dynamic state enabled,
then [vkCmdSetRasterizationSamplesEXT](vkCmdSetRasterizationSamplesEXT.html) **must** have set
`rasterizationSamples` to `VK_SAMPLE_COUNT_1_BIT` prior to this
drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09366) VUID-vkCmdDrawMultiIndexedEXT-None-09366

If there is a shader object bound to any graphics stage, and the current
render pass includes a color attachment that uses the
`VK_RESOLVE_MODE_EXTERNAL_FORMAT_DOWNSAMPLE_BIT_ANDROID` resolve
mode, then [vkCmdSetColorBlendEnableEXT](vkCmdSetColorBlendEnableEXT.html) **must** have set blend enable
to `VK_FALSE` prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-rasterizationSamples-09367) VUID-vkCmdDrawMultiIndexedEXT-rasterizationSamples-09367

If there is a shader object bound to any graphics stage, and the current
render pass includes a color attachment that uses the
`VK_RESOLVE_MODE_EXTERNAL_FORMAT_DOWNSAMPLE_BIT_ANDROID` resolve
mode, then [vkCmdSetRasterizationSamplesEXT](vkCmdSetRasterizationSamplesEXT.html) **must** have set
`rasterizationSamples` to `VK_SAMPLE_COUNT_1_BIT` prior to this
drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09368) VUID-vkCmdDrawMultiIndexedEXT-None-09368

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html),
there is no shader object bound to any graphics stage,
and the bound graphics pipeline was created with a non-zero
[VkExternalFormatANDROID](VkExternalFormatANDROID.html)::`externalFormat` value and with the
`VK_DYNAMIC_STATE_FRAGMENT_SHADING_RATE_KHR` dynamic state enabled,
then [vkCmdSetFragmentShadingRateKHR](vkCmdSetFragmentShadingRateKHR.html) **must** have set
`pFragmentSize->width` to `1` prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09369) VUID-vkCmdDrawMultiIndexedEXT-None-09369

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html),
there is no shader object bound to any graphics stage,
and the bound graphics pipeline was created with a non-zero
[VkExternalFormatANDROID](VkExternalFormatANDROID.html)::`externalFormat` value and with the
`VK_DYNAMIC_STATE_FRAGMENT_SHADING_RATE_KHR` dynamic state enabled,
then [vkCmdSetFragmentShadingRateKHR](vkCmdSetFragmentShadingRateKHR.html) **must** have set
`pFragmentSize->height` to `1` prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-pFragmentSize-09370) VUID-vkCmdDrawMultiIndexedEXT-pFragmentSize-09370

If there is a shader object bound to any graphics stage, and the current
render pass includes a color attachment that uses the
`VK_RESOLVE_MODE_EXTERNAL_FORMAT_DOWNSAMPLE_BIT_ANDROID` resolve
mode, then [vkCmdSetFragmentShadingRateKHR](vkCmdSetFragmentShadingRateKHR.html) **must** have set
`pFragmentSize->width` to `1` prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-pFragmentSize-09371) VUID-vkCmdDrawMultiIndexedEXT-pFragmentSize-09371

If there is a shader object bound to any graphics stage, and the current
render pass includes a color attachment that uses the
`VK_RESOLVE_MODE_EXTERNAL_FORMAT_DOWNSAMPLE_BIT_ANDROID` resolve
mode, then [vkCmdSetFragmentShadingRateKHR](vkCmdSetFragmentShadingRateKHR.html) **must** have set
`pFragmentSize->height` to `1` prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07749) VUID-vkCmdDrawMultiIndexedEXT-None-07749

If the [`colorWriteEnable`](../../../../spec/latest/chapters/features.html#features-colorWriteEnable) feature is
enabled,
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_COLOR_WRITE_ENABLE_EXT` dynamic state enabled, and
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetColorWriteEnableEXT](vkCmdSetColorWriteEnableEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-attachmentCount-07750) VUID-vkCmdDrawMultiIndexedEXT-attachmentCount-07750

If the [`colorWriteEnable`](../../../../spec/latest/chapters/features.html#features-colorWriteEnable) feature is
enabled,
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_COLOR_WRITE_ENABLE_EXT` dynamic state enabled, and
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then the
`attachmentCount` parameter of most recent call to
`vkCmdSetColorWriteEnableEXT` in the current command buffer **must** be
greater than or equal to the number of active color attachments

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07751) VUID-vkCmdDrawMultiIndexedEXT-None-07751

If the `[VK_EXT_discard_rectangles](VK_EXT_discard_rectangles.html)` extension is enabled, a
graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DISCARD_RECTANGLE_EXT` dynamic state enabled and
the `pNext` chain of [VkGraphicsPipelineCreateInfo](VkGraphicsPipelineCreateInfo.html) included a
[VkPipelineDiscardRectangleStateCreateInfoEXT](VkPipelineDiscardRectangleStateCreateInfoEXT.html) structure, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`discardRectangleEnable` is `VK_TRUE`, then
[vkCmdSetDiscardRectangleEXT](vkCmdSetDiscardRectangleEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command for each discard rectangle
in
[VkPipelineDiscardRectangleStateCreateInfoEXT](VkPipelineDiscardRectangleStateCreateInfoEXT.html)::`discardRectangleCount`

[](#VUID-vkCmdDrawMultiIndexedEXT-rasterizerDiscardEnable-09236) VUID-vkCmdDrawMultiIndexedEXT-rasterizerDiscardEnable-09236

If the `[VK_EXT_discard_rectangles](VK_EXT_discard_rectangles.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with
`VK_DYNAMIC_STATE_DISCARD_RECTANGLE_EXT` dynamic state enabled and
the `pNext` chain of [VkGraphicsPipelineCreateInfo](VkGraphicsPipelineCreateInfo.html) did not
include a [VkPipelineDiscardRectangleStateCreateInfoEXT](VkPipelineDiscardRectangleStateCreateInfoEXT.html) structure,
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`discardRectangleEnable` is `VK_TRUE`, then
[vkCmdSetDiscardRectangleEXT](vkCmdSetDiscardRectangleEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command for each discard rectangle
in
[VkPhysicalDeviceDiscardRectanglePropertiesEXT](VkPhysicalDeviceDiscardRectanglePropertiesEXT.html)::`maxDiscardRectangles`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07880) VUID-vkCmdDrawMultiIndexedEXT-None-07880

If the `[VK_EXT_discard_rectangles](VK_EXT_discard_rectangles.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DISCARD_RECTANGLE_ENABLE_EXT` dynamic state
enabled, the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetDiscardRectangleEnableEXT](vkCmdSetDiscardRectangleEnableEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07881) VUID-vkCmdDrawMultiIndexedEXT-None-07881

If the `[VK_EXT_discard_rectangles](VK_EXT_discard_rectangles.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DISCARD_RECTANGLE_MODE_EXT` dynamic state enabled,
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`discardRectangleEnable` is `VK_TRUE`, then
[vkCmdSetDiscardRectangleModeEXT](vkCmdSetDiscardRectangleModeEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08913) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08913

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html),
the
[`dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments)
feature is not enabled,
and [VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->imageView` was
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`depthAttachmentFormat` used to
create the bound graphics pipeline **must** be equal to
`VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08914) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08914

If current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html),
the
[`dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments)
feature is not enabled,
and [VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->imageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`depthAttachmentFormat` used to
create the bound graphics pipeline **must** be equal to the [VkFormat](VkFormat.html)
used to create [VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->imageView`

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08915) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08915

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the
[    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is enabled,
[VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->imageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), and the value of
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`depthAttachmentFormat` used to
create the bound graphics pipeline was not equal to the [VkFormat](VkFormat.html)
used to create [VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->imageView`,
the value of the format **must** be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08916) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08916

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html),
the
[`dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments)
feature is not enabled,
and [VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->imageView` was
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`stencilAttachmentFormat` used
to create the bound graphics pipeline **must** be equal to
`VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08917) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08917

If current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html),
the
[`dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments)
feature is not enabled,
and [VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->imageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`stencilAttachmentFormat` used
to create the bound graphics pipeline **must** be equal to the
[VkFormat](VkFormat.html) used to create
[VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->imageView`

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08918) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-08918

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the
[    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is enabled,
[VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->imageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), and the value of
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`stencilAttachmentFormat` used
to create the bound graphics pipeline was not equal to the
[VkFormat](VkFormat.html) used to create
[VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->imageView`, the value of
the format **must** be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-imageView-06183) VUID-vkCmdDrawMultiIndexedEXT-imageView-06183

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html) and
[VkRenderingFragmentShadingRateAttachmentInfoKHR](VkRenderingFragmentShadingRateAttachmentInfoKHR.html)::`imageView`
was not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), the bound graphics pipeline **must** have
been created with
`VK_PIPELINE_CREATE_RENDERING_FRAGMENT_SHADING_RATE_ATTACHMENT_BIT_KHR`

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingLocalRead-11797) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingLocalRead-11797

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the
[`dynamicRenderingLocalRead`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingLocalRead)
feature is enabled, the
`VK_RENDERING_LOCAL_READ_CONCURRENT_ACCESS_CONTROL_BIT_KHR` flag is
specified, and an attachment is being used as a feedback loop as
specified by
[`VK_RENDERING_ATTACHMENT_INPUT_ATTACHMENT_FEEDBACK_BIT_KHR`](../../../../spec/latest/chapters/renderpass.html#rendering-attachment-input-attachment-feedback),
[VkRenderingAttachmentFlagsInfoKHR](VkRenderingAttachmentFlagsInfoKHR.html)::`flags` for that attachment
**must** include
`VK_RENDERING_ATTACHMENT_INPUT_ATTACHMENT_FEEDBACK_BIT_KHR`

[](#VUID-vkCmdDrawMultiIndexedEXT-imageView-06184) VUID-vkCmdDrawMultiIndexedEXT-imageView-06184

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html) and
[VkRenderingFragmentDensityMapAttachmentInfoEXT](VkRenderingFragmentDensityMapAttachmentInfoEXT.html)::`imageView`
was not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), the bound graphics pipeline **must** have
been created with
`VK_PIPELINE_CREATE_RENDERING_FRAGMENT_DENSITY_MAP_ATTACHMENT_BIT_EXT`

[](#VUID-vkCmdDrawMultiIndexedEXT-layers-10831) VUID-vkCmdDrawMultiIndexedEXT-layers-10831

If the current render pass instance was created with
`VK_RENDERING_PER_LAYER_FRAGMENT_DENSITY_BIT_VALVE` or
`VK_RENDER_PASS_CREATE_PER_LAYER_FRAGMENT_DENSITY_BIT_VALVE`, and
the bound graphics pipeline was created with
`VK_PIPELINE_CREATE_2_PER_LAYER_FRAGMENT_DENSITY_BIT_VALVE`, then
the current render pass instance **must** have a `layers` value less
than or equal to
[VkPipelineFragmentDensityMapLayeredCreateInfoVALVE](VkPipelineFragmentDensityMapLayeredCreateInfoVALVE.html)::`maxFragmentDensityMapLayers`

[](#VUID-vkCmdDrawMultiIndexedEXT-colorAttachmentCount-06185) VUID-vkCmdDrawMultiIndexedEXT-colorAttachmentCount-06185

If the bound pipeline was created with a
[VkAttachmentSampleCountInfoAMD](VkAttachmentSampleCountInfoAMD.html) or
[VkAttachmentSampleCountInfoNV](VkAttachmentSampleCountInfoAMD.html) structure, and the current render
pass instance was begun with [vkCmdBeginRendering](vkCmdBeginRendering.html) with a
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` parameter greater than
`0`, then each element of the
[VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments` array with a
`imageView` not equal to [VK_NULL_HANDLE](VK_NULL_HANDLE.html) **must** have been
created with a sample count equal to the corresponding element of the
`pColorAttachmentSamples` member of
[VkAttachmentSampleCountInfoAMD](VkAttachmentSampleCountInfoAMD.html) or
[VkAttachmentSampleCountInfoNV](VkAttachmentSampleCountInfoAMD.html) used to create the bound graphics
pipeline

[](#VUID-vkCmdDrawMultiIndexedEXT-pDepthAttachment-06186) VUID-vkCmdDrawMultiIndexedEXT-pDepthAttachment-06186

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the bound pipeline was created with a
[VkAttachmentSampleCountInfoAMD](VkAttachmentSampleCountInfoAMD.html) or
[VkAttachmentSampleCountInfoNV](VkAttachmentSampleCountInfoAMD.html) structure, and
[VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->imageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of the
`depthStencilAttachmentSamples` member of
[VkAttachmentSampleCountInfoAMD](VkAttachmentSampleCountInfoAMD.html) or
[VkAttachmentSampleCountInfoNV](VkAttachmentSampleCountInfoAMD.html) used to create the bound graphics
pipeline **must** be equal to the sample count used to create
[VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->imageView`

[](#VUID-vkCmdDrawMultiIndexedEXT-pStencilAttachment-06187) VUID-vkCmdDrawMultiIndexedEXT-pStencilAttachment-06187

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the bound pipeline was created with a
[VkAttachmentSampleCountInfoAMD](VkAttachmentSampleCountInfoAMD.html) or
[VkAttachmentSampleCountInfoNV](VkAttachmentSampleCountInfoAMD.html) structure, and
[VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->imageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of the
`depthStencilAttachmentSamples` member of
[VkAttachmentSampleCountInfoAMD](VkAttachmentSampleCountInfoAMD.html) or
[VkAttachmentSampleCountInfoNV](VkAttachmentSampleCountInfoAMD.html) used to create the bound graphics
pipeline **must** be equal to the sample count used to create
[VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->imageView`

[](#VUID-vkCmdDrawMultiIndexedEXT-multisampledRenderToSingleSampled-07285) VUID-vkCmdDrawMultiIndexedEXT-multisampledRenderToSingleSampled-07285

    If
    the bound pipeline was created without a
    [VkAttachmentSampleCountInfoAMD](VkAttachmentSampleCountInfoAMD.html)
or
    [VkAttachmentSampleCountInfoNV](VkAttachmentSampleCountInfoAMD.html)
    structure, and
    the [    `multisampledRenderToSingleSampled`](../../../../spec/latest/chapters/features.html#features-multisampledRenderToSingleSampled) feature is not enabled, and
[vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has not yet been recorded in the render pass instance, and
    the current render pass instance was begun with
    [vkCmdBeginRendering](vkCmdBeginRendering.html) with a
    [VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` parameter greater than
    `0`, then each element of the
    [VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments` array with a
    `imageView` not equal to [VK_NULL_HANDLE](VK_NULL_HANDLE.html) **must** have been
    created with a sample count equal to the value of
    `rasterizationSamples` for the bound graphics pipeline

[](#VUID-vkCmdDrawMultiIndexedEXT-multisampledRenderToSingleSampled-07286) VUID-vkCmdDrawMultiIndexedEXT-multisampledRenderToSingleSampled-07286

    If
    the bound pipeline was created without a
    [VkAttachmentSampleCountInfoAMD](VkAttachmentSampleCountInfoAMD.html)
or
    [VkAttachmentSampleCountInfoNV](VkAttachmentSampleCountInfoAMD.html)
    structure, and
    the [    `multisampledRenderToSingleSampled`](../../../../spec/latest/chapters/features.html#features-multisampledRenderToSingleSampled) feature is not enabled, and
[vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has not yet been recorded in the render pass instance, and
    [VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->imageView` was not
    [VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of `rasterizationSamples` for the
    bound graphics pipeline **must** be equal to the sample count used to
    create [VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->imageView`

[](#VUID-vkCmdDrawMultiIndexedEXT-multisampledRenderToSingleSampled-07287) VUID-vkCmdDrawMultiIndexedEXT-multisampledRenderToSingleSampled-07287

    If
    the bound pipeline was created without a
    [VkAttachmentSampleCountInfoAMD](VkAttachmentSampleCountInfoAMD.html)
or
    [VkAttachmentSampleCountInfoNV](VkAttachmentSampleCountInfoAMD.html)
    structure, and
    the [    `multisampledRenderToSingleSampled`](../../../../spec/latest/chapters/features.html#features-multisampledRenderToSingleSampled) feature is not enabled, and
[vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has not yet been recorded in the render pass instance, and
    [VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->imageView` was not
    [VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of `rasterizationSamples` for the
    bound graphics pipeline **must** be equal to the sample count used to
    create [VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->imageView`

[](#VUID-vkCmdDrawMultiIndexedEXT-pNext-07935) VUID-vkCmdDrawMultiIndexedEXT-pNext-07935

If this command is called inside a render pass instance started with
[vkCmdBeginRendering](vkCmdBeginRendering.html), and the `pNext` chain of
[VkRenderingInfo](VkRenderingInfo.html) includes a
[VkMultisampledRenderToSingleSampledInfoEXT](VkMultisampledRenderToSingleSampledInfoEXT.html) structure with
`multisampledRenderToSingleSampledEnable` equal to `VK_TRUE`,
then the value of `rasterizationSamples` for the bound graphics
pipeline **must** be equal to
[VkMultisampledRenderToSingleSampledInfoEXT](VkMultisampledRenderToSingleSampledInfoEXT.html)::`rasterizationSamples`

[](#VUID-vkCmdDrawMultiIndexedEXT-renderPass-06198) VUID-vkCmdDrawMultiIndexedEXT-renderPass-06198

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), the bound pipeline **must** have been created
with a [VkGraphicsPipelineCreateInfo](VkGraphicsPipelineCreateInfo.html)::`renderPass` equal to
[VK_NULL_HANDLE](VK_NULL_HANDLE.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-pColorAttachments-08963) VUID-vkCmdDrawMultiIndexedEXT-pColorAttachments-08963

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html),
[vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has not yet been recorded in the render
pass instance,
there is a graphics pipeline bound with a fragment shader that
statically writes to a color attachment, the color write mask is not
zero, color writes are enabled, and the corresponding element of the
[VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments->imageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), then the corresponding element of
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`pColorAttachmentFormats` used
to create the pipeline **must** not be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-pColorAttachments-11539) VUID-vkCmdDrawMultiIndexedEXT-pColorAttachments-11539

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), [vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has been
recorded in the render pass instance, there is a graphics pipeline bound
with a fragment shader that statically writes to a color attachment, the
color write mask is not zero, color writes are enabled, and the
corresponding element of the
[VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments->resolveImageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), then the corresponding element of
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`pColorAttachmentFormats` used
to create the pipeline **must** not be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-pDepthAttachment-08964) VUID-vkCmdDrawMultiIndexedEXT-pDepthAttachment-08964

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html),
[vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has not yet been recorded in the render
pass instance,
there is a graphics pipeline bound, depth test is enabled, and the
[VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->imageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), then the
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`depthAttachmentFormat` used to
create the pipeline **must** not be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-pDepthAttachment-11540) VUID-vkCmdDrawMultiIndexedEXT-pDepthAttachment-11540

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), [vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has been
recorded in the render pass instance, there is a graphics pipeline
bound, depth test is enabled, and the
[VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->resolveImageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), then the
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`depthAttachmentFormat` used to
create the pipeline **must** not be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-pStencilAttachment-08965) VUID-vkCmdDrawMultiIndexedEXT-pStencilAttachment-08965

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html),
[vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has not yet been recorded in the render
pass instance,
there is a graphics pipeline bound, stencil test is enabled and the
[VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->imageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), then the
[VkPipelineRenderingCreateInfo](VkPipelineRenderingCreateInfo.html)::`stencilAttachmentFormat` used
to create the pipeline **must** not be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-pStencilAttachment-11860) VUID-vkCmdDrawMultiIndexedEXT-pStencilAttachment-11860

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), [vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has been
recorded in the render pass instance, there is a graphics pipeline
bound, stencil test is enabled and the
[VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->resolveImageView` was
not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), then the
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`stencilAttachmentFormat` used
to create the pipeline **must** not be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-flags-10582) VUID-vkCmdDrawMultiIndexedEXT-flags-10582

If the current render pass instance was begun with a
[vkCmdBeginRendering](vkCmdBeginRendering.html) call in `commandBuffer`, its
[VkRenderingInfo](VkRenderingInfo.html)::`flags` parameter **must** not have
`VK_RENDERING_CONTENTS_SECONDARY_COMMAND_BUFFERS_BIT` set
unless `VK_RENDERING_CONTENTS_INLINE_BIT_KHR` is also set

[](#VUID-vkCmdDrawMultiIndexedEXT-primitivesGeneratedQueryWithRasterizerDiscard-06708) VUID-vkCmdDrawMultiIndexedEXT-primitivesGeneratedQueryWithRasterizerDiscard-06708

If the [    `primitivesGeneratedQueryWithRasterizerDiscard`](../../../../spec/latest/chapters/features.html#features-primitivesGeneratedQueryWithRasterizerDiscard) feature is not
enabled and the `VK_QUERY_TYPE_PRIMITIVES_GENERATED_EXT` query is
active, [rasterization discard](../../../../spec/latest/chapters/primsrast.html#primsrast-discard) **must** not be enabled

[](#VUID-vkCmdDrawMultiIndexedEXT-primitivesGeneratedQueryWithNonZeroStreams-06709) VUID-vkCmdDrawMultiIndexedEXT-primitivesGeneratedQueryWithNonZeroStreams-06709

If the [    `primitivesGeneratedQueryWithNonZeroStreams`](../../../../spec/latest/chapters/features.html#features-primitivesGeneratedQueryWithNonZeroStreams) feature is not
enabled and the `VK_QUERY_TYPE_PRIMITIVES_GENERATED_EXT` query is
active, the bound graphics pipeline **must** not have been created with a
non-zero value in
`VkPipelineRasterizationStateStreamCreateInfoEXT`::`rasterizationStream`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07620) VUID-vkCmdDrawMultiIndexedEXT-None-07620

If the [`depthClamp`](../../../../spec/latest/chapters/features.html#features-depthClamp) feature is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DEPTH_CLAMP_ENABLE_EXT` dynamic state enabled, and
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetDepthClampEnableEXT](vkCmdSetDepthClampEnableEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07621) VUID-vkCmdDrawMultiIndexedEXT-None-07621

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_POLYGON_MODE_EXT` dynamic state enabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetPolygonModeEXT](vkCmdSetPolygonModeEXT.html) **must** have been called and not subsequently
[invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer
prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07622) VUID-vkCmdDrawMultiIndexedEXT-None-07622

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` dynamic state enabled,
and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetRasterizationSamplesEXT](vkCmdSetRasterizationSamplesEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07623) VUID-vkCmdDrawMultiIndexedEXT-None-07623

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_SAMPLE_MASK_EXT` dynamic state enabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetSampleMaskEXT](vkCmdSetSampleMaskEXT.html) **must** have been called and not subsequently
[invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer
prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-alphaToCoverageEnable-08919) VUID-vkCmdDrawMultiIndexedEXT-alphaToCoverageEnable-08919

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_ALPHA_TO_COVERAGE_ENABLE_EXT` dynamic state
enabled, and `alphaToCoverageEnable` was `VK_TRUE` in the last
call to [vkCmdSetAlphaToCoverageEnableEXT](vkCmdSetAlphaToCoverageEnableEXT.html), then the
[Fragment Output Interface](../../../../spec/latest/chapters/interfaces.html#interfaces-fragmentoutput) **must** contain a
variable for the alpha `Component` word in `Location` 0 at
`Index` 0

[](#VUID-vkCmdDrawMultiIndexedEXT-alphaToCoverageEnable-08920) VUID-vkCmdDrawMultiIndexedEXT-alphaToCoverageEnable-08920

If a shader object is bound to any graphics stage, and the most recent
call to [vkCmdSetAlphaToCoverageEnableEXT](vkCmdSetAlphaToCoverageEnableEXT.html) in the current command
buffer set `alphaToCoverageEnable` to `VK_TRUE`, then the
[Fragment Output Interface](../../../../spec/latest/chapters/interfaces.html#interfaces-fragmentoutput) **must** contain a
variable for the alpha `Component` word in `Location` 0 at
`Index` 0

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07624) VUID-vkCmdDrawMultiIndexedEXT-None-07624

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_ALPHA_TO_COVERAGE_ENABLE_EXT` dynamic state
enabled, and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetAlphaToCoverageEnableEXT](vkCmdSetAlphaToCoverageEnableEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07625) VUID-vkCmdDrawMultiIndexedEXT-None-07625

If the [`alphaToOne`](../../../../spec/latest/chapters/features.html#features-alphaToOne) feature is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_ALPHA_TO_ONE_ENABLE_EXT` dynamic state enabled,
and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetAlphaToOneEnableEXT](vkCmdSetAlphaToOneEnableEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07626) VUID-vkCmdDrawMultiIndexedEXT-None-07626

If the [`logicOp`](../../../../spec/latest/chapters/features.html#features-logicOp) feature is enabled,
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_LOGIC_OP_ENABLE_EXT` dynamic state enabled, and
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetLogicOpEnableEXT](vkCmdSetLogicOpEnableEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07627) VUID-vkCmdDrawMultiIndexedEXT-None-07627

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound which was created with
`VK_DYNAMIC_STATE_COLOR_BLEND_ENABLE_EXT` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and there are color
attachments bound, then [vkCmdSetColorBlendEnableEXT](vkCmdSetColorBlendEnableEXT.html) **must** have
been called and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime)
in the current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07629) VUID-vkCmdDrawMultiIndexedEXT-None-07629

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound which was created with
`VK_DYNAMIC_STATE_COLOR_WRITE_MASK_EXT` dynamic state enabled, the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and there are color
attachments bound, then [vkCmdSetColorWriteMaskEXT](vkCmdSetColorWriteMaskEXT.html) **must** have been
called and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in
the current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07630) VUID-vkCmdDrawMultiIndexedEXT-None-07630

If the [`geometryStreams`](../../../../spec/latest/chapters/features.html#features-geometryStreams) feature is
enabled, and
a shader object is bound to the `VK_SHADER_STAGE_GEOMETRY_BIT` stage
or
a graphics pipeline is bound which was created with both a
`VK_SHADER_STAGE_GEOMETRY_BIT` stage and the
`VK_DYNAMIC_STATE_RASTERIZATION_STREAM_EXT` dynamic state enabled,
then [vkCmdSetRasterizationStreamEXT](vkCmdSetRasterizationStreamEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07631) VUID-vkCmdDrawMultiIndexedEXT-None-07631

If the `[VK_EXT_conservative_rasterization](VK_EXT_conservative_rasterization.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_CONSERVATIVE_RASTERIZATION_MODE_EXT` dynamic state
enabled, and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetConservativeRasterizationModeEXT](vkCmdSetConservativeRasterizationModeEXT.html) **must** have been called
and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the
current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07632) VUID-vkCmdDrawMultiIndexedEXT-None-07632

If the `[VK_EXT_conservative_rasterization](VK_EXT_conservative_rasterization.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_EXTRA_PRIMITIVE_OVERESTIMATION_SIZE_EXT` dynamic
state enabled, the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`conservativeRasterizationMode` is
`VK_CONSERVATIVE_RASTERIZATION_MODE_OVERESTIMATE_EXT`, then
[vkCmdSetExtraPrimitiveOverestimationSizeEXT](vkCmdSetExtraPrimitiveOverestimationSizeEXT.html) **must** have been called
and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the
current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-conservativePointAndLineRasterization-07499) VUID-vkCmdDrawMultiIndexedEXT-conservativePointAndLineRasterization-07499

If the `[VK_EXT_conservative_rasterization](VK_EXT_conservative_rasterization.html)` extension is enabled,
[    `conservativePointAndLineRasterization`](../../../../spec/latest/chapters/limits.html#limits-conservativePointAndLineRasterization) is not supported,
a shader object is bound to any graphics stage or
a graphics pipeline is bound, the [current    value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `rasterizerDiscardEnable` is `VK_FALSE`, and the
[effective rasterization input    topology](../../../../spec/latest/chapters/drawing.html#drawing-rasterization-input-topology) is in line or point topology class, then the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`conservativeRasterizationMode` **must** be
`VK_CONSERVATIVE_RASTERIZATION_MODE_DISABLED_EXT`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07633) VUID-vkCmdDrawMultiIndexedEXT-None-07633

If the [`depthClipEnable`](../../../../spec/latest/chapters/features.html#features-depthClipEnable) feature is
enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DEPTH_CLIP_ENABLE_EXT` dynamic state, then
[vkCmdSetDepthClipEnableEXT](vkCmdSetDepthClipEnableEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07636) VUID-vkCmdDrawMultiIndexedEXT-None-07636

If the `[VK_EXT_provoking_vertex](VK_EXT_provoking_vertex.html)` extension is enabled,
a shader object is bound to the `VK_SHADER_STAGE_VERTEX_BIT` stage
or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_PROVOKING_VERTEX_MODE_EXT` dynamic state enabled,
and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetProvokingVertexModeEXT](vkCmdSetProvokingVertexModeEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08666) VUID-vkCmdDrawMultiIndexedEXT-None-08666

If any of the [    `stippledRectangularLines`](../../../../spec/latest/chapters/features.html#features-stippledRectangularLines), [    `stippledBresenhamLines`](../../../../spec/latest/chapters/features.html#features-stippledBresenhamLines) or [    `stippledSmoothLines`](../../../../spec/latest/chapters/features.html#features-stippledSmoothLines) features are enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_LINE_RASTERIZATION_MODE_EXT` dynamic state
enabled, and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[effective rasterization input    topology](../../../../spec/latest/chapters/drawing.html#drawing-rasterization-input-topology) is in line topology class, then
[vkCmdSetLineRasterizationModeEXT](vkCmdSetLineRasterizationModeEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08669) VUID-vkCmdDrawMultiIndexedEXT-None-08669

If any of the [    `stippledRectangularLines`](../../../../spec/latest/chapters/features.html#features-stippledRectangularLines), [    `stippledBresenhamLines`](../../../../spec/latest/chapters/features.html#features-stippledBresenhamLines) or [    `stippledSmoothLines`](../../../../spec/latest/chapters/features.html#features-stippledSmoothLines) features are enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_LINE_STIPPLE_ENABLE_EXT` dynamic state enabled,
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[effective rasterization input    topology](../../../../spec/latest/chapters/drawing.html#drawing-rasterization-input-topology) is in line topology class, then
[vkCmdSetLineStippleEnableEXT](vkCmdSetLineStippleEnableEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07849) VUID-vkCmdDrawMultiIndexedEXT-None-07849

    If any of the [    `stippledRectangularLines`](../../../../spec/latest/chapters/features.html#features-stippledRectangularLines), [    `stippledBresenhamLines`](../../../../spec/latest/chapters/features.html#features-stippledBresenhamLines) or [    `stippledSmoothLines`](../../../../spec/latest/chapters/features.html#features-stippledSmoothLines) features are enabled and
    a shader object is bound to any graphics stage, or
    a bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_LINE_STIPPLE`
    dynamic state enabled, the [current    value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `rasterizerDiscardEnable` is `VK_FALSE`, and the
    [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
    `stippledLineEnable` is `VK_TRUE`, then
[vkCmdSetLineStipple](vkCmdSetLineStipple.html)
    **must** have been called and not subsequently [    invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current command buffer prior to this drawing
    command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-10608) VUID-vkCmdDrawMultiIndexedEXT-None-10608

If
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_LINE_RASTERIZATION_MODE_EXT` dynamic state
enabled, the [effective    rasterization input topology](../../../../spec/latest/chapters/drawing.html#drawing-rasterization-input-topology) is in line topology class, and the
current `lineRasterizationMode` is
`VK_LINE_RASTERIZATION_MODE_BRESENHAM` or
`VK_LINE_RASTERIZATION_MODE_RECTANGULAR_SMOOTH`, then the current
`alphaToCoverageEnable`, `alphaToOneEnable` and
`sampleShadingEnable` states **must** all be `VK_FALSE`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07639) VUID-vkCmdDrawMultiIndexedEXT-None-07639

If the [`depthClipControl`](../../../../spec/latest/chapters/features.html#features-depthClipControl) feature is
enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DEPTH_CLIP_NEGATIVE_ONE_TO_ONE_EXT` dynamic state
enabled, then [vkCmdSetDepthClipNegativeOneToOneEXT](vkCmdSetDepthClipNegativeOneToOneEXT.html) **must** have been
called and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in
the current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09650) VUID-vkCmdDrawMultiIndexedEXT-None-09650

If the [`depthClampControl`](../../../../spec/latest/chapters/features.html#features-depthClampControl) feature
is enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_DEPTH_CLAMP_RANGE_EXT` dynamic state enabled, and
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`depthClampEnable` is `VK_TRUE`, then
[vkCmdSetDepthClampRangeEXT](vkCmdSetDepthClampRangeEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07640) VUID-vkCmdDrawMultiIndexedEXT-None-07640

If the `[VK_NV_clip_space_w_scaling](VK_NV_clip_space_w_scaling.html)` extension is enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_VIEWPORT_W_SCALING_ENABLE_NV` dynamic state
enabled, then [vkCmdSetViewportWScalingEnableNV](vkCmdSetViewportWScalingEnableNV.html) **must** have been
called and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in
the current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07641) VUID-vkCmdDrawMultiIndexedEXT-None-07641

If the `[VK_NV_viewport_swizzle](VK_NV_viewport_swizzle.html)` extension is enabled, and
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_VIEWPORT_SWIZZLE_NV` dynamic state enabled, then
[vkCmdSetViewportSwizzleNV](vkCmdSetViewportSwizzleNV.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07642) VUID-vkCmdDrawMultiIndexedEXT-None-07642

If the `[VK_NV_fragment_coverage_to_color](VK_NV_fragment_coverage_to_color.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_COVERAGE_TO_COLOR_ENABLE_NV` dynamic state
enabled, and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetCoverageToColorEnableNV](vkCmdSetCoverageToColorEnableNV.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07643) VUID-vkCmdDrawMultiIndexedEXT-None-07643

If the `[VK_NV_fragment_coverage_to_color](VK_NV_fragment_coverage_to_color.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_COVERAGE_TO_COLOR_LOCATION_NV` dynamic state
enabled, the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`coverageToColorEnable` is `VK_TRUE`, then
[vkCmdSetCoverageToColorLocationNV](vkCmdSetCoverageToColorLocationNV.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07644) VUID-vkCmdDrawMultiIndexedEXT-None-07644

If the `[VK_NV_framebuffer_mixed_samples](VK_NV_framebuffer_mixed_samples.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_COVERAGE_MODULATION_MODE_NV` dynamic state
enabled, and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetCoverageModulationModeNV](vkCmdSetCoverageModulationModeNV.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07645) VUID-vkCmdDrawMultiIndexedEXT-None-07645

If the `[VK_NV_framebuffer_mixed_samples](VK_NV_framebuffer_mixed_samples.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_COVERAGE_MODULATION_TABLE_ENABLE_NV` dynamic state
enabled, the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`coverageModulationMode` is any value other than
`VK_COVERAGE_MODULATION_MODE_NONE_NV`, then
[vkCmdSetCoverageModulationTableEnableNV](vkCmdSetCoverageModulationTableEnableNV.html) **must** have been called and
not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07646) VUID-vkCmdDrawMultiIndexedEXT-None-07646

If the `[VK_NV_framebuffer_mixed_samples](VK_NV_framebuffer_mixed_samples.html)` extension is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_COVERAGE_MODULATION_TABLE_NV` dynamic state
enabled, the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`coverageModulationTableEnable` is `VK_TRUE`, then
[vkCmdSetCoverageModulationTableNV](vkCmdSetCoverageModulationTableNV.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07647) VUID-vkCmdDrawMultiIndexedEXT-None-07647

If the [`shadingRateImage`](../../../../spec/latest/chapters/features.html#features-shadingRateImage) feature is
enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_SHADING_RATE_IMAGE_ENABLE_NV` dynamic state
enabled, and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetShadingRateImageEnableNV](vkCmdSetShadingRateImageEnableNV.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-pipelineFragmentShadingRate-09238) VUID-vkCmdDrawMultiIndexedEXT-pipelineFragmentShadingRate-09238

If the [    `pipelineFragmentShadingRate`](../../../../spec/latest/chapters/features.html#features-pipelineFragmentShadingRate) feature is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_FRAGMENT_SHADING_RATE_KHR` dynamic state enabled,
and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetFragmentShadingRateKHR](vkCmdSetFragmentShadingRateKHR.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07648) VUID-vkCmdDrawMultiIndexedEXT-None-07648

If the [    `representativeFragmentTest`](../../../../spec/latest/chapters/features.html#features-representativeFragmentTest) feature is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_REPRESENTATIVE_FRAGMENT_TEST_ENABLE_NV` dynamic
state enabled, and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetRepresentativeFragmentTestEnableNV](vkCmdSetRepresentativeFragmentTestEnableNV.html) **must** have been called
and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the
current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07649) VUID-vkCmdDrawMultiIndexedEXT-None-07649

If the [`coverageReductionMode`](../../../../spec/latest/chapters/features.html#features-coverageReductionMode)
feature is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_COVERAGE_REDUCTION_MODE_NV` dynamic state enabled,
and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetCoverageReductionModeNV](vkCmdSetCoverageReductionModeNV.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-rasterizationSamples-07471) VUID-vkCmdDrawMultiIndexedEXT-rasterizationSamples-07471

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` state enabled, and the
current subpass does not use any color and/or depth/stencil attachments,
then the `rasterizationSamples` in the last call to
[vkCmdSetRasterizationSamplesEXT](vkCmdSetRasterizationSamplesEXT.html) **must** follow the rules for a
[zero-attachment subpass](../../../../spec/latest/chapters/renderpass.html#renderpass-noattachments)

[](#VUID-vkCmdDrawMultiIndexedEXT-samples-07472) VUID-vkCmdDrawMultiIndexedEXT-samples-07472

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_SAMPLE_MASK_EXT` state enabled and the
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` state disabled, then
the `samples` parameter in the last call to
[vkCmdSetSampleMaskEXT](vkCmdSetSampleMaskEXT.html) **must** be greater or equal to the
[VkPipelineMultisampleStateCreateInfo](VkPipelineMultisampleStateCreateInfo.html)::`rasterizationSamples`
parameter used to create the bound graphics pipeline

[](#VUID-vkCmdDrawMultiIndexedEXT-samples-07473) VUID-vkCmdDrawMultiIndexedEXT-samples-07473

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_SAMPLE_MASK_EXT` state and
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` states enabled, then
the `samples` parameter in the last call to
[vkCmdSetSampleMaskEXT](vkCmdSetSampleMaskEXT.html) **must** be greater or equal to the
`rasterizationSamples` parameter in the last call to
[vkCmdSetRasterizationSamplesEXT](vkCmdSetRasterizationSamplesEXT.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-rasterizationSamples-07474) VUID-vkCmdDrawMultiIndexedEXT-rasterizationSamples-07474

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` state enabled, and
the [    `multisampledRenderToSingleSampled`](../../../../spec/latest/chapters/features.html#features-multisampledRenderToSingleSampled) feature is not enabled, and
neither the `[VK_AMD_mixed_attachment_samples](VK_AMD_mixed_attachment_samples.html)` nor the
`[VK_NV_framebuffer_mixed_samples](VK_NV_framebuffer_mixed_samples.html)` extensions are enabled, then
the `rasterizationSamples` in the last call to
[vkCmdSetRasterizationSamplesEXT](vkCmdSetRasterizationSamplesEXT.html) **must** be the same as the current
subpass color and/or depth/stencil attachments

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09211) VUID-vkCmdDrawMultiIndexedEXT-None-09211

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` state enabled,
or a shader object is bound to any graphics stage,
and the current render pass instance includes a
[VkMultisampledRenderToSingleSampledInfoEXT](VkMultisampledRenderToSingleSampledInfoEXT.html) structure with
`multisampledRenderToSingleSampledEnable` equal to `VK_TRUE`,
then the `rasterizationSamples` in the last call to
[vkCmdSetRasterizationSamplesEXT](vkCmdSetRasterizationSamplesEXT.html) **must** be the same as the
`rasterizationSamples` member of that structure

[](#VUID-vkCmdDrawMultiIndexedEXT-firstAttachment-07476) VUID-vkCmdDrawMultiIndexedEXT-firstAttachment-07476

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound was created with the
`VK_DYNAMIC_STATE_COLOR_BLEND_ENABLE_EXT` dynamic states enabled,
and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then the last call to
[vkCmdSetColorBlendEnableEXT](vkCmdSetColorBlendEnableEXT.html) in the current command buffer prior to
this drawing command **must** have set a value for all active color
attachments

[](#VUID-vkCmdDrawMultiIndexedEXT-firstAttachment-07478) VUID-vkCmdDrawMultiIndexedEXT-firstAttachment-07478

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound was created with the
`VK_DYNAMIC_STATE_COLOR_WRITE_MASK_EXT` dynamic states enabled, and
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then the last call to
[vkCmdSetColorWriteMaskEXT](vkCmdSetColorWriteMaskEXT.html) in the current command buffer prior to
this drawing command **must** have set a value for all active color
attachments

[](#VUID-vkCmdDrawMultiIndexedEXT-advancedBlendMaxColorAttachments-07480) VUID-vkCmdDrawMultiIndexedEXT-advancedBlendMaxColorAttachments-07480

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound was created with the
`VK_DYNAMIC_STATE_COLOR_BLEND_ADVANCED_EXT` and
`VK_DYNAMIC_STATE_COLOR_BLEND_ENABLE_EXT` dynamic states enabled,
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, and an active color
attachment [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`blendEnable` is `VK_TRUE`, then the number of active color
attachments **must** not exceed [    `advancedBlendMaxColorAttachments`](../../../../spec/latest/chapters/limits.html#limits-advancedBlendMaxColorAttachments)

[](#VUID-vkCmdDrawMultiIndexedEXT-None-10862) VUID-vkCmdDrawMultiIndexedEXT-None-10862

If a graphics pipeline is bound was created with
`VK_DYNAMIC_STATE_COLOR_BLEND_EQUATION_EXT`
, but not the `VK_DYNAMIC_STATE_COLOR_BLEND_ADVANCED_EXT`
dynamic state enabled, and the [current    value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetColorBlendEquationEXT](vkCmdSetColorBlendEquationEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command for all active color
attachments with the `blendEnable` [    current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `VK_TRUE`

[](#VUID-vkCmdDrawMultiIndexedEXT-rasterizerDiscardEnable-10863) VUID-vkCmdDrawMultiIndexedEXT-rasterizerDiscardEnable-10863

If a graphics pipeline is bound was created with
`VK_DYNAMIC_STATE_COLOR_BLEND_ADVANCED_EXT`, but not the
`VK_DYNAMIC_STATE_COLOR_BLEND_EQUATION_EXT` dynamic state enabled,
and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetColorBlendAdvancedEXT](vkCmdSetColorBlendAdvancedEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command for all active color
attachments with the `blendEnable` [    current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `VK_TRUE`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-10864) VUID-vkCmdDrawMultiIndexedEXT-None-10864

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound was created with
`VK_DYNAMIC_STATE_COLOR_BLEND_ADVANCED_EXT` and
`VK_DYNAMIC_STATE_COLOR_BLEND_EQUATION_EXT` dynamic state enabled,
and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
either [vkCmdSetColorBlendAdvancedEXT](vkCmdSetColorBlendAdvancedEXT.html) or
[vkCmdSetColorBlendEquationEXT](vkCmdSetColorBlendEquationEXT.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command for all active color
attachments with the `blendEnable` [    current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `VK_TRUE`

[](#VUID-vkCmdDrawMultiIndexedEXT-primitivesGeneratedQueryWithNonZeroStreams-07481) VUID-vkCmdDrawMultiIndexedEXT-primitivesGeneratedQueryWithNonZeroStreams-07481

If the [    `primitivesGeneratedQueryWithNonZeroStreams`](../../../../spec/latest/chapters/features.html#features-primitivesGeneratedQueryWithNonZeroStreams) feature is not
enabled and the `VK_QUERY_TYPE_PRIMITIVES_GENERATED_EXT` query is
active, and the bound graphics pipeline was created with
`VK_DYNAMIC_STATE_RASTERIZATION_STREAM_EXT` state enabled, the last
call to [vkCmdSetRasterizationStreamEXT](vkCmdSetRasterizationStreamEXT.html) **must** have set the
`rasterizationStream` to zero

[](#VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsPerPixel-07482) VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsPerPixel-07482

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_EXT` state enabled and the
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` state disabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`sampleLocationsEnable` is `VK_TRUE`, then the
`sampleLocationsPerPixel` member of `pSampleLocationsInfo` in
the last call to [vkCmdSetSampleLocationsEXT](vkCmdSetSampleLocationsEXT.html) **must** equal the
`rasterizationSamples` member of the
[VkPipelineMultisampleStateCreateInfo](VkPipelineMultisampleStateCreateInfo.html) structure the bound graphics
pipeline has been created with

[](#VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsPerPixel-07483) VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsPerPixel-07483

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_EXT` state enabled and the
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` state enabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`sampleLocationsEnable` is `VK_TRUE`, then the
`sampleLocationsPerPixel` member of `pSampleLocationsInfo` in
the last call to [vkCmdSetSampleLocationsEXT](vkCmdSetSampleLocationsEXT.html) **must** equal the
`rasterizationSamples` parameter of the last call to
[vkCmdSetRasterizationSamplesEXT](vkCmdSetRasterizationSamplesEXT.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07484) VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07484

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT`
stage, or
the bound graphics pipeline was created with the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_ENABLE_EXT` state enabled, and
`sampleLocationsEnable` was `VK_TRUE` in the last call to
[vkCmdSetSampleLocationsEnableEXT](vkCmdSetSampleLocationsEnableEXT.html) then the current active depth
attachment **must** have been created with the
`VK_IMAGE_CREATE_SAMPLE_LOCATIONS_COMPATIBLE_DEPTH_BIT_EXT` bit set

[](#VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07485) VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07485

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT`
stage, or
the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_EXT` state enabled and the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_ENABLE_EXT` state enabled, and if
`sampleLocationsEnable` was `VK_TRUE` in the last call to
[vkCmdSetSampleLocationsEnableEXT](vkCmdSetSampleLocationsEnableEXT.html), then the
`sampleLocationsInfo.maxSampleLocationGridSize.width` in the last
call to [vkCmdSetSampleLocationsEXT](vkCmdSetSampleLocationsEXT.html) **must** evenly divide
[VkMultisamplePropertiesEXT](VkMultisamplePropertiesEXT.html)::`maxSampleLocationGridSize.width`
as returned by [vkGetPhysicalDeviceMultisamplePropertiesEXT](vkGetPhysicalDeviceMultisamplePropertiesEXT.html) with a
`samples` parameter equaling `rasterizationSamples`

[](#VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07486) VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07486

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT`
stage, or
the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_EXT` state enabled and the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_ENABLE_EXT` state enabled, and if
`sampleLocationsEnable` was `VK_TRUE` in the last call to
[vkCmdSetSampleLocationsEnableEXT](vkCmdSetSampleLocationsEnableEXT.html), then the
`sampleLocationsInfo.maxSampleLocationGridSize.height` in the last
call to [vkCmdSetSampleLocationsEXT](vkCmdSetSampleLocationsEXT.html) **must** evenly divide
[VkMultisamplePropertiesEXT](VkMultisamplePropertiesEXT.html)::`maxSampleLocationGridSize.height`
as returned by [vkGetPhysicalDeviceMultisamplePropertiesEXT](vkGetPhysicalDeviceMultisamplePropertiesEXT.html) with a
`samples` parameter equaling `rasterizationSamples`

[](#VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07487) VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07487

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT`
stage, or
the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_ENABLE_EXT` state enabled, and if
`sampleLocationsEnable` was `VK_TRUE` in the last call to
[vkCmdSetSampleLocationsEnableEXT](vkCmdSetSampleLocationsEnableEXT.html), the fragment shader code **must**
not statically use the extended instruction `InterpolateAtSample`

[](#VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07936) VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07936

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_EXT` state disabled and the
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` state enabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`sampleLocationsEnable` is `VK_TRUE`, then
`sampleLocationsInfo.sampleLocationGridSize.width` **must** evenly
divide
[VkMultisamplePropertiesEXT](VkMultisamplePropertiesEXT.html)::`maxSampleLocationGridSize.width`
as returned by [vkGetPhysicalDeviceMultisamplePropertiesEXT](vkGetPhysicalDeviceMultisamplePropertiesEXT.html) with a
`samples` parameter equaling the value of `rasterizationSamples`
in the last call to [vkCmdSetRasterizationSamplesEXT](vkCmdSetRasterizationSamplesEXT.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07937) VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07937

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_EXT` state disabled and the
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` state enabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`sampleLocationsEnable` is `VK_TRUE`, then
`sampleLocationsInfo.sampleLocationGridSize.height` **must** evenly
divide
[VkMultisamplePropertiesEXT](VkMultisamplePropertiesEXT.html)::`maxSampleLocationGridSize.height`
as returned by [vkGetPhysicalDeviceMultisamplePropertiesEXT](vkGetPhysicalDeviceMultisamplePropertiesEXT.html) with a
`samples` parameter equaling the value of `rasterizationSamples`
in the last call to [vkCmdSetRasterizationSamplesEXT](vkCmdSetRasterizationSamplesEXT.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07938) VUID-vkCmdDrawMultiIndexedEXT-sampleLocationsEnable-07938

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_SAMPLE_LOCATIONS_EXT` state disabled and the
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` state enabled, and the
[current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`sampleLocationsEnable` is `VK_TRUE`, then
`sampleLocationsInfo.sampleLocationsPerPixel` **must** equal
`rasterizationSamples` in the last call to
[vkCmdSetRasterizationSamplesEXT](vkCmdSetRasterizationSamplesEXT.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-coverageModulationTableEnable-07488) VUID-vkCmdDrawMultiIndexedEXT-coverageModulationTableEnable-07488

If
a shader object is bound to any graphics stage or
the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_COVERAGE_MODULATION_TABLE_ENABLE_NV` state
enabled, and the last call to
[vkCmdSetCoverageModulationTableEnableNV](vkCmdSetCoverageModulationTableEnableNV.html) set
`coverageModulationTableEnable` to `VK_TRUE`, then the
`coverageModulationTableCount` parameter in the last call to
[vkCmdSetCoverageModulationTableNV](vkCmdSetCoverageModulationTableNV.html) **must** equal the current
`rasterizationSamples` divided by the number of color samples in the
current active color attachment

[](#VUID-vkCmdDrawMultiIndexedEXT-rasterizationSamples-07489) VUID-vkCmdDrawMultiIndexedEXT-rasterizationSamples-07489

If the `[VK_NV_framebuffer_mixed_samples](VK_NV_framebuffer_mixed_samples.html)` extension is enabled,
and if current subpass has a depth/stencil attachment and depth test,
stencil test, or depth bounds test are enabled in the bound pipeline,
then the current `rasterizationSamples` **must** be the same as the
sample count of the depth/stencil attachment

[](#VUID-vkCmdDrawMultiIndexedEXT-coverageToColorEnable-07490) VUID-vkCmdDrawMultiIndexedEXT-coverageToColorEnable-07490

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_COVERAGE_TO_COLOR_ENABLE_NV` state enabled and the
last call to [vkCmdSetCoverageToColorEnableNV](vkCmdSetCoverageToColorEnableNV.html) set the
`coverageToColorEnable` to `VK_TRUE`, then there **must** be an
active color attachment at the location selected by the last call to
[vkCmdSetCoverageToColorLocationNV](vkCmdSetCoverageToColorLocationNV.html) `coverageToColorLocation`,
with a [VkFormat](VkFormat.html) of `VK_FORMAT_R8_UINT`,
`VK_FORMAT_R8_SINT`, `VK_FORMAT_R16_UINT`,
`VK_FORMAT_R16_SINT`, `VK_FORMAT_R32_UINT`, or
`VK_FORMAT_R32_SINT`

[](#VUID-vkCmdDrawMultiIndexedEXT-rasterizerDiscardEnable-09420) VUID-vkCmdDrawMultiIndexedEXT-rasterizerDiscardEnable-09420

If the `[VK_NV_fragment_coverage_to_color](VK_NV_fragment_coverage_to_color.html)` extension is enabled,
and a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT`
stage, and the most recent call to [vkCmdSetRasterizerDiscardEnable](vkCmdSetRasterizerDiscardEnable.html)
in the current command buffer set `rasterizerDiscardEnable` to
`VK_FALSE`, and the last call to
[vkCmdSetCoverageToColorEnableNV](vkCmdSetCoverageToColorEnableNV.html) set the
`coverageToColorEnable` to `VK_TRUE`, then there **must** be an
active color attachment at the location selected by the last call to
[vkCmdSetCoverageToColorLocationNV](vkCmdSetCoverageToColorLocationNV.html) `coverageToColorLocation`,
with a [VkFormat](VkFormat.html) of `VK_FORMAT_R8_UINT`,
`VK_FORMAT_R8_SINT`, `VK_FORMAT_R16_UINT`,
`VK_FORMAT_R16_SINT`, `VK_FORMAT_R32_UINT`, or
`VK_FORMAT_R32_SINT`

[](#VUID-vkCmdDrawMultiIndexedEXT-coverageReductionMode-07491) VUID-vkCmdDrawMultiIndexedEXT-coverageReductionMode-07491

If the [`coverageReductionMode`](../../../../spec/latest/chapters/features.html#features-coverageReductionMode)
feature is enabled,
a shader object is bound to any graphics stage or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_COVERAGE_REDUCTION_MODE_NV` or
`VK_DYNAMIC_STATE_RASTERIZATION_SAMPLES_EXT` dynamic states enabled,
then the [current values](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`coverageReductionMode`, `rasterizationSamples`, the sample
counts for the color and depth/stencil attachments (if the subpass has
them) **must** be a valid combination returned by
[vkGetPhysicalDeviceSupportedFramebufferMixedSamplesCombinationsNV](vkGetPhysicalDeviceSupportedFramebufferMixedSamplesCombinationsNV.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-viewportCount-07492) VUID-vkCmdDrawMultiIndexedEXT-viewportCount-07492

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` dynamic state enabled, but
not the `VK_DYNAMIC_STATE_VIEWPORT_SWIZZLE_NV` dynamic state
enabled, then the bound graphics pipeline **must** have been created with
[VkPipelineViewportSwizzleStateCreateInfoNV](VkPipelineViewportSwizzleStateCreateInfoNV.html)::`viewportCount`
greater or equal to the `viewportCount` parameter in the last call
to [vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-viewportCount-07493) VUID-vkCmdDrawMultiIndexedEXT-viewportCount-07493

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_VIEWPORT_WITH_COUNT` and
`VK_DYNAMIC_STATE_VIEWPORT_SWIZZLE_NV` dynamic states enabled then
the `viewportCount` parameter in the last call to
[vkCmdSetViewportSwizzleNV](vkCmdSetViewportSwizzleNV.html) **must** be greater than or equal to the
`viewportCount` parameter in the last call to
[vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-viewportCount-09421) VUID-vkCmdDrawMultiIndexedEXT-viewportCount-09421

If the `[VK_NV_viewport_swizzle](VK_NV_viewport_swizzle.html)` extension is enabled, and a
shader object is bound to any graphics stage, then the
`viewportCount` parameter in the last call to
[vkCmdSetViewportSwizzleNV](vkCmdSetViewportSwizzleNV.html) **must** be greater than or equal to the
`viewportCount` parameter in the last call to
[vkCmdSetViewportWithCount](vkCmdSetViewportWithCount.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-rasterizationSamples-07494) VUID-vkCmdDrawMultiIndexedEXT-rasterizationSamples-07494

If the `[VK_NV_framebuffer_mixed_samples](VK_NV_framebuffer_mixed_samples.html)` extension is enabled,
and the [`coverageReductionMode`](../../../../spec/latest/chapters/features.html#features-coverageReductionMode)
feature is not enabled, or the [current    value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of `coverageReductionMode` is not
`VK_COVERAGE_REDUCTION_MODE_TRUNCATE_NV`,
and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizationSamples` is greater than sample count of the color
attachment, then [sample shading](../../../../spec/latest/chapters/primsrast.html#primsrast-sampleshading) **must** be
disabled

[](#VUID-vkCmdDrawMultiIndexedEXT-stippledLineEnable-07495) VUID-vkCmdDrawMultiIndexedEXT-stippledLineEnable-07495

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_LINE_STIPPLE_ENABLE_EXT` or
`VK_DYNAMIC_STATE_LINE_RASTERIZATION_MODE_EXT` dynamic states
enabled, and if the current `stippledLineEnable` state is
`VK_TRUE` and the current `lineRasterizationMode` state is
`VK_LINE_RASTERIZATION_MODE_RECTANGULAR`, then the
[`stippledRectangularLines`](../../../../spec/latest/chapters/features.html#features-stippledRectangularLines)
feature **must** be enabled

[](#VUID-vkCmdDrawMultiIndexedEXT-stippledLineEnable-07496) VUID-vkCmdDrawMultiIndexedEXT-stippledLineEnable-07496

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_LINE_STIPPLE_ENABLE_EXT` or
`VK_DYNAMIC_STATE_LINE_RASTERIZATION_MODE_EXT` dynamic states
enabled, and if the current `stippledLineEnable` state is
`VK_TRUE` and the current `lineRasterizationMode` state is
`VK_LINE_RASTERIZATION_MODE_BRESENHAM`, then the
[`stippledBresenhamLines`](../../../../spec/latest/chapters/features.html#features-stippledBresenhamLines)
feature **must** be enabled

[](#VUID-vkCmdDrawMultiIndexedEXT-stippledLineEnable-07497) VUID-vkCmdDrawMultiIndexedEXT-stippledLineEnable-07497

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_LINE_STIPPLE_ENABLE_EXT` or
`VK_DYNAMIC_STATE_LINE_RASTERIZATION_MODE_EXT` dynamic states
enabled, and if the current `stippledLineEnable` state is
`VK_TRUE` and the current `lineRasterizationMode` state is
`VK_LINE_RASTERIZATION_MODE_RECTANGULAR_SMOOTH`, then the
[`stippledSmoothLines`](../../../../spec/latest/chapters/features.html#features-stippledSmoothLines) feature
**must** be enabled

[](#VUID-vkCmdDrawMultiIndexedEXT-stippledLineEnable-07498) VUID-vkCmdDrawMultiIndexedEXT-stippledLineEnable-07498

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_LINE_STIPPLE_ENABLE_EXT` or
`VK_DYNAMIC_STATE_LINE_RASTERIZATION_MODE_EXT` dynamic states
enabled, and if the current `stippledLineEnable` state is
`VK_TRUE` and the current `lineRasterizationMode` state is
`VK_LINE_RASTERIZATION_MODE_DEFAULT`, then the
[`stippledRectangularLines`](../../../../spec/latest/chapters/features.html#features-stippledRectangularLines)
feature **must** be enabled and
[VkPhysicalDeviceLimits](VkPhysicalDeviceLimits.html)::`strictLines` **must** be `VK_TRUE`

[](#VUID-vkCmdDrawMultiIndexedEXT-stage-07073) VUID-vkCmdDrawMultiIndexedEXT-stage-07073

If the bound pipeline was created with the
[VkPipelineShaderStageCreateInfo](VkPipelineShaderStageCreateInfo.html)::`stage` member of an element
of [VkGraphicsPipelineCreateInfo](VkGraphicsPipelineCreateInfo.html)::`pStages` set to
`VK_SHADER_STAGE_VERTEX_BIT`,
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT`,
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT` or
`VK_SHADER_STAGE_GEOMETRY_BIT`, then [Mesh    Shader Queries](../../../../spec/latest/chapters/queries.html#queries-mesh-shader) **must** not be active

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08877) VUID-vkCmdDrawMultiIndexedEXT-None-08877

If
a shader object is bound to the `VK_SHADER_STAGE_FRAGMENT_BIT` stage
or
a graphics pipeline is bound which was created with the
`VK_DYNAMIC_STATE_ATTACHMENT_FEEDBACK_LOOP_ENABLE_EXT` dynamic state
enabled, and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`rasterizerDiscardEnable` is `VK_FALSE`, then
[vkCmdSetAttachmentFeedbackLoopEnableEXT](vkCmdSetAttachmentFeedbackLoopEnableEXT.html) **must** have been called and
not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-None-07850) VUID-vkCmdDrawMultiIndexedEXT-None-07850

If dynamic state was inherited from
[VkCommandBufferInheritanceViewportScissorInfoNV](VkCommandBufferInheritanceViewportScissorInfoNV.html), it **must** be set
in the current command buffer prior to this drawing command

[](#VUID-vkCmdDrawMultiIndexedEXT-nextStage-10745) VUID-vkCmdDrawMultiIndexedEXT-nextStage-10745

For each shader object bound to a graphics stage, except for shader
object bound to the last graphics stage in the logical pipeline, it
**must** have been created with a `nextStage` including the
corresponding bit to the shader object bound to the following graphics
stage in the logical pipeline

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08684) VUID-vkCmdDrawMultiIndexedEXT-None-08684

If there is no bound graphics pipeline, `vkCmdBindShadersEXT` **must**
have been called in the current command buffer with `pStages` with
an element of `VK_SHADER_STAGE_VERTEX_BIT`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08685) VUID-vkCmdDrawMultiIndexedEXT-None-08685

If there is no bound graphics pipeline, and the
[`tessellationShader`](../../../../spec/latest/chapters/features.html#features-tessellationShader) feature is
enabled, `vkCmdBindShadersEXT` **must** have been called in the current
command buffer with `pStages` with an element of
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08686) VUID-vkCmdDrawMultiIndexedEXT-None-08686

If there is no bound graphics pipeline, and the
[`tessellationShader`](../../../../spec/latest/chapters/features.html#features-tessellationShader) feature is
enabled, `vkCmdBindShadersEXT` **must** have been called in the current
command buffer with `pStages` with an element of
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08687) VUID-vkCmdDrawMultiIndexedEXT-None-08687

If there is no bound graphics pipeline, and the
[`geometryShader`](../../../../spec/latest/chapters/features.html#features-geometryShader) feature is enabled,
`vkCmdBindShadersEXT` **must** have been called in the current command
buffer with `pStages` with an element of
`VK_SHADER_STAGE_GEOMETRY_BIT`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08688) VUID-vkCmdDrawMultiIndexedEXT-None-08688

If there is no bound graphics pipeline, `vkCmdBindShadersEXT` **must**
have been called in the current command buffer with `pStages` with
an element of `VK_SHADER_STAGE_FRAGMENT_BIT`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08689) VUID-vkCmdDrawMultiIndexedEXT-None-08689

If there is no bound graphics pipeline, and the [    `taskShader`](../../../../spec/latest/chapters/features.html#features-taskShader) feature is enabled, `vkCmdBindShadersEXT` **must**
have been called in the current command buffer with `pStages` with
an element of `VK_SHADER_STAGE_TASK_BIT_EXT`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08690) VUID-vkCmdDrawMultiIndexedEXT-None-08690

If there is no bound graphics pipeline, and the [    `meshShader`](../../../../spec/latest/chapters/features.html#features-meshShader) feature is enabled, `vkCmdBindShadersEXT` **must**
have been called in the current command buffer with `pStages` with
an element of `VK_SHADER_STAGE_MESH_BIT_EXT`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08693) VUID-vkCmdDrawMultiIndexedEXT-None-08693

If there is no bound graphics pipeline, and at least one of the
[`taskShader`](../../../../spec/latest/chapters/features.html#features-taskShader) and [    `meshShader`](../../../../spec/latest/chapters/features.html#features-meshShader) features is enabled, one of the
`VK_SHADER_STAGE_VERTEX_BIT` or `VK_SHADER_STAGE_MESH_BIT_EXT`
stages **must** have a valid `VkShaderEXT` bound, and the other **must**
have no `VkShaderEXT` bound

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08696) VUID-vkCmdDrawMultiIndexedEXT-None-08696

If there is no bound graphics pipeline, and a valid `VkShaderEXT` is
bound to the `VK_SHADER_STAGE_VERTEX_BIT` stage, there **must** be no
`VkShaderEXT` bound to either the `VK_SHADER_STAGE_TASK_BIT_EXT`
stage or the `VK_SHADER_STAGE_MESH_BIT_EXT` stage

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08698) VUID-vkCmdDrawMultiIndexedEXT-None-08698

If any graphics shader is bound which was created with the
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT` flag, then all shaders created
with the `VK_SHADER_CREATE_LINK_STAGE_BIT_EXT` flag in the same
[vkCreateShadersEXT](vkCreateShadersEXT.html) call **must** also be bound

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08699) VUID-vkCmdDrawMultiIndexedEXT-None-08699

If any graphics shader is bound which was created with the
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT` flag, any stages in between
stages whose shaders which did not create a shader with the
`VK_SHADER_CREATE_LINK_STAGE_BIT_EXT` flag as part of the same
[vkCreateShadersEXT](vkCreateShadersEXT.html) call **must** not have any `VkShaderEXT` bound

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08878) VUID-vkCmdDrawMultiIndexedEXT-None-08878

All bound graphics shader objects **must** have been created with identical
or [identically defined](../../../../spec/latest/appendices/glossary.html#glossary-identically-defined) push constant
ranges

[](#VUID-vkCmdDrawMultiIndexedEXT-None-08879) VUID-vkCmdDrawMultiIndexedEXT-None-08879

All bound graphics shader objects **must** have been created with identical
or [identically defined](../../../../spec/latest/appendices/glossary.html#glossary-identically-defined) arrays of
descriptor set layouts

[](#VUID-vkCmdDrawMultiIndexedEXT-colorAttachmentCount-09372) VUID-vkCmdDrawMultiIndexedEXT-colorAttachmentCount-09372

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html) and a
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` equal to `1`, a color
attachment with a resolve mode of
`VK_RESOLVE_MODE_EXTERNAL_FORMAT_DOWNSAMPLE_BIT_ANDROID`, and a
fragment shader is bound, it **must** not declare the `DepthReplacing`
or `StencilRefReplacingEXT` execution modes

[](#VUID-vkCmdDrawMultiIndexedEXT-pDynamicStates-08715) VUID-vkCmdDrawMultiIndexedEXT-pDynamicStates-08715

If the bound graphics pipeline state includes a fragment shader stage,
was created with `VK_DYNAMIC_STATE_DEPTH_WRITE_ENABLE` set in
[VkPipelineDynamicStateCreateInfo](VkPipelineDynamicStateCreateInfo.html)::`pDynamicStates`, and the
fragment shader declares the `EarlyFragmentTests` execution mode and
uses `OpDepthAttachmentReadEXT`, the `depthWriteEnable` parameter
in the last call to [vkCmdSetDepthWriteEnable](vkCmdSetDepthWriteEnable.html) **must** be
`VK_FALSE`

[](#VUID-vkCmdDrawMultiIndexedEXT-pDynamicStates-08716) VUID-vkCmdDrawMultiIndexedEXT-pDynamicStates-08716

If the bound graphics pipeline state includes a fragment shader stage,
was created with `VK_DYNAMIC_STATE_STENCIL_WRITE_MASK` set in
[VkPipelineDynamicStateCreateInfo](VkPipelineDynamicStateCreateInfo.html)::`pDynamicStates`, and the
fragment shader declares the `EarlyFragmentTests` execution mode and
uses `OpStencilAttachmentReadEXT`, the `writeMask` parameter in
the last call to [vkCmdSetStencilWriteMask](vkCmdSetStencilWriteMask.html) **must** be `0`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09116) VUID-vkCmdDrawMultiIndexedEXT-None-09116

    If
    a shader object is bound to any graphics stage
or
    the bound graphics pipeline was created with
    `VK_DYNAMIC_STATE_COLOR_WRITE_MASK_EXT`,
    and the format of any color attachment is
    `VK_FORMAT_E5B9G9R9_UFLOAT_PACK32`, the corresponding element of the
    `pColorWriteMasks` parameter of [vkCmdSetColorWriteMaskEXT](vkCmdSetColorWriteMaskEXT.html)
    **must** either include all of `VK_COLOR_COMPONENT_R_BIT`,
    `VK_COLOR_COMPONENT_G_BIT`, and `VK_COLOR_COMPONENT_B_BIT`, or
    none of them

[](#VUID-vkCmdDrawMultiIndexedEXT-maxFragmentDualSrcAttachments-09239) VUID-vkCmdDrawMultiIndexedEXT-maxFragmentDualSrcAttachments-09239

If [blending](../../../../spec/latest/chapters/framebuffer.html#framebuffer-blending) is enabled for any attachment where
either the source or destination blend factors for that attachment
[use the secondary color input](../../../../spec/latest/chapters/framebuffer.html#framebuffer-dsb), the maximum value of
`Location` for any output attachment [statically    used](../../../../spec/latest/chapters/shaders.html#shaders-staticuse) in the `Fragment` `Execution` `Model` executed by this command
**must** be less than [    `maxFragmentDualSrcAttachments`](../../../../spec/latest/chapters/limits.html#limits-maxFragmentDualSrcAttachments)

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09548) VUID-vkCmdDrawMultiIndexedEXT-None-09548

If the current render pass was begun with [vkCmdBeginRendering](vkCmdBeginRendering.html),
there is no shader object bound to any graphics stage,
the value of each element of
[VkRenderingAttachmentLocationInfo](VkRenderingAttachmentLocationInfo.html)::`pColorAttachmentLocations`
in the bound pipeline **must** match the value for the corresponding
locations set currently in the current render pass instance

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09549) VUID-vkCmdDrawMultiIndexedEXT-None-09549

If the current render pass was begun with [vkCmdBeginRendering](vkCmdBeginRendering.html),
and there is no shader object bound to any graphics stage,
the value of each element of
[VkRenderingInputAttachmentIndexInfo](VkRenderingInputAttachmentIndexInfo.html)::`pColorAttachmentInputIndices`
in the bound pipeline **must** match the value for the corresponding index
set currently in the current render pass instance

[](#VUID-vkCmdDrawMultiIndexedEXT-None-10927) VUID-vkCmdDrawMultiIndexedEXT-None-10927

If the current render pass was begun with [vkCmdBeginRendering](vkCmdBeginRendering.html),
and there is no shader object bound to any graphics stage,
the value of
[VkRenderingInputAttachmentIndexInfo](VkRenderingInputAttachmentIndexInfo.html)::`pDepthInputAttachmentIndex`
in the bound pipeline **must** match the value set currently in the current
render pass instance

[](#VUID-vkCmdDrawMultiIndexedEXT-None-10928) VUID-vkCmdDrawMultiIndexedEXT-None-10928

If the current render pass was begun with [vkCmdBeginRendering](vkCmdBeginRendering.html),
and there is no shader object bound to any graphics stage,
the value of
[VkRenderingInputAttachmentIndexInfo](VkRenderingInputAttachmentIndexInfo.html)::`pStencilInputAttachmentIndex`
in the bound pipeline **must** match the value set currently in the current
render pass instance

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09642) VUID-vkCmdDrawMultiIndexedEXT-None-09642

If the current render pass was begun with [vkCmdBeginRendering](vkCmdBeginRendering.html) with
the `VK_RENDERING_ENABLE_LEGACY_DITHERING_BIT_EXT` flag, the bound
graphics pipeline **must** have been created with
`VK_PIPELINE_CREATE_2_ENABLE_LEGACY_DITHERING_BIT_EXT`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-09643) VUID-vkCmdDrawMultiIndexedEXT-None-09643

If the bound graphics pipeline was created with
`VK_PIPELINE_CREATE_2_ENABLE_LEGACY_DITHERING_BIT_EXT`, the current
render pass **must** have begun with [vkCmdBeginRendering](vkCmdBeginRendering.html) with the
`VK_RENDERING_ENABLE_LEGACY_DITHERING_BIT_EXT` flag

[](#VUID-vkCmdDrawMultiIndexedEXT-None-10677) VUID-vkCmdDrawMultiIndexedEXT-None-10677

If the [per-tile execution model](../../../../spec/latest/chapters/renderpass.html#renderpass-per-tile-execution-model)
is enabled, the
[tileShadingPerTileDraw](../../../../spec/latest/chapters/features.html#features-tileShadingPerTileDraw) feature **must**
be enabled

[](#VUID-vkCmdDrawMultiIndexedEXT-None-10772) VUID-vkCmdDrawMultiIndexedEXT-None-10772

If a shader object is bound to any graphics stage, *multiview*
functionality **must** not be enabled in the current render pass

[](#VUID-vkCmdDrawMultiIndexedEXT-flags-11521) VUID-vkCmdDrawMultiIndexedEXT-flags-11521

If current render pass instance was begun with [vkCmdBeginRendering](vkCmdBeginRendering.html)
with [VkRenderingInfo](VkRenderingInfo.html)::`flags` which includes
`VK_RENDERING_FRAGMENT_REGION_BIT_EXT`, and if
[sample shading](../../../../spec/latest/chapters/primsrast.html#primsrast-sampleshading) is enabled (explicitly or
implicitly), then the minimum fraction for sample shading **must** equal
0.0

[](#VUID-vkCmdDrawMultiIndexedEXT-None-11522) VUID-vkCmdDrawMultiIndexedEXT-None-11522

    If the current render pass instance was begun with
    [vkCmdBeginRendering](vkCmdBeginRendering.html) and contains a custom resolve,
and the [`dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is not enabled,
    the graphics pipeline bound **must** have been created with a
    [VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-None-11523) VUID-vkCmdDrawMultiIndexedEXT-None-11523

    If the current render pass instance was begun with
    [vkCmdBeginRendering](vkCmdBeginRendering.html) and does not contain a custom resolve,
and the [`dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is not enabled,
    the graphics pipeline bound **must** not have been created with a
    [VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)

[](#VUID-vkCmdDrawMultiIndexedEXT-customResolve-11524) VUID-vkCmdDrawMultiIndexedEXT-customResolve-11524

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html) and [vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has been
recorded in the render pass instance, the graphics pipeline bound **must**
have been created with
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`customResolve` as `VK_TRUE`

[](#VUID-vkCmdDrawMultiIndexedEXT-customResolve-11525) VUID-vkCmdDrawMultiIndexedEXT-customResolve-11525

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html) and contains a custom resolve, and
[vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has not been recorded in the render
pass instance, the graphics pipeline bound **must** have been created with
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`customResolve` as
`VK_FALSE`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-11861) VUID-vkCmdDrawMultiIndexedEXT-None-11861

If
the [    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is not enabled and
the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html) and contains a custom resolve, the bound
graphics pipeline **must** have been created with a
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`colorAttachmentCount` equal to
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-11862) VUID-vkCmdDrawMultiIndexedEXT-None-11862

If
the [    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is not enabled, and
the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), it contains a custom resolve, and
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` greater than `0`, then
each element of the [VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments` array
with an `resolveImageView` not equal to [VK_NULL_HANDLE](VK_NULL_HANDLE.html) **must**
have been created with a [VkFormat](VkFormat.html) equal to the corresponding
element of
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`pColorAttachmentFormats` used
to create the bound graphics pipeline

[](#VUID-vkCmdDrawMultiIndexedEXT-None-11863) VUID-vkCmdDrawMultiIndexedEXT-None-11863

If
the [    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is not enabled, and
the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), it contains a custom resolve, and
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` greater than `0`, then
each element of the [VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments` array
with an `resolveImageView` equal to [VK_NULL_HANDLE](VK_NULL_HANDLE.html) **must** have
the corresponding element of
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`pColorAttachmentFormats` used
to create the bound pipeline equal to `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-11864) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-11864

If the [    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is enabled, the
current render pass instance was begun with [vkCmdBeginRendering](vkCmdBeginRendering.html),
it contains a custom resolve, and
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` greater than `0`, then
each element of the [VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments` array
with an `resolveImageView` not equal to [VK_NULL_HANDLE](VK_NULL_HANDLE.html) **must**
have been created with a [VkFormat](VkFormat.html) equal to the corresponding
element of
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`pColorAttachmentFormats` used
to create the bound graphics pipeline, or the corresponding element of
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`pColorAttachmentFormats`, if it
exists, **must** be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-11865) VUID-vkCmdDrawMultiIndexedEXT-None-11865

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), it contains a custom resolve,
the
[`dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments)
feature is not enabled,
and [VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->resolveImageView` was
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`depthAttachmentFormat` used to
create the bound graphics pipeline **must** be equal to
`VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-11866) VUID-vkCmdDrawMultiIndexedEXT-None-11866

If current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), it contains a custom resolve,
the
[`dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments)
feature is not enabled,
and [VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->resolveImageView` was
not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`depthAttachmentFormat` used to
create the bound graphics pipeline **must** be equal to the [VkFormat](VkFormat.html)
used to create
[VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->resolveImageView`

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-11867) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-11867

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), it contains a custom resolve, the
[    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is enabled,
[VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->resolveImageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), and the value of
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`depthAttachmentFormat` used to
create the bound graphics pipeline was not equal to the [VkFormat](VkFormat.html)
used to create
[VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->resolveImageView`, the
value of the format **must** be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-11868) VUID-vkCmdDrawMultiIndexedEXT-None-11868

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), it contains a custom resolve,
the
[`dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments)
feature is not enabled,
and [VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->resolveImageView`
was [VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`stencilAttachmentFormat` used
to create the bound graphics pipeline **must** be equal to
`VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-None-11869) VUID-vkCmdDrawMultiIndexedEXT-None-11869

If current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), it contains a custom resolve,
the
[`dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments)
feature is not enabled,
and [VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->resolveImageView`
was not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`stencilAttachmentFormat` used
to create the bound graphics pipeline **must** be equal to the
[VkFormat](VkFormat.html) used to create
[VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->resolveImageView`

[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-11870) VUID-vkCmdDrawMultiIndexedEXT-dynamicRenderingUnusedAttachments-11870

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), it contains a custom resolve, the
[    `dynamicRenderingUnusedAttachments`](../../../../spec/latest/chapters/features.html#features-dynamicRenderingUnusedAttachments) feature is enabled,
[VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->resolveImageView` was
not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), and the value of
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`stencilAttachmentFormat` used
to create the bound graphics pipeline was not equal to the
[VkFormat](VkFormat.html) used to create
[VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->resolveImageView`, the
value of the format **must** be `VK_FORMAT_UNDEFINED`

[](#VUID-vkCmdDrawMultiIndexedEXT-colorAttachmentCount-11871) VUID-vkCmdDrawMultiIndexedEXT-colorAttachmentCount-11871

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html) with a
[VkRenderingInfo](VkRenderingInfo.html)::`colorAttachmentCount` parameter greater than
`0` and [vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has been recorded in the render
pass instance, then for each element of the
[VkRenderingInfo](VkRenderingInfo.html)::`pColorAttachments` array with a
`resolveImageView` not equal to [VK_NULL_HANDLE](VK_NULL_HANDLE.html), the
`resolveImageView` **must** have been created with a sample count equal
to the value of `rasterizationSamples` for the bound graphics
pipeline

[](#VUID-vkCmdDrawMultiIndexedEXT-pDepthAttachment-11872) VUID-vkCmdDrawMultiIndexedEXT-pDepthAttachment-11872

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), [vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has been
recorded in the render pass instance, and
[VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->resolveImageView` was not
[VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of `rasterizationSamples` for the
bound graphics pipeline **must** be equal to the sample count used to
create [VkRenderingInfo](VkRenderingInfo.html)::`pDepthAttachment->resolveImageView`

[](#VUID-vkCmdDrawMultiIndexedEXT-pStencilAttachment-11873) VUID-vkCmdDrawMultiIndexedEXT-pStencilAttachment-11873

If the current render pass instance was begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html), [vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has been
recorded in the render pass instance,
[VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->resolveImageView` was
not [VK_NULL_HANDLE](VK_NULL_HANDLE.html), the value of `rasterizationSamples` for
the bound graphics pipeline **must** be equal to the sample count used to
create [VkRenderingInfo](VkRenderingInfo.html)::`pStencilAttachment->resolveImageView`

[](#VUID-vkCmdDrawMultiIndexedEXT-customResolve-11529) VUID-vkCmdDrawMultiIndexedEXT-customResolve-11529

If a shader object is bound to the fragment stage, the current render
pass instance was begun with [vkCmdBeginRendering](vkCmdBeginRendering.html), a fragment
density map attachment is active, and [vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html)
has been called, then the fragment shader object bound **must** have been
created with [VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`customResolve` as
`VK_TRUE`

[](#VUID-vkCmdDrawMultiIndexedEXT-customResolve-11530) VUID-vkCmdDrawMultiIndexedEXT-customResolve-11530

If a shader object is bound to the fragment stage, the current render
pass instance was begun with [vkCmdBeginRendering](vkCmdBeginRendering.html) and contains a
custom resolve, a fragment density map attachment is active, and
[vkCmdBeginCustomResolveEXT](vkCmdBeginCustomResolveEXT.html) has not yet been called, then the
fragment shader object bound **must** have been created with
[VkCustomResolveCreateInfoEXT](VkCustomResolveCreateInfoEXT.html)::`customResolve` as
`VK_FALSE`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-02712) VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-02712

If `commandBuffer` is a protected command buffer and
[`protectedNoFault`](../../../../spec/latest/chapters/devsandqueues.html#limits-protectedNoFault) is not supported,
any resource written to by the `VkPipeline` object bound to the
pipeline bind point used by this command **must** not be an unprotected
resource

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-02713) VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-02713

If `commandBuffer` is a protected command buffer and
[`protectedNoFault`](../../../../spec/latest/chapters/devsandqueues.html#limits-protectedNoFault) is not supported,
pipeline stages other than the framebuffer-space and compute stages in
the `VkPipeline` object bound to the pipeline bind point used by
this command **must** not write to any resource

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-04617) VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-04617

If any of the shader stages of the `VkPipeline` bound to the
pipeline bind point used by this command uses the
[`RayQueryKHR`](../../../../spec/latest/appendices/spirvenv.html#spirvenv-capabilities-table-RayQueryKHR)
capability, then `commandBuffer` **must** not be a protected command
buffer

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-04007) VUID-vkCmdDrawMultiIndexedEXT-None-04007

All vertex input bindings accessed via vertex input variables declared
in the vertex shader entry point’s interface **must** have either valid or
[VK_NULL_HANDLE](VK_NULL_HANDLE.html) buffers bound

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-04008) VUID-vkCmdDrawMultiIndexedEXT-None-04008

If the [`nullDescriptor`](../../../../spec/latest/chapters/features.html#features-nullDescriptor) feature is not
enabled, all vertex input bindings accessed via vertex input variables
declared in the vertex shader entry point’s interface **must** not be
[VK_NULL_HANDLE](VK_NULL_HANDLE.html)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-02721) VUID-vkCmdDrawMultiIndexedEXT-None-02721

If the [`robustBufferAccess`](../../../../spec/latest/chapters/features.html#features-robustBufferAccess) feature
is not enabled,
and that pipeline was created without enabling
`VK_PIPELINE_ROBUSTNESS_BUFFER_BEHAVIOR_ROBUST_BUFFER_ACCESS` for
`vertexInputs`,
then for a given vertex buffer binding, any attribute data fetched **must**
be entirely contained within the corresponding vertex buffer binding, as
described in [Vertex Input Description](../../../../spec/latest/chapters/fxvertex.html#fxvertex-input)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-format-10389) VUID-vkCmdDrawMultiIndexedEXT-format-10389

For each vertex attribute accessed by this command, if its
[VkVertexInputAttributeDescription](VkVertexInputAttributeDescription.html)::`format`
or [VkVertexInputAttributeDescription2EXT](VkVertexInputAttributeDescription2EXT.html)::`format`
is a [packed format](../../../../spec/latest/chapters/formats.html#formats-packed),
and the [    `legacyVertexAttributes`](../../../../spec/latest/chapters/features.html#features-legacyVertexAttributes) feature is not enabled,
the value of `attribAddress`, calculated as described in
[Vertex Input Calculation](../../../../spec/latest/chapters/fxvertex.html#fxvertex-input-address-calculation), **must**
be a multiple of the [size of the `format`](../../../../spec/latest/chapters/formats.html#formats)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-format-10390) VUID-vkCmdDrawMultiIndexedEXT-format-10390

For each vertex attribute accessed by this command, if its
[VkVertexInputAttributeDescription](VkVertexInputAttributeDescription.html)::`format`
or [VkVertexInputAttributeDescription2EXT](VkVertexInputAttributeDescription2EXT.html)::`format`
is not a [packed format](../../../../spec/latest/chapters/formats.html#formats-packed),
and either the [    `legacyVertexAttributes`](../../../../spec/latest/chapters/features.html#features-legacyVertexAttributes) feature is not enabled or `format`
has 64-bit components,
the value of `attribAddress`, calculated as described in
[Vertex Input Calculation](../../../../spec/latest/chapters/fxvertex.html#fxvertex-input-address-calculation), **must**
be a multiple of the [component size of the `format`](../../../../spec/latest/chapters/formats.html#formats)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-07842) VUID-vkCmdDrawMultiIndexedEXT-None-07842

    If
    there is a shader object bound to the `VK_SHADER_STAGE_VERTEX_BIT`
    stage
or
    the bound graphics pipeline state was created with the
    `VK_DYNAMIC_STATE_PRIMITIVE_TOPOLOGY` dynamic state enabled
    then [vkCmdSetPrimitiveTopology](vkCmdSetPrimitiveTopology.html) **must** have been called and not
    subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
    command buffer prior to this drawing command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-dynamicPrimitiveTopologyUnrestricted-07500) VUID-vkCmdDrawMultiIndexedEXT-dynamicPrimitiveTopologyUnrestricted-07500

If the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_PRIMITIVE_TOPOLOGY` dynamic state enabled
and the [    `dynamicPrimitiveTopologyUnrestricted`](../../../../spec/latest/chapters/limits.html#limits-dynamicPrimitiveTopologyUnrestricted) is `VK_FALSE`,
then the `primitiveTopology` parameter of
`vkCmdSetPrimitiveTopology` **must** be of the same
[topology class](../../../../spec/latest/chapters/drawing.html#drawing-primitive-topology-class) as the pipeline
[VkPipelineInputAssemblyStateCreateInfo](VkPipelineInputAssemblyStateCreateInfo.html)::`topology` state

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-primitiveTopology-10286) VUID-vkCmdDrawMultiIndexedEXT-primitiveTopology-10286

If a `VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` stage is bound, then
the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
`primitiveTopology` **must** be `VK_PRIMITIVE_TOPOLOGY_PATCH_LIST`
prior to this drawing command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-primitiveTopology-10747) VUID-vkCmdDrawMultiIndexedEXT-primitiveTopology-10747

If [vkCmdSetPrimitiveTopology](vkCmdSetPrimitiveTopology.html) set `primitiveTopology` to
`VK_PRIMITIVE_TOPOLOGY_PATCH_LIST` prior to this drawing command,
then a `VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` stage **must** be
bound

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-primitiveTopology-10748) VUID-vkCmdDrawMultiIndexedEXT-primitiveTopology-10748

If [vkCmdSetPrimitiveTopology](vkCmdSetPrimitiveTopology.html) set `primitiveTopology` to
`VK_PRIMITIVE_TOPOLOGY_POINT_LIST` prior to this drawing command,
the [`maintenance5`](../../../../spec/latest/chapters/features.html#features-maintenance5) feature is not
enabled,
both a `VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT` and
`VK_SHADER_STAGE_GEOMETRY_BIT` stage are not bound, then the
`Vertex` `Execution` `Model` **must** have a `PointSize` decorated
variable that is statically written to

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-pStrides-04913) VUID-vkCmdDrawMultiIndexedEXT-pStrides-04913

If the bound graphics pipeline was created with the
`VK_DYNAMIC_STATE_VERTEX_INPUT_BINDING_STRIDE` dynamic state
enabled,
but without the `VK_DYNAMIC_STATE_VERTEX_INPUT_EXT` dynamic state
enabled,
then [vkCmdBindVertexBuffers2](vkCmdBindVertexBuffers2.html) **must** have been called and not
subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
command buffer prior to this draw command, and the `pStrides`
parameter of [vkCmdBindVertexBuffers2](vkCmdBindVertexBuffers2.html) **must** not be `NULL`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-04914) VUID-vkCmdDrawMultiIndexedEXT-None-04914

    If
    there is a shader object bound to the `VK_SHADER_STAGE_VERTEX_BIT`
    stage
or
    the bound graphics pipeline state was created with the
    `VK_DYNAMIC_STATE_VERTEX_INPUT_EXT` dynamic state enabled
    then [vkCmdSetVertexInputEXT](vkCmdSetVertexInputEXT.html) **must** have been called and not
    subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
    command buffer prior to this draw command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-Input-07939) VUID-vkCmdDrawMultiIndexedEXT-Input-07939

    If
    the [    `vertexAttributeRobustness`](../../../../spec/latest/chapters/features.html#features-vertexAttributeRobustness) feature is not enabled, and
    the [`maintenance9`](../../../../spec/latest/chapters/features.html#features-maintenance9) feature is not
    enabled, and
    there is a shader object bound to the `VK_SHADER_STAGE_VERTEX_BIT`
    stage
or
    the bound graphics pipeline state was created with the
    `VK_DYNAMIC_STATE_VERTEX_INPUT_EXT` dynamic state enabled
    then all variables with the `Input` storage class decorated with
    `Location` in the `Vertex` `Execution` `Model` `OpEntryPoint`
    **must** contain a location in
    [VkVertexInputAttributeDescription2EXT](VkVertexInputAttributeDescription2EXT.html)::`location`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-Input-08734) VUID-vkCmdDrawMultiIndexedEXT-Input-08734

    If
    there is a shader object bound to the `VK_SHADER_STAGE_VERTEX_BIT`
    stage
or
    the bound graphics pipeline state was created with the
    `VK_DYNAMIC_STATE_VERTEX_INPUT_EXT` dynamic state enabled
    and either the [    `legacyVertexAttributes`](../../../../spec/latest/chapters/features.html#features-legacyVertexAttributes) feature is not enabled or the SPIR-V Type
    associated with a given `Input` variable of the corresponding
    `Location` in the `Vertex` `Execution` `Model` `OpEntryPoint` is
    64-bit,
    then the numeric type associated with all `Input` variables of the
    corresponding `Location` in the `Vertex` `Execution` `Model`
    `OpEntryPoint` **must** be the same as
    [VkVertexInputAttributeDescription2EXT](VkVertexInputAttributeDescription2EXT.html)::`format`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-format-08936) VUID-vkCmdDrawMultiIndexedEXT-format-08936

    If
    there is a shader object bound to the `VK_SHADER_STAGE_VERTEX_BIT`
    stage
or
    the bound graphics pipeline state was created with the
    `VK_DYNAMIC_STATE_VERTEX_INPUT_EXT` dynamic state enabled
    and [VkVertexInputAttributeDescription2EXT](VkVertexInputAttributeDescription2EXT.html)::`format` has a
    64-bit component, then the scalar width associated with all `Input`
    variables of the corresponding `Location` in the `Vertex`
    `Execution` `Model` `OpEntryPoint` **must** be 64-bit

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-format-08937) VUID-vkCmdDrawMultiIndexedEXT-format-08937

    If
    there is a shader object bound to the `VK_SHADER_STAGE_VERTEX_BIT`
    stage
or
    the bound graphics pipeline state was created with the
    `VK_DYNAMIC_STATE_VERTEX_INPUT_EXT` dynamic state enabled
    and the scalar width associated with a `Location` decorated
    `Input` variable in the `Vertex` `Execution` `Model`
    `OpEntryPoint` is 64-bit, then the corresponding
    [VkVertexInputAttributeDescription2EXT](VkVertexInputAttributeDescription2EXT.html)::`format` **must** have a
    64-bit component

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-09203) VUID-vkCmdDrawMultiIndexedEXT-None-09203

    If
    there is a shader object bound to the `VK_SHADER_STAGE_VERTEX_BIT`
    stage
or
    the bound graphics pipeline state was created with the
    `VK_DYNAMIC_STATE_VERTEX_INPUT_EXT` dynamic state enabled
    and [VkVertexInputAttributeDescription2EXT](VkVertexInputAttributeDescription2EXT.html)::`format` has a
    64-bit component, then all `Input` variables at the corresponding
    `Location` in the `Vertex` `Execution` `Model` `OpEntryPoint`
    **must** not use components that are not present in the format

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-04875) VUID-vkCmdDrawMultiIndexedEXT-None-04875

    If
    there is a shader object bound to the
    `VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` stage
or
    the bound graphics pipeline state was created with both a
    `VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` stage and the
    `VK_DYNAMIC_STATE_PATCH_CONTROL_POINTS_EXT` dynamic state enabled,
    and the [current value](../../../../spec/latest/chapters/pipelines.html#dynamic-state-current-value) of
    `primitiveTopology` is `VK_PRIMITIVE_TOPOLOGY_PATCH_LIST`, then
    [vkCmdSetPatchControlPointsEXT](vkCmdSetPatchControlPointsEXT.html) **must** have been called and not
    subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
    command buffer prior to this drawing command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-04879) VUID-vkCmdDrawMultiIndexedEXT-None-04879

    If
    there is a shader object bound to the `VK_SHADER_STAGE_VERTEX_BIT`
    stage
or
    the bound graphics pipeline state was created with the
    `VK_DYNAMIC_STATE_PRIMITIVE_RESTART_ENABLE` dynamic state enabled
    then [vkCmdSetPrimitiveRestartEnable](vkCmdSetPrimitiveRestartEnable.html) **must** have been called and not
    subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in the current
    command buffer prior to this drawing command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-09637) VUID-vkCmdDrawMultiIndexedEXT-None-09637

    If
    the [    `primitiveTopologyListRestart`](../../../../spec/latest/chapters/features.html#features-primitiveTopologyListRestart) feature is not enabled,
    the [input assembly](../../../../spec/latest/chapters/drawing.html#drawing-vertex-input-assembler-topology) is
    `VK_PRIMITIVE_TOPOLOGY_POINT_LIST`,
    `VK_PRIMITIVE_TOPOLOGY_LINE_LIST`,
    `VK_PRIMITIVE_TOPOLOGY_TRIANGLE_LIST`,
    `VK_PRIMITIVE_TOPOLOGY_LINE_LIST_WITH_ADJACENCY`, or
    `VK_PRIMITIVE_TOPOLOGY_TRIANGLE_LIST_WITH_ADJACENCY`,
    there is a shader object bound to the `VK_SHADER_STAGE_VERTEX_BIT`
    stage
or
    the bound graphics pipeline state was created with the
    `VK_DYNAMIC_STATE_PRIMITIVE_RESTART_ENABLE` dynamic state enabled,
    then [vkCmdSetPrimitiveRestartEnable](vkCmdSetPrimitiveRestartEnable.html) **must** be `VK_FALSE`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-10909) VUID-vkCmdDrawMultiIndexedEXT-None-10909

    If
    the [    `primitiveTopologyPatchListRestart`](../../../../spec/latest/chapters/features.html#features-primitiveTopologyPatchListRestart) feature is not enabled,
    the [input assembly](../../../../spec/latest/chapters/drawing.html#drawing-vertex-input-assembler-topology) is
    `VK_PRIMITIVE_TOPOLOGY_PATCH_LIST`,
    there is a shader object bound to the
    `VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` stage
or
    the bound graphics pipeline state was created with the
    `VK_DYNAMIC_STATE_PRIMITIVE_RESTART_ENABLE` dynamic state enabled
    then [vkCmdSetPrimitiveRestartEnable](vkCmdSetPrimitiveRestartEnable.html) **must** be `VK_FALSE`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-stage-06481) VUID-vkCmdDrawMultiIndexedEXT-stage-06481

The bound graphics pipeline **must** not have been created with the
[VkPipelineShaderStageCreateInfo](VkPipelineShaderStageCreateInfo.html)::`stage` member of any element
of [VkGraphicsPipelineCreateInfo](VkGraphicsPipelineCreateInfo.html)::`pStages` set to
`VK_SHADER_STAGE_TASK_BIT_EXT` or `VK_SHADER_STAGE_MESH_BIT_EXT`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-08885) VUID-vkCmdDrawMultiIndexedEXT-None-08885

There **must** be no shader object bound to either of the
`VK_SHADER_STAGE_TASK_BIT_EXT` or `VK_SHADER_STAGE_MESH_BIT_EXT`
stages

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-07619) VUID-vkCmdDrawMultiIndexedEXT-None-07619

If
a shader object is bound to the
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT` stage or
a graphics pipeline is bound which was created with both a
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT` stage and the
`VK_DYNAMIC_STATE_TESSELLATION_DOMAIN_ORIGIN_EXT` dynamic state
enabled, then [vkCmdSetTessellationDomainOriginEXT](vkCmdSetTessellationDomainOriginEXT.html) **must** have been
called and not subsequently [invalidated](../../../../spec/latest/chapters/pipelines.html#dynamic-state-lifetime) in
the current command buffer prior to this drawing command

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpExecutionMode-12239) VUID-vkCmdDrawMultiIndexedEXT-OpExecutionMode-12239

If a shader is bound to both the
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` and
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT` stages, and if both
stages contain an `OpExecutionMode` instruction specifying the type
of subdivision, they **must** be the same

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpExecutionMode-12240) VUID-vkCmdDrawMultiIndexedEXT-OpExecutionMode-12240

If a shader is bound to both the
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` and
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT` stages, and if both
stages contain an `OpExecutionMode` instruction specifying the
orientation of triangles, they **must** be the same

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpExecutionMode-12241) VUID-vkCmdDrawMultiIndexedEXT-OpExecutionMode-12241

If a shader is bound to both the
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` and
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT` stages, and if both
stages contain an `OpExecutionMode` instruction specifying the
segment spacing, they **must** be the same

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-OpExecutionMode-12242) VUID-vkCmdDrawMultiIndexedEXT-OpExecutionMode-12242

If a shader is bound to both the
`VK_SHADER_STAGE_TESSELLATION_CONTROL_BIT` and
`VK_SHADER_STAGE_TESSELLATION_EVALUATION_BIT` stages, and if both
stages contain an `OpExecutionMode` instruction specifying the output
patch size, they **must** be the same

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-07312) VUID-vkCmdDrawMultiIndexedEXT-None-07312

If the [`maintenance6`](../../../../spec/latest/chapters/features.html#features-maintenance6) feature is not
enabled, a
valid index buffer **must** be bound

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-pNext-09461) VUID-vkCmdDrawMultiIndexedEXT-pNext-09461

If the bound graphics pipeline state was created with
[VkPipelineVertexInputDivisorStateCreateInfo](VkPipelineVertexInputDivisorStateCreateInfo.html) in the `pNext`
chain of [VkGraphicsPipelineCreateInfo](VkGraphicsPipelineCreateInfo.html)::`pVertexInputState`,
any member of
[VkPipelineVertexInputDivisorStateCreateInfo](VkPipelineVertexInputDivisorStateCreateInfo.html)::`pVertexBindingDivisors`
has a value other than `1` in `divisor`, and
[VkPhysicalDeviceVertexAttributeDivisorProperties](VkPhysicalDeviceVertexAttributeDivisorProperties.html)::`supportsNonZeroFirstInstance`
is `VK_FALSE`, then `firstInstance` **must** be `0`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-09462) VUID-vkCmdDrawMultiIndexedEXT-None-09462

If
[shader objects](../../../../spec/latest/chapters/shaders.html#shaders-objects) are used for drawing or
the bound graphics pipeline state was created with the
`VK_DYNAMIC_STATE_VERTEX_INPUT_EXT` dynamic state enabled, any
member of the `pVertexBindingDescriptions` parameter to the
[vkCmdSetVertexInputEXT](vkCmdSetVertexInputEXT.html) call that sets this dynamic state has a
value other than `1` in `divisor`, and
[VkPhysicalDeviceVertexAttributeDivisorProperties](VkPhysicalDeviceVertexAttributeDivisorProperties.html)::`supportsNonZeroFirstInstance`
is `VK_FALSE`, then `firstInstance` **must** be `0`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-robustBufferAccess2-08798) VUID-vkCmdDrawMultiIndexedEXT-robustBufferAccess2-08798

If the [`robustBufferAccess2`](../../../../spec/latest/chapters/features.html#features-robustBufferAccess2)
feature is not enabled, (`indexSize` × (`firstIndex`
+  `indexCount`) +  `offset`) **must** be less than or
equal to the size of the bound index buffer, with `indexSize` being
based on the type specified by `indexType`, where the index buffer,
`indexType`, and `offset` are specified via
`vkCmdBindIndexBuffer`
or `vkCmdBindIndexBuffer2`.
If `vkCmdBindIndexBuffer2` is used to bind the index buffer, the
size of the bound index buffer is
[vkCmdBindIndexBuffer2](vkCmdBindIndexBuffer2.html)::`size`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-None-04937) VUID-vkCmdDrawMultiIndexedEXT-None-04937

The [`multiDraw`](../../../../spec/latest/chapters/features.html#features-multiDraw) feature **must** be enabled

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-drawCount-04939) VUID-vkCmdDrawMultiIndexedEXT-drawCount-04939

`drawCount` **must** be less than
`VkPhysicalDeviceMultiDrawPropertiesEXT`::`maxMultiDrawCount`

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-drawCount-04940) VUID-vkCmdDrawMultiIndexedEXT-drawCount-04940

If `drawCount` is greater than zero, `pIndexInfo` **must** be a
valid pointer to memory containing one or more valid instances of
[VkMultiDrawIndexedInfoEXT](VkMultiDrawIndexedInfoEXT.html) structures

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-drawCount-09629) VUID-vkCmdDrawMultiIndexedEXT-drawCount-09629

If `drawCount` is greater than `1`, `stride` **must** be a multiple
of `4` and **must** be greater than or equal to
`sizeof`(`VkMultiDrawIndexedInfoEXT`)

Valid Usage (Implicit)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-parameter) VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-parameter

 `commandBuffer` **must** be a valid [VkCommandBuffer](VkCommandBuffer.html) handle

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-pVertexOffset-parameter) VUID-vkCmdDrawMultiIndexedEXT-pVertexOffset-parameter

 If `pVertexOffset` is not `NULL`, `pVertexOffset` **must** be a valid pointer to a valid `int32_t` value

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-recording) VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-recording

 `commandBuffer` **must** be in the [recording state](../../../../spec/latest/chapters/cmdbuffers.html#commandbuffers-lifecycle)

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-cmdpool) VUID-vkCmdDrawMultiIndexedEXT-commandBuffer-cmdpool

 The `VkCommandPool` that `commandBuffer` was allocated from **must** support `VK_QUEUE_GRAPHICS_BIT` operations

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-renderpass) VUID-vkCmdDrawMultiIndexedEXT-renderpass

 This command **must** only be called inside of a render pass instance

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-suspended) VUID-vkCmdDrawMultiIndexedEXT-suspended

 This command **must** not be called between suspended render pass instances

* 
[](#VUID-vkCmdDrawMultiIndexedEXT-videocoding) VUID-vkCmdDrawMultiIndexedEXT-videocoding

 This command **must** only be called outside of a video coding scope

Host Synchronization

* 
Host access to `commandBuffer` **must** be externally synchronized

* 
Host access to the `VkCommandPool` that `commandBuffer` was allocated from **must** be externally synchronized

Command Properties
| [Command Buffer Levels](../../../../spec/latest/chapters/cmdbuffers.html#VkCommandBufferLevel) | [Render Pass Scope](../../../../spec/latest/chapters/renderpass.html#vkCmdBeginRenderPass) | [Video Coding Scope](../../../../spec/latest/chapters/videocoding.html#vkCmdBeginVideoCodingKHR) | [Supported Queue Types](../../../../spec/latest/chapters/devsandqueues.html#VkQueueFlagBits) | [Command Type](../../../../spec/latest/chapters/fundamentals.html#fundamentals-queueoperation-command-types) |
| --- | --- | --- | --- | --- |
| Primary

Secondary | Inside | Outside | VK_QUEUE_GRAPHICS_BIT | Action |

Conditional Rendering

vkCmdDrawMultiIndexedEXT is affected by [conditional rendering](../../../../spec/latest/chapters/drawing.html#drawing-conditional-rendering)

[VK_EXT_multi_draw](VK_EXT_multi_draw.html), [VkCommandBuffer](VkCommandBuffer.html), [VkMultiDrawIndexedInfoEXT](VkMultiDrawIndexedInfoEXT.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/drawing.html#vkCmdDrawMultiIndexedEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
