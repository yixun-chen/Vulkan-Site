# VkDeviceFaultVendorInfoEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkDeviceFaultVendorInfoEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkDeviceFaultVendorInfoEXT - Structure specifying vendor-specific fault information

The `VkDeviceFaultVendorInfoEXT` structure is defined as:

// Provided by VK_EXT_device_fault
typedef struct VkDeviceFaultVendorInfoEXT {
    char        description[VK_MAX_DESCRIPTION_SIZE];
    uint64_t    vendorFaultCode;
    uint64_t    vendorFaultData;
} VkDeviceFaultVendorInfoEXT;

* 
`description` is an array of `VK_MAX_DESCRIPTION_SIZE` `char`
containing a null-terminated UTF-8 string which is a human readable
description of the fault.

* 
`vendorFaultCode` is the vendor-specific fault code for this fault.

* 
`vendorFaultData` is the vendor-specific fault data associated with
this fault.

[VK_EXT_device_fault](VK_EXT_device_fault.html), [VkDeviceFaultInfoEXT](VkDeviceFaultInfoEXT.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/debugging.html#VkDeviceFaultVendorInfoEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
