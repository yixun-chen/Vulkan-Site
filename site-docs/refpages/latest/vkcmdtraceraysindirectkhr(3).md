# vkCmdTraceRaysIndirectKHR(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkCmdTraceRaysIndirectKHR.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkCmdTraceRaysIndirectKHR - Initialize an indirect ray tracing dispatch

To dispatch ray tracing, with some parameters sourced on the device, use:

// Provided by VK_KHR_ray_tracing_pipeline
void vkCmdTraceRaysIndirectKHR(
    VkCommandBuffer                             commandBuffer,
    const VkStridedDeviceAddressRegionKHR*      pRaygenShaderBindingTable,
    const VkStridedDeviceAddressRegionKHR*      pMissShaderBindingTable,
    const VkStridedDeviceAddressRegionKHR*      pHitShaderBindingTable,
    const VkStridedDeviceAddressRegionKHR*      pCallableShaderBindingTable,
    VkDeviceAddress                             indirectDeviceAddress);

* 
`commandBuffer` is the command buffer into which the command will be
recorded.

* 
`pRaygenShaderBindingTable` is a
[VkStridedDeviceAddressRegionKHR](VkStridedDeviceAddressRegionKHR.html) that holds the shader binding
table data for the ray generation shader stage.

* 
`pMissShaderBindingTable` is a [VkStridedDeviceAddressRegionKHR](VkStridedDeviceAddressRegionKHR.html)
that holds the shader binding table data for the miss shader stage.

* 
`pHitShaderBindingTable` is a [VkStridedDeviceAddressRegionKHR](VkStridedDeviceAddressRegionKHR.html)
that holds the shader binding table data for the hit shader stage.

* 
`pCallableShaderBindingTable` is a
[VkStridedDeviceAddressRegionKHR](VkStridedDeviceAddressRegionKHR.html) that holds the shader binding
table data for the callable shader stage.

* 
`indirectDeviceAddress` is a buffer device address which is a
pointer to a [VkTraceRaysIndirectCommandKHR](VkTraceRaysIndirectCommandKHR.html) structure containing
the trace ray parameters.

`vkCmdTraceRaysIndirectKHR` behaves similarly to [vkCmdTraceRaysKHR](vkCmdTraceRaysKHR.html)
except that the ray trace query dimensions are read by the device from
`indirectDeviceAddress` during execution.

Valid Usage

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-magFilter-04553) VUID-vkCmdTraceRaysIndirectKHR-magFilter-04553

If a [VkSampler](VkSampler.html) created with `magFilter` or `minFilter`
equal to `VK_FILTER_LINEAR`,
`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE`,
and `compareEnable` equal to `VK_FALSE` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_LINEAR_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-magFilter-09598) VUID-vkCmdTraceRaysIndirectKHR-magFilter-09598

If a [VkSampler](VkSampler.html) created with `magFilter` or `minFilter`
equal to `VK_FILTER_LINEAR` and `reductionMode` equal to either
`VK_SAMPLER_REDUCTION_MODE_MIN` or
`VK_SAMPLER_REDUCTION_MODE_MAX` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_MINMAX_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-mipmapMode-04770) VUID-vkCmdTraceRaysIndirectKHR-mipmapMode-04770

If a [VkSampler](VkSampler.html) created with `mipmapMode` equal to
`VK_SAMPLER_MIPMAP_MODE_LINEAR`,
`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE`,
and `compareEnable` equal to `VK_FALSE` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_LINEAR_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-mipmapMode-09599) VUID-vkCmdTraceRaysIndirectKHR-mipmapMode-09599

If a [VkSampler](VkSampler.html) created with `mipmapMode` equal to
`VK_SAMPLER_MIPMAP_MODE_LINEAR` and `reductionMode` equal to
either `VK_SAMPLER_REDUCTION_MODE_MIN` or
`VK_SAMPLER_REDUCTION_MODE_MAX` is used to sample a
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_MINMAX_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-unnormalizedCoordinates-09635) VUID-vkCmdTraceRaysIndirectKHR-unnormalizedCoordinates-09635

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the image view’s `levelCount` and `layerCount`
**must** be 1

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08609) VUID-vkCmdTraceRaysIndirectKHR-None-08609

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the image view’s `viewType` **must** be
`VK_IMAGE_VIEW_TYPE_1D` or `VK_IMAGE_VIEW_TYPE_2D`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08610) VUID-vkCmdTraceRaysIndirectKHR-None-08610

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the sampler **must** not be used with any of the SPIR-V
`OpImageSample*` or `OpImageSparseSample*` instructions with
`ImplicitLod`, `Dref` or `Proj` in their name

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08611) VUID-vkCmdTraceRaysIndirectKHR-None-08611

If a [VkSampler](VkSampler.html) created with `unnormalizedCoordinates` equal to
`VK_TRUE` is used to sample a [VkImageView](VkImageView.html) as a result of this
command, then the sampler **must** not be used with any of the SPIR-V
`OpImageSample*` or `OpImageSparseSample*` instructions that includes a
LOD bias or any offset values

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-06479) VUID-vkCmdTraceRaysIndirectKHR-None-06479

If a [VkImageView](VkImageView.html) is sampled with
[depth comparison](../../../../spec/latest/chapters/textures.html#textures-depth-compare-operation), the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_SAMPLED_IMAGE_DEPTH_COMPARISON_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-02691) VUID-vkCmdTraceRaysIndirectKHR-None-02691

If a [VkImageView](VkImageView.html) is accessed using atomic operations as a result
of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_STORAGE_IMAGE_ATOMIC_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-07888) VUID-vkCmdTraceRaysIndirectKHR-None-07888

If a `VK_DESCRIPTOR_TYPE_STORAGE_TEXEL_BUFFER` descriptor is
accessed using atomic operations as a result of this command, then the
storage texel buffer’s [format    features](../../../../spec/latest/chapters/resources.html#resources-buffer-view-format-features) **must** contain
`VK_FORMAT_FEATURE_STORAGE_TEXEL_BUFFER_ATOMIC_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-02692) VUID-vkCmdTraceRaysIndirectKHR-None-02692

If a [VkImageView](VkImageView.html) is sampled with `VK_FILTER_CUBIC_EXT` as a
result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_SAMPLED_IMAGE_FILTER_CUBIC_BIT_EXT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-02693) VUID-vkCmdTraceRaysIndirectKHR-None-02693

If
the [VK_EXT_filter_cubic](VK_EXT_filter_cubic.html) extension is not enabled and
any [VkImageView](VkImageView.html) is sampled with `VK_FILTER_CUBIC_EXT` as a
result of this command, it **must** not have a [VkImageViewType](VkImageViewType.html) of
`VK_IMAGE_VIEW_TYPE_3D`, `VK_IMAGE_VIEW_TYPE_CUBE`, or
`VK_IMAGE_VIEW_TYPE_CUBE_ARRAY`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-filterCubic-02694) VUID-vkCmdTraceRaysIndirectKHR-filterCubic-02694

Any [VkImageView](VkImageView.html) being sampled with `VK_FILTER_CUBIC_EXT` as a
result of this command **must** have a [VkImageViewType](VkImageViewType.html) and format
that supports cubic filtering, as specified by
[VkFilterCubicImageViewImageFormatPropertiesEXT](VkFilterCubicImageViewImageFormatPropertiesEXT.html)::`filterCubic`
returned by [vkGetPhysicalDeviceImageFormatProperties2](vkGetPhysicalDeviceImageFormatProperties2.html)

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-filterCubicMinmax-02695) VUID-vkCmdTraceRaysIndirectKHR-filterCubicMinmax-02695

Any [VkImageView](VkImageView.html) being sampled with `VK_FILTER_CUBIC_EXT` with
a reduction mode of either `VK_SAMPLER_REDUCTION_MODE_MIN` or
`VK_SAMPLER_REDUCTION_MODE_MAX` as a result of this command **must**
have a [VkImageViewType](VkImageViewType.html) and format that supports cubic filtering
together with minmax filtering, as specified by
[VkFilterCubicImageViewImageFormatPropertiesEXT](VkFilterCubicImageViewImageFormatPropertiesEXT.html)::`filterCubicMinmax`
returned by [vkGetPhysicalDeviceImageFormatProperties2](vkGetPhysicalDeviceImageFormatProperties2.html)

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-cubicRangeClamp-09212) VUID-vkCmdTraceRaysIndirectKHR-cubicRangeClamp-09212

If the [`cubicRangeClamp`](../../../../spec/latest/chapters/features.html#features-cubicRangeClamp) feature is
not enabled, then any [VkImageView](VkImageView.html) being sampled with
`VK_FILTER_CUBIC_EXT` as a result of this command **must** not have a
[VkSamplerReductionModeCreateInfo](VkSamplerReductionModeCreateInfo.html)::`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE_RANGECLAMP_QCOM`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-reductionMode-09213) VUID-vkCmdTraceRaysIndirectKHR-reductionMode-09213

Any [VkImageView](VkImageView.html) being sampled with a
[VkSamplerReductionModeCreateInfo](VkSamplerReductionModeCreateInfo.html)::`reductionMode` equal to
`VK_SAMPLER_REDUCTION_MODE_WEIGHTED_AVERAGE_RANGECLAMP_QCOM` as a
result of this command **must** sample with `VK_FILTER_CUBIC_EXT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-selectableCubicWeights-09214) VUID-vkCmdTraceRaysIndirectKHR-selectableCubicWeights-09214

If the [`selectableCubicWeights`](../../../../spec/latest/chapters/features.html#features-selectableCubicWeights)
feature is not enabled, then any [VkImageView](VkImageView.html) being sampled with
`VK_FILTER_CUBIC_EXT` as a result of this command **must** have
[VkSamplerCubicWeightsCreateInfoQCOM](VkSamplerCubicWeightsCreateInfoQCOM.html)::`cubicWeights` equal to
`VK_CUBIC_FILTER_WEIGHTS_CATMULL_ROM_QCOM`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-flags-02696) VUID-vkCmdTraceRaysIndirectKHR-flags-02696

Any [VkImage](VkImage.html) created with a [VkImageCreateInfo](VkImageCreateInfo.html)::`flags`
containing `VK_IMAGE_CREATE_CORNER_SAMPLED_BIT_NV` sampled as a
result of this command **must** only be sampled using a
[VkSamplerAddressMode](VkSamplerAddressMode.html) of
`VK_SAMPLER_ADDRESS_MODE_CLAMP_TO_EDGE`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpTypeImage-07027) VUID-vkCmdTraceRaysIndirectKHR-OpTypeImage-07027

For any [VkImageView](VkImageView.html) being written as a storage image where the
image format field of the `OpTypeImage` is `Unknown`, the view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_WRITE_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpTypeImage-07028) VUID-vkCmdTraceRaysIndirectKHR-OpTypeImage-07028

For any [VkImageView](VkImageView.html) being read as a storage image where the image
format field of the `OpTypeImage` is `Unknown`, the view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_READ_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpTypeImage-07029) VUID-vkCmdTraceRaysIndirectKHR-OpTypeImage-07029

For any [VkBufferView](VkBufferView.html) being written as a storage texel buffer where
the image format field of the `OpTypeImage` is `Unknown`, the
view’s [buffer features](../../../../spec/latest/chapters/formats.html#VkFormatProperties3) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_WRITE_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpTypeImage-07030) VUID-vkCmdTraceRaysIndirectKHR-OpTypeImage-07030

Any [VkBufferView](VkBufferView.html) being read as a storage texel buffer where the
image format field of the `OpTypeImage` is `Unknown` then the
view’s [buffer features](../../../../spec/latest/chapters/formats.html#VkFormatProperties3) **must** contain
`VK_FORMAT_FEATURE_2_STORAGE_READ_WITHOUT_FORMAT_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08600) VUID-vkCmdTraceRaysIndirectKHR-None-08600

For each set *n* that is statically used by [a bound    shader](../../../../spec/latest/chapters/shaders.html#shaders-binding), a descriptor set **must** have been bound to *n* at the same
pipeline bind point, with a [VkPipelineLayout](VkPipelineLayout.html) that is compatible
for set *n*, with the [VkPipelineLayout](VkPipelineLayout.html) used to create the current
[VkPipeline](VkPipeline.html)
or the [VkDescriptorSetLayout](VkDescriptorSetLayout.html) array used to create the current
[VkShaderEXT](VkShaderEXT.html)
, as described in [Pipeline Layout Compatibility](../../../../spec/latest/chapters/descriptorsets.html#descriptorsets-compatibility)

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08601) VUID-vkCmdTraceRaysIndirectKHR-None-08601

For each push constant that is statically used by [a    bound shader](../../../../spec/latest/chapters/shaders.html#shaders-binding), a push constant value **must** have been set for the same
pipeline bind point, with a [VkPipelineLayout](VkPipelineLayout.html) that is compatible
for push constants, with the [VkPipelineLayout](VkPipelineLayout.html) used to create the
current [VkPipeline](VkPipeline.html)
or the [VkDescriptorSetLayout](VkDescriptorSetLayout.html) array used to create the current
[VkShaderEXT](VkShaderEXT.html)
, as described in [Pipeline Layout Compatibility](../../../../spec/latest/chapters/descriptorsets.html#descriptorsets-compatibility)

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-10068) VUID-vkCmdTraceRaysIndirectKHR-None-10068

For each array of resources that is used by [a bound    shader](../../../../spec/latest/chapters/shaders.html#shaders-binding), the indices used to access members of the array **must** be less
than the descriptor count for the identified binding in the descriptor
sets used by this command

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-maintenance4-08602) VUID-vkCmdTraceRaysIndirectKHR-maintenance4-08602

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
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08114) VUID-vkCmdTraceRaysIndirectKHR-None-08114

Descriptors in each bound descriptor set, specified via
[vkCmdBindDescriptorSets](vkCmdBindDescriptorSets.html), **must** be valid as described by
[descriptor validity](../../../../spec/latest/chapters/descriptorsets.html#descriptor-validity) if they are statically used
by
the [VkPipeline](VkPipeline.html) bound to the pipeline bind point used by this
command and the bound [VkPipeline](VkPipeline.html) was not created with
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-imageLayout-00344) VUID-vkCmdTraceRaysIndirectKHR-imageLayout-00344

If an image descriptor is accessed by a shader, the [VkImageLayout](VkImageLayout.html)
**must** match the subresource accessible from the [VkImageView](VkImageView.html) as
defined by the [image layout    matching rules](../../../../spec/latest/chapters/resources.html#resources-image-layouts-matching-rule)

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08115) VUID-vkCmdTraceRaysIndirectKHR-None-08115

If the descriptors used by the [VkPipeline](VkPipeline.html) bound to the pipeline
bind point were specified via [vkCmdBindDescriptorSets](vkCmdBindDescriptorSets.html), the bound
[VkPipeline](VkPipeline.html) **must** have been created without
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08116) VUID-vkCmdTraceRaysIndirectKHR-None-08116

Descriptors in bound descriptor buffers, specified via
[vkCmdSetDescriptorBufferOffsetsEXT](vkCmdSetDescriptorBufferOffsetsEXT.html), **must** be valid if they are
dynamically used by the [VkPipeline](VkPipeline.html) bound to the pipeline bind
point used by this command and the bound [VkPipeline](VkPipeline.html) was created
with `VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08604) VUID-vkCmdTraceRaysIndirectKHR-None-08604

Descriptors in bound descriptor buffers, specified via
[vkCmdSetDescriptorBufferOffsetsEXT](vkCmdSetDescriptorBufferOffsetsEXT.html), **must** be valid if they are
dynamically used by any [VkShaderEXT](VkShaderEXT.html) bound to a stage corresponding
to the pipeline bind point used by this command

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08117) VUID-vkCmdTraceRaysIndirectKHR-None-08117

If the descriptors used by the [VkPipeline](VkPipeline.html) bound to the pipeline
bind point were specified via [vkCmdSetDescriptorBufferOffsetsEXT](vkCmdSetDescriptorBufferOffsetsEXT.html),
the bound [VkPipeline](VkPipeline.html) **must** have been created with
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08119) VUID-vkCmdTraceRaysIndirectKHR-None-08119

If a descriptor is dynamically used with a [VkPipeline](VkPipeline.html) created with
`VK_PIPELINE_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`, the descriptor
memory **must** be resident

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08605) VUID-vkCmdTraceRaysIndirectKHR-None-08605

If a descriptor is dynamically used with a [VkShaderEXT](VkShaderEXT.html) created
with a `VkDescriptorSetLayout` that was created with
`VK_DESCRIPTOR_SET_LAYOUT_CREATE_DESCRIPTOR_BUFFER_BIT_EXT`, the
descriptor memory **must** be resident

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08606) VUID-vkCmdTraceRaysIndirectKHR-None-08606

If the [`shaderObject`](../../../../spec/latest/chapters/features.html#features-shaderObject) feature is not
enabled, a
valid pipeline **must** be bound to the pipeline bind point used by this
command

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08608) VUID-vkCmdTraceRaysIndirectKHR-None-08608

If a pipeline is bound to the pipeline bind point used by this command,
there
**must** not have been any calls to dynamic state setting commands for any
state specified statically in the [VkPipeline](VkPipeline.html) object bound to the
pipeline bind point used by this command, since that pipeline was bound

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-uniformBuffers-06935) VUID-vkCmdTraceRaysIndirectKHR-uniformBuffers-06935

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
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08612) VUID-vkCmdTraceRaysIndirectKHR-None-08612

If the [`robustBufferAccess`](../../../../spec/latest/chapters/features.html#features-robustBufferAccess) feature
is not enabled, and any [VkShaderEXT](VkShaderEXT.html) bound to a stage corresponding
to the pipeline bind point used by this command accesses a uniform
buffer, it **must** not access values outside of the range of the buffer as
specified in the descriptor set bound to the same pipeline bind point

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-storageBuffers-06936) VUID-vkCmdTraceRaysIndirectKHR-storageBuffers-06936

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
[](#VUID-vkCmdTraceRaysIndirectKHR-None-08613) VUID-vkCmdTraceRaysIndirectKHR-None-08613

If the [`robustBufferAccess`](../../../../spec/latest/chapters/features.html#features-robustBufferAccess) feature
is not enabled, and any [VkShaderEXT](VkShaderEXT.html) bound to a stage corresponding
to the pipeline bind point used by this command accesses a storage
buffer, it **must** not access values outside of the range of the buffer as
specified in the descriptor set bound to the same pipeline bind point

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-02707) VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-02707

If `commandBuffer` is an unprotected command buffer and
[`protectedNoFault`](../../../../spec/latest/chapters/devsandqueues.html#limits-protectedNoFault) is not supported,
any resource accessed by [bound shaders](../../../../spec/latest/chapters/shaders.html#shaders-binding) **must** not be
a protected resource

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-viewType-07752) VUID-vkCmdTraceRaysIndirectKHR-viewType-07752

If a [VkImageView](VkImageView.html) is accessed as a result of this command, then the
image view’s `viewType` **must** match the `Dim` operand of the
`OpTypeImage` as described in [Compatibility Between SPIR-V Image Dimensions and Vulkan ImageView Types](../../../../spec/latest/appendices/spirvenv.html#spirvenv-image-dimensions)

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-format-07753) VUID-vkCmdTraceRaysIndirectKHR-format-07753

If a [VkImageView](VkImageView.html) or [VkBufferView](VkBufferView.html) is accessed as a result of
this command, then the [numeric type](../../../../spec/latest/chapters/formats.html#formats-numericformat) of the
view’s `format` and the `Sampled` `Type` operand of the
`OpTypeImage` **must** match

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageWrite-08795) VUID-vkCmdTraceRaysIndirectKHR-OpImageWrite-08795

If a [VkImageView](VkImageView.html)
created with a format other than `VK_FORMAT_A8_UNORM`
is accessed using `OpImageWrite` as a result of this command, then
the `Type` of the `Texel` operand of that instruction **must** have
at least as many components as the image view’s format

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageWrite-08796) VUID-vkCmdTraceRaysIndirectKHR-OpImageWrite-08796

If a [VkImageView](VkImageView.html) created with the format `VK_FORMAT_A8_UNORM`
is accessed using `OpImageWrite` as a result of this command, then
the `Type` of the `Texel` operand of that instruction **must** have
four components

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageWrite-04469) VUID-vkCmdTraceRaysIndirectKHR-OpImageWrite-04469

If a [VkBufferView](VkBufferView.html) is accessed using `OpImageWrite` as a result
of this command, then the `Type` of the `Texel` operand of that
instruction **must** have at least as many components as the buffer view’s
format

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-SampledType-04470) VUID-vkCmdTraceRaysIndirectKHR-SampledType-04470

If a [VkImageView](VkImageView.html) with a [VkFormat](VkFormat.html) that has a 64-bit component
width is accessed as a result of this command, the `SampledType` of
the `OpTypeImage` operand of that instruction **must** have a `Width`
of 64

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-SampledType-04471) VUID-vkCmdTraceRaysIndirectKHR-SampledType-04471

If a [VkImageView](VkImageView.html) with a [VkFormat](VkFormat.html) that has a component width
less than 64-bit is accessed as a result of this command, the
`SampledType` of the `OpTypeImage` operand of that instruction
**must** have a `Width` of 32

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-SampledType-04472) VUID-vkCmdTraceRaysIndirectKHR-SampledType-04472

If a [VkBufferView](VkBufferView.html) with a [VkFormat](VkFormat.html) that has a 64-bit
component width is accessed as a result of this command, the
`SampledType` of the `OpTypeImage` operand of that instruction
**must** have a `Width` of 64

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-SampledType-04473) VUID-vkCmdTraceRaysIndirectKHR-SampledType-04473

If a [VkBufferView](VkBufferView.html) with a [VkFormat](VkFormat.html) that has a component width
less than 64-bit is accessed as a result of this command, the
`SampledType` of the `OpTypeImage` operand of that instruction
**must** have a `Width` of 32

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-sparseImageInt64Atomics-04474) VUID-vkCmdTraceRaysIndirectKHR-sparseImageInt64Atomics-04474

If the [    `sparseImageInt64Atomics`](../../../../spec/latest/chapters/features.html#features-sparseImageInt64Atomics) feature is not enabled, [VkImage](VkImage.html)
objects created with the `VK_IMAGE_CREATE_SPARSE_RESIDENCY_BIT` flag
**must** not be accessed by atomic instructions through an `OpTypeImage`
with a `SampledType` with a `Width` of 64 by this command

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-sparseImageInt64Atomics-04475) VUID-vkCmdTraceRaysIndirectKHR-sparseImageInt64Atomics-04475

If the [    `sparseImageInt64Atomics`](../../../../spec/latest/chapters/features.html#features-sparseImageInt64Atomics) feature is not enabled, [VkBuffer](VkBuffer.html)
objects created with the `VK_BUFFER_CREATE_SPARSE_RESIDENCY_BIT`
flag **must** not be accessed by atomic instructions through an
`OpTypeImage` with a `SampledType` with a `Width` of 64 by this
command

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageWeightedSampleQCOM-06971) VUID-vkCmdTraceRaysIndirectKHR-OpImageWeightedSampleQCOM-06971

If `OpImageWeightedSampleQCOM` is used to sample a [VkImageView](VkImageView.html)
as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_WEIGHT_SAMPLED_IMAGE_BIT_QCOM`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageWeightedSampleQCOM-06972) VUID-vkCmdTraceRaysIndirectKHR-OpImageWeightedSampleQCOM-06972

If `OpImageWeightedSampleQCOM` uses a [VkImageView](VkImageView.html) as a sample
weight image as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_WEIGHT_IMAGE_BIT_QCOM`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageBoxFilterQCOM-06973) VUID-vkCmdTraceRaysIndirectKHR-OpImageBoxFilterQCOM-06973

If `OpImageBoxFilterQCOM` is used to sample a [VkImageView](VkImageView.html) as a
result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BOX_FILTER_SAMPLED_BIT_QCOM`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchSSDQCOM-06974) VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchSSDQCOM-06974

If `OpImageBlockMatchSSDQCOM` is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BLOCK_MATCHING_BIT_QCOM`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchSADQCOM-06975) VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchSADQCOM-06975

If `OpImageBlockMatchSADQCOM` is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BLOCK_MATCHING_BIT_QCOM`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchSADQCOM-06976) VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchSADQCOM-06976

If `OpImageBlockMatchSADQCOM` or OpImageBlockMatchSSDQCOM is used to
read from a reference image as result of this command, then the
specified reference coordinates **must** not fail
[integer texel coordinate    validation](../../../../spec/latest/chapters/textures.html#textures-integer-coordinate-validation)

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageWeightedSampleQCOM-06977) VUID-vkCmdTraceRaysIndirectKHR-OpImageWeightedSampleQCOM-06977

If `OpImageWeightedSampleQCOM`, `OpImageBoxFilterQCOM`,
`OpImageBlockMatchWindowSSDQCOM`,
`OpImageBlockMatchWindowSADQCOM`,
`OpImageBlockMatchGatherSSDQCOM`,
`OpImageBlockMatchGatherSADQCOM`,
`OpImageBlockMatchSSDQCOM`, or `OpImageBlockMatchSADQCOM` uses a
[VkSampler](VkSampler.html) as a result of this command, then the sampler **must** have
been created with `VK_SAMPLER_CREATE_IMAGE_PROCESSING_BIT_QCOM`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageWeightedSampleQCOM-06978) VUID-vkCmdTraceRaysIndirectKHR-OpImageWeightedSampleQCOM-06978

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
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchWindow-09215) VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchWindow-09215

If a `OpImageBlockMatchWindow*QCOM` or
`OpImageBlockMatchGather*QCOM` instruction is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
[format features](../../../../spec/latest/chapters/resources.html#resources-image-view-format-features) **must** contain
`VK_FORMAT_FEATURE_2_BLOCK_MATCHING_BIT_QCOM`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchWindow-09216) VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchWindow-09216

If a `OpImageBlockMatchWindow*QCOM` or
`OpImageBlockMatchGather*QCOM` instruction is used to read from an
[VkImageView](VkImageView.html) as a result of this command, then the image view’s
format **must** be a single-component format

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchWindow-09217) VUID-vkCmdTraceRaysIndirectKHR-OpImageBlockMatchWindow-09217

If a `OpImageBlockMatchWindow*QCOM` or
`OpImageBlockMatchGather*QCOM` read from a reference image as result
of this command, then the specified reference coordinates **must** not fail
[integer texel coordinate    validation](../../../../spec/latest/chapters/textures.html#textures-integer-coordinate-validation)

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-07288) VUID-vkCmdTraceRaysIndirectKHR-None-07288

Any shader invocation executed by this command **must**
[terminate](../../../../spec/latest/chapters/shaders.html#shaders-termination)

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-09600) VUID-vkCmdTraceRaysIndirectKHR-None-09600

If a descriptor with type equal to any of
`VK_DESCRIPTOR_TYPE_SAMPLE_WEIGHT_IMAGE_QCOM`,
`VK_DESCRIPTOR_TYPE_BLOCK_MATCH_IMAGE_QCOM`,
`VK_DESCRIPTOR_TYPE_SAMPLED_IMAGE`,
`VK_DESCRIPTOR_TYPE_STORAGE_IMAGE`, or
`VK_DESCRIPTOR_TYPE_INPUT_ATTACHMENT` is accessed as a result of
this command, all image subresources identified by that descriptor **must**
be in the image layout identified when the descriptor was written

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-10746) VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-10746

The `VkDeviceMemory` object allocated from a `VkMemoryHeap` with
the `VK_MEMORY_HEAP_TILE_MEMORY_BIT_QCOM` property that is bound to
a resource accessed as a result of this command **must** be the active
bound [bound tile memory object](../../../../spec/latest/chapters/memory.html#memory-bind-tile-memory) in
`commandBuffer`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-10678) VUID-vkCmdTraceRaysIndirectKHR-None-10678

If this command is recorded inside a [tile    shading render pass](../../../../spec/latest/chapters/renderpass.html#renderpass-tile-shading) instance, the stages corresponding to the pipeline
bind point used by this command **must** only include
`VK_SHADER_STAGE_VERTEX_BIT`, `VK_SHADER_STAGE_FRAGMENT_BIT`,
and/or `VK_SHADER_STAGE_COMPUTE_BIT`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-10679) VUID-vkCmdTraceRaysIndirectKHR-None-10679

If this command is recorded where
[per-tile execution model](../../../../spec/latest/chapters/renderpass.html#renderpass-per-tile-execution-model) is
enabled, there **must** be no access to any image while the image was be
transitioned to the
`VK_IMAGE_LAYOUT_ATTACHMENT_FEEDBACK_LOOP_OPTIMAL_EXT` layout

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pDescription-09900) VUID-vkCmdTraceRaysIndirectKHR-pDescription-09900

If a `VK_DESCRIPTOR_TYPE_TENSOR_ARM` descriptor is accessed as a
result of this command, then the underlying [VkTensorARM](VkTensorARM.html) object
**must** have been created with a
[VkTensorCreateInfoARM](VkTensorCreateInfoARM.html)::`pDescription` whose `usage` member
contained `VK_TENSOR_USAGE_SHADER_BIT_ARM`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-dimensionCount-09905) VUID-vkCmdTraceRaysIndirectKHR-dimensionCount-09905

If a `VK_DESCRIPTOR_TYPE_TENSOR_ARM` descriptor is accessed as a
result of this command, then the `Rank` of the `OpTypeTensorARM`
of the tensor resource variable **must** be equal to the
`dimensionCount` provided via
[VkTensorCreateInfoARM](VkTensorCreateInfoARM.html)::`pDescription` when creating the
underlying [VkTensorARM](VkTensorARM.html) object

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-OpTypeTensorARM-09906) VUID-vkCmdTraceRaysIndirectKHR-OpTypeTensorARM-09906

If a `VK_DESCRIPTOR_TYPE_TENSOR_ARM` descriptor is accessed as a
result of this command, then the element type of the
`OpTypeTensorARM` of the tensor resource variable **must** be
[compatible](../../../../spec/latest/appendices/spirvenv.html#spirvenv-tensor-formats) with the [VkFormat](VkFormat.html) of the
[VkTensorViewARM](VkTensorViewARM.html) used for the access

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-03429) VUID-vkCmdTraceRaysIndirectKHR-None-03429

Any shader group handle referenced by this call **must** have been queried
from the bound ray tracing pipeline

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-None-09458) VUID-vkCmdTraceRaysIndirectKHR-None-09458

If the bound ray tracing pipeline state was created with the
`VK_DYNAMIC_STATE_RAY_TRACING_PIPELINE_STACK_SIZE_KHR` dynamic state
enabled then [vkCmdSetRayTracingPipelineStackSizeKHR](vkCmdSetRayTracingPipelineStackSizeKHR.html) **must** have
been called in the current command buffer prior to this trace command

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-maxPipelineRayRecursionDepth-03679) VUID-vkCmdTraceRaysIndirectKHR-maxPipelineRayRecursionDepth-03679

This command **must** not cause a shader call instruction to be executed
from a shader invocation with a [recursion    depth](../../../../spec/latest/chapters/raytracing.html#ray-tracing-recursion-depth) greater than the value of `maxPipelineRayRecursionDepth`
used to create the bound ray tracing pipeline

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-03635) VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-03635

`commandBuffer` **must** not be a protected command buffer

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-size-04023) VUID-vkCmdTraceRaysIndirectKHR-size-04023

The `size` member of `pRayGenShaderBindingTable` **must** be equal
to its `stride` member

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pRayGenShaderBindingTable-03681) VUID-vkCmdTraceRaysIndirectKHR-pRayGenShaderBindingTable-03681

The buffer from which the `pRayGenShaderBindingTable->deviceAddress` is queried
**must** have been created with the
`VK_BUFFER_USAGE_SHADER_BINDING_TABLE_BIT_KHR` usage flag set

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pRayGenShaderBindingTable-03682) VUID-vkCmdTraceRaysIndirectKHR-pRayGenShaderBindingTable-03682

`pRayGenShaderBindingTable->deviceAddress` **must** be a multiple of
`VkPhysicalDeviceRayTracingPipelinePropertiesKHR`::`shaderGroupBaseAlignment`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pMissShaderBindingTable-03684) VUID-vkCmdTraceRaysIndirectKHR-pMissShaderBindingTable-03684

The buffer from which the `pMissShaderBindingTable->deviceAddress` is queried
**must** have been created with the
`VK_BUFFER_USAGE_SHADER_BINDING_TABLE_BIT_KHR` usage flag set

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pMissShaderBindingTable-03685) VUID-vkCmdTraceRaysIndirectKHR-pMissShaderBindingTable-03685

`pMissShaderBindingTable->deviceAddress` **must** be a multiple of
`VkPhysicalDeviceRayTracingPipelinePropertiesKHR`::`shaderGroupBaseAlignment`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-stride-03686) VUID-vkCmdTraceRaysIndirectKHR-stride-03686

`pMissShaderBindingTable->stride` **must** be a multiple of
`VkPhysicalDeviceRayTracingPipelinePropertiesKHR`::`shaderGroupHandleAlignment`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-stride-04029) VUID-vkCmdTraceRaysIndirectKHR-stride-04029

`pMissShaderBindingTable->stride` **must** be less than or equal to
`VkPhysicalDeviceRayTracingPipelinePropertiesKHR`::`maxShaderGroupStride`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pHitShaderBindingTable-03688) VUID-vkCmdTraceRaysIndirectKHR-pHitShaderBindingTable-03688

The buffer from which the `pHitShaderBindingTable->deviceAddress` is queried
**must** have been created with the
`VK_BUFFER_USAGE_SHADER_BINDING_TABLE_BIT_KHR` usage flag set

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pHitShaderBindingTable-03689) VUID-vkCmdTraceRaysIndirectKHR-pHitShaderBindingTable-03689

`pHitShaderBindingTable->deviceAddress` **must** be a multiple of
`VkPhysicalDeviceRayTracingPipelinePropertiesKHR`::`shaderGroupBaseAlignment`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-stride-03690) VUID-vkCmdTraceRaysIndirectKHR-stride-03690

`pHitShaderBindingTable->stride` **must** be a multiple of
`VkPhysicalDeviceRayTracingPipelinePropertiesKHR`::`shaderGroupHandleAlignment`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-stride-04035) VUID-vkCmdTraceRaysIndirectKHR-stride-04035

`pHitShaderBindingTable->stride` **must** be less than or equal to
`VkPhysicalDeviceRayTracingPipelinePropertiesKHR`::`maxShaderGroupStride`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pCallableShaderBindingTable-03692) VUID-vkCmdTraceRaysIndirectKHR-pCallableShaderBindingTable-03692

The buffer from which the `pCallableShaderBindingTable->deviceAddress` is queried
**must** have been created with the
`VK_BUFFER_USAGE_SHADER_BINDING_TABLE_BIT_KHR` usage flag set

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pCallableShaderBindingTable-03693) VUID-vkCmdTraceRaysIndirectKHR-pCallableShaderBindingTable-03693

`pCallableShaderBindingTable->deviceAddress` **must** be a multiple of
`VkPhysicalDeviceRayTracingPipelinePropertiesKHR`::`shaderGroupBaseAlignment`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-stride-03694) VUID-vkCmdTraceRaysIndirectKHR-stride-03694

`pCallableShaderBindingTable->stride` **must** be a multiple of
`VkPhysicalDeviceRayTracingPipelinePropertiesKHR`::`shaderGroupHandleAlignment`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-stride-04041) VUID-vkCmdTraceRaysIndirectKHR-stride-04041

`pCallableShaderBindingTable->stride` **must** be less than or equal to
`VkPhysicalDeviceRayTracingPipelinePropertiesKHR`::`maxShaderGroupStride`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-flags-03511) VUID-vkCmdTraceRaysIndirectKHR-flags-03511

If the bound ray tracing pipeline was created with `flags` that
included
`VK_PIPELINE_CREATE_RAY_TRACING_NO_NULL_MISS_SHADERS_BIT_KHR`, the
entries in the table identified by `pMissShaderBindingTable->deviceAddress`
accessed as a result of this command in order to execute a miss shader
**must** not be zero

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-flags-03512) VUID-vkCmdTraceRaysIndirectKHR-flags-03512

If the bound ray tracing pipeline was created with `flags` that
included
`VK_PIPELINE_CREATE_RAY_TRACING_NO_NULL_ANY_HIT_SHADERS_BIT_KHR`,
entries in the table identified by `pHitShaderBindingTable->deviceAddress`
accessed as a result of this command in order to execute an any-hit
shader **must** not be zero

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-flags-03513) VUID-vkCmdTraceRaysIndirectKHR-flags-03513

If the bound ray tracing pipeline was created with `flags` that
included
`VK_PIPELINE_CREATE_RAY_TRACING_NO_NULL_CLOSEST_HIT_SHADERS_BIT_KHR`,
entries in the table identified by `pHitShaderBindingTable->deviceAddress`
accessed as a result of this command in order to execute a closest hit
shader **must** not be zero

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-flags-03514) VUID-vkCmdTraceRaysIndirectKHR-flags-03514

If the bound ray tracing pipeline was created with `flags` that
included
`VK_PIPELINE_CREATE_RAY_TRACING_NO_NULL_INTERSECTION_SHADERS_BIT_KHR`,
entries in the table identified by `pHitShaderBindingTable->deviceAddress`
accessed as a result of this command in order to execute an intersection
shader **must** not be zero

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pHitShaderBindingTable-04735) VUID-vkCmdTraceRaysIndirectKHR-pHitShaderBindingTable-04735

Any non-zero hit shader group entries in the table identified by
`pHitShaderBindingTable->deviceAddress` accessed by this call from a geometry
with a `geometryType` of `VK_GEOMETRY_TYPE_TRIANGLES_KHR` **must**
have been created with
`VK_RAY_TRACING_SHADER_GROUP_TYPE_TRIANGLES_HIT_GROUP_KHR`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pHitShaderBindingTable-04736) VUID-vkCmdTraceRaysIndirectKHR-pHitShaderBindingTable-04736

Any non-zero hit shader group entries in the table identified by
`pHitShaderBindingTable->deviceAddress` accessed by this call from a geometry
with a `geometryType` of `VK_GEOMETRY_TYPE_AABBS_KHR` **must** have
been created with
`VK_RAY_TRACING_SHADER_GROUP_TYPE_PROCEDURAL_HIT_GROUP_KHR`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-indirectDeviceAddress-03633) VUID-vkCmdTraceRaysIndirectKHR-indirectDeviceAddress-03633

The buffer from which `indirectDeviceAddress` was queried **must** have
been created with the `VK_BUFFER_USAGE_INDIRECT_BUFFER_BIT` usage
flag set

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-indirectDeviceAddress-03634) VUID-vkCmdTraceRaysIndirectKHR-indirectDeviceAddress-03634

`indirectDeviceAddress` **must** be a multiple of `4`

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-indirectDeviceAddress-03636) VUID-vkCmdTraceRaysIndirectKHR-indirectDeviceAddress-03636

All device addresses between `indirectDeviceAddress` and
`indirectDeviceAddress` +  `sizeof`(`VkTraceRaysIndirectCommandKHR`) -
1 **must** be in the buffer device address range of the same buffer

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-rayTracingPipelineTraceRaysIndirect-03637) VUID-vkCmdTraceRaysIndirectKHR-rayTracingPipelineTraceRaysIndirect-03637

The [`rayTracingPipelineTraceRaysIndirect`](#features-rayTracingPipelineTraceRaysIndirect) feature **must** be enabled

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-rayTracingMotionBlurPipelineTraceRaysIndirect-04951) VUID-vkCmdTraceRaysIndirectKHR-rayTracingMotionBlurPipelineTraceRaysIndirect-04951

If the bound ray tracing pipeline was created with
`VK_PIPELINE_CREATE_RAY_TRACING_ALLOW_MOTION_BIT_NV`
`VkPhysicalDeviceRayTracingMotionBlurFeaturesNV`::`rayTracingMotionBlurPipelineTraceRaysIndirect`
feature **must** be enabled

Valid Usage (Implicit)

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-parameter) VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-parameter

 `commandBuffer` **must** be a valid [VkCommandBuffer](VkCommandBuffer.html) handle

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pRaygenShaderBindingTable-parameter) VUID-vkCmdTraceRaysIndirectKHR-pRaygenShaderBindingTable-parameter

 `pRaygenShaderBindingTable` **must** be a valid pointer to a valid [VkStridedDeviceAddressRegionKHR](VkStridedDeviceAddressRegionKHR.html) structure

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pMissShaderBindingTable-parameter) VUID-vkCmdTraceRaysIndirectKHR-pMissShaderBindingTable-parameter

 `pMissShaderBindingTable` **must** be a valid pointer to a valid [VkStridedDeviceAddressRegionKHR](VkStridedDeviceAddressRegionKHR.html) structure

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pHitShaderBindingTable-parameter) VUID-vkCmdTraceRaysIndirectKHR-pHitShaderBindingTable-parameter

 `pHitShaderBindingTable` **must** be a valid pointer to a valid [VkStridedDeviceAddressRegionKHR](VkStridedDeviceAddressRegionKHR.html) structure

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-pCallableShaderBindingTable-parameter) VUID-vkCmdTraceRaysIndirectKHR-pCallableShaderBindingTable-parameter

 `pCallableShaderBindingTable` **must** be a valid pointer to a valid [VkStridedDeviceAddressRegionKHR](VkStridedDeviceAddressRegionKHR.html) structure

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-indirectDeviceAddress-parameter) VUID-vkCmdTraceRaysIndirectKHR-indirectDeviceAddress-parameter

 `indirectDeviceAddress` **must** be a valid `VkDeviceAddress` value

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-recording) VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-recording

 `commandBuffer` **must** be in the [recording state](../../../../spec/latest/chapters/cmdbuffers.html#commandbuffers-lifecycle)

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-cmdpool) VUID-vkCmdTraceRaysIndirectKHR-commandBuffer-cmdpool

 The `VkCommandPool` that `commandBuffer` was allocated from **must** support `VK_QUEUE_COMPUTE_BIT` operations

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-renderpass) VUID-vkCmdTraceRaysIndirectKHR-renderpass

 This command **must** only be called outside of a render pass instance

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-suspended) VUID-vkCmdTraceRaysIndirectKHR-suspended

 This command **must** not be called between suspended render pass instances

* 
[](#VUID-vkCmdTraceRaysIndirectKHR-videocoding) VUID-vkCmdTraceRaysIndirectKHR-videocoding

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

Secondary | Outside | Outside | VK_QUEUE_COMPUTE_BIT | Action |

Conditional Rendering

vkCmdTraceRaysIndirectKHR is not affected by [conditional rendering](../../../../spec/latest/chapters/drawing.html#drawing-conditional-rendering)

[VK_KHR_ray_tracing_pipeline](VK_KHR_ray_tracing_pipeline.html), [VkCommandBuffer](VkCommandBuffer.html), `VkDeviceAddress`, [VkStridedDeviceAddressRegionKHR](VkStridedDeviceAddressRegionKHR.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/raytracing.html#vkCmdTraceRaysIndirectKHR).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
