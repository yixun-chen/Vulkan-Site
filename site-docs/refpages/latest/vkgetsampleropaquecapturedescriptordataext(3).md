# vkGetSamplerOpaqueCaptureDescriptorDataEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkGetSamplerOpaqueCaptureDescriptorDataEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkGetSamplerOpaqueCaptureDescriptorDataEXT - Get sampler opaque capture descriptor data

To get the opaque capture descriptor data for a sampler, call:

// Provided by VK_EXT_descriptor_buffer
VkResult vkGetSamplerOpaqueCaptureDescriptorDataEXT(
    VkDevice                                    device,
    const VkSamplerCaptureDescriptorDataInfoEXT* pInfo,
    void*                                       pData);

* 
`device` is the logical device that gets the data.

* 
`pInfo` is a pointer to a
[VkSamplerCaptureDescriptorDataInfoEXT](VkSamplerCaptureDescriptorDataInfoEXT.html) structure specifying the
sampler.

* 
`pData` is a pointer to an application-allocated buffer where the
data will be written.

Valid Usage

* 
[](#VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-None-08084) VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-None-08084

The [    `descriptorBufferCaptureReplay`](../../../../spec/latest/chapters/features.html#features-descriptorBufferCaptureReplay) feature **must** be enabled

* 
[](#VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-pData-08085) VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-pData-08085

`pData` **must** point to a buffer that is at least
[VkPhysicalDeviceDescriptorBufferPropertiesEXT](VkPhysicalDeviceDescriptorBufferPropertiesEXT.html)::`samplerCaptureReplayDescriptorDataSize`
bytes in size

* 
[](#VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-device-08086) VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-device-08086

If `device` was created with multiple physical devices, then the
[    `bufferDeviceAddressMultiDevice`](../../../../spec/latest/chapters/features.html#features-bufferDeviceAddressMultiDevice) feature **must** be enabled

Valid Usage (Implicit)

* 
[](#VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-device-parameter) VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-device-parameter

 `device` **must** be a valid [VkDevice](VkDevice.html) handle

* 
[](#VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-pInfo-parameter) VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-pInfo-parameter

 `pInfo` **must** be a valid pointer to a valid [VkSamplerCaptureDescriptorDataInfoEXT](VkSamplerCaptureDescriptorDataInfoEXT.html) structure

* 
[](#VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-pData-parameter) VUID-vkGetSamplerOpaqueCaptureDescriptorDataEXT-pData-parameter

 `pData` **must** be a pointer value

Return Codes

[Success](../../../../spec/latest/chapters/fundamentals.html#fundamentals-successcodes)

* 
`VK_SUCCESS`

[Failure](../../../../spec/latest/chapters/fundamentals.html#fundamentals-errorcodes)

* 
`VK_ERROR_OUT_OF_DEVICE_MEMORY`

* 
`VK_ERROR_OUT_OF_HOST_MEMORY`

* 
`VK_ERROR_UNKNOWN`

* 
`VK_ERROR_VALIDATION_FAILED`

[VK_EXT_descriptor_buffer](VK_EXT_descriptor_buffer.html), [VkDevice](VkDevice.html), [VkSamplerCaptureDescriptorDataInfoEXT](VkSamplerCaptureDescriptorDataInfoEXT.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/descriptorsets.html#vkGetSamplerOpaqueCaptureDescriptorDataEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
