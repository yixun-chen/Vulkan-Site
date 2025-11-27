# VkDeviceFaultVendorBinaryHeaderVersionEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkDeviceFaultVendorBinaryHeaderVersionEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkDeviceFaultVendorBinaryHeaderVersionEXT - Encode vendor binary crash dump version

Possible values of the `headerVersion` value of the crash dump header
are:

// Provided by VK_EXT_device_fault
typedef enum VkDeviceFaultVendorBinaryHeaderVersionEXT {
    VK_DEVICE_FAULT_VENDOR_BINARY_HEADER_VERSION_ONE_EXT = 1,
} VkDeviceFaultVendorBinaryHeaderVersionEXT;

* 
`VK_DEVICE_FAULT_VENDOR_BINARY_HEADER_VERSION_ONE_EXT` specifies
version one of the binary crash dump header.

[VK_EXT_device_fault](VK_EXT_device_fault.html), [VkDeviceFaultVendorBinaryHeaderVersionOneEXT](VkDeviceFaultVendorBinaryHeaderVersionOneEXT.html), [vkGetDeviceFaultInfoEXT](vkGetDeviceFaultInfoEXT.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/debugging.html#VkDeviceFaultVendorBinaryHeaderVersionEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
