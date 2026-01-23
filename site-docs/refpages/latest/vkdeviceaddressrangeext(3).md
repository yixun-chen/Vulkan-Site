# VkDeviceAddressRangeEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkDeviceAddressRangeEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkDeviceAddressRangeEXT - Structure specifying a device address range

A device address range indicates a sized range of device memory.

// Provided by VK_EXT_descriptor_heap
typedef struct VkDeviceAddressRangeEXT {
    VkDeviceAddress    address;
    VkDeviceSize       size;
} VkDeviceAddressRangeEXT;

* 
`address` is a `VkDeviceAddress` specifying the start of the
range.

* 
`size` is a `VkDeviceSize` specifying the size of the range.

Valid Usage

* 
[](#VUID-VkDeviceAddressRangeEXT-size-11411) VUID-VkDeviceAddressRangeEXT-size-11411

If `size` is not 0, `address` **must** not be 0

* 
[](#VUID-VkDeviceAddressRangeEXT-address-11365) VUID-VkDeviceAddressRangeEXT-address-11365

The sum of `address` and `size` **must** be less than or equal to
the sum of an address retrieved from a [VkBuffer](VkBuffer.html) and the value of
[VkBufferCreateInfo](VkBufferCreateInfo.html)::`size` used to create that [VkBuffer](VkBuffer.html)

Valid Usage (Implicit)

* 
[](#VUID-VkDeviceAddressRangeEXT-address-parameter) VUID-VkDeviceAddressRangeEXT-address-parameter

 If `address` is not `0`, `address` **must** be a valid `VkDeviceAddress` value

[VK_EXT_descriptor_heap](VK_EXT_descriptor_heap.html), [VkBindHeapInfoEXT](VkBindHeapInfoEXT.html), `VkDeviceAddress`, `VkDeviceSize`, [VkResourceDescriptorDataEXT](VkResourceDescriptorDataEXT.html), [VkTexelBufferDescriptorInfoEXT](VkTexelBufferDescriptorInfoEXT.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/fundamentals.html#VkDeviceAddressRangeEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
