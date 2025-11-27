# VkImageUsageFlags(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkImageUsageFlags.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkImageUsageFlags - Bitmask of VkImageUsageFlagBits

// Provided by VK_VERSION_1_0
typedef VkFlags VkImageUsageFlags;

`VkImageUsageFlags` is a bitmask type for setting a mask of zero or more
[VkImageUsageFlagBits](VkImageUsageFlagBits.html).

When creating a `VkImageView` one of the following
[VkImageUsageFlagBits](VkImageUsageFlagBits.html) **must** be set:

* 
`VK_IMAGE_USAGE_SAMPLED_BIT`

* 
`VK_IMAGE_USAGE_STORAGE_BIT`

* 
`VK_IMAGE_USAGE_COLOR_ATTACHMENT_BIT`

* 
`VK_IMAGE_USAGE_DEPTH_STENCIL_ATTACHMENT_BIT`

* 
`VK_IMAGE_USAGE_INPUT_ATTACHMENT_BIT`

* 
`VK_IMAGE_USAGE_TRANSIENT_ATTACHMENT_BIT`

* 
`VK_IMAGE_USAGE_FRAGMENT_SHADING_RATE_ATTACHMENT_BIT_KHR`

* 
`VK_IMAGE_USAGE_FRAGMENT_DENSITY_MAP_BIT_EXT`

* 
`VK_IMAGE_USAGE_VIDEO_DECODE_DST_BIT_KHR`

* 
`VK_IMAGE_USAGE_VIDEO_DECODE_DPB_BIT_KHR`

* 
`VK_IMAGE_USAGE_VIDEO_ENCODE_SRC_BIT_KHR`

* 
`VK_IMAGE_USAGE_VIDEO_ENCODE_DPB_BIT_KHR`

* 
`VK_IMAGE_USAGE_SAMPLE_WEIGHT_BIT_QCOM`

* 
`VK_IMAGE_USAGE_SAMPLE_BLOCK_MATCH_BIT_QCOM`

* 
`VK_IMAGE_USAGE_VIDEO_ENCODE_QUANTIZATION_DELTA_MAP_BIT_KHR`

* 
`VK_IMAGE_USAGE_VIDEO_ENCODE_EMPHASIS_MAP_BIT_KHR`

[VK_VERSION_1_0](VK_VERSION_1_0.html), `VkFlags`, [VkFramebufferAttachmentImageInfo](VkFramebufferAttachmentImageInfo.html), [VkImageCreateInfo](VkImageCreateInfo.html), [VkImageStencilUsageCreateInfo](VkImageStencilUsageCreateInfo.html), [VkImageUsageFlagBits](VkImageUsageFlagBits.html), [VkImageViewUsageCreateInfo](VkImageViewUsageCreateInfo.html), [VkPhysicalDeviceExtendedSparseAddressSpacePropertiesNV](VkPhysicalDeviceExtendedSparseAddressSpacePropertiesNV.html), [VkPhysicalDeviceImageFormatInfo2](VkPhysicalDeviceImageFormatInfo2.html), [VkPhysicalDeviceSparseImageFormatInfo2](VkPhysicalDeviceSparseImageFormatInfo2.html), [VkPhysicalDeviceVideoFormatInfoKHR](VkPhysicalDeviceVideoFormatInfoKHR.html), [VkSharedPresentSurfaceCapabilitiesKHR](VkSharedPresentSurfaceCapabilitiesKHR.html), [VkSurfaceCapabilities2EXT](VkSurfaceCapabilities2EXT.html), [VkSurfaceCapabilitiesKHR](VkSurfaceCapabilitiesKHR.html), [VkSwapchainCreateInfoKHR](VkSwapchainCreateInfoKHR.html), [VkVideoFormatPropertiesKHR](VkVideoFormatPropertiesKHR.html), [vkGetPhysicalDeviceExternalImageFormatPropertiesNV](vkGetPhysicalDeviceExternalImageFormatPropertiesNV.html), [vkGetPhysicalDeviceImageFormatProperties](vkGetPhysicalDeviceImageFormatProperties.html), [vkGetPhysicalDeviceSparseImageFormatProperties](vkGetPhysicalDeviceSparseImageFormatProperties.html), [vkGetSwapchainGrallocUsageOHOS](vkGetSwapchainGrallocUsageOHOS.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/resources.html#VkImageUsageFlags).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
