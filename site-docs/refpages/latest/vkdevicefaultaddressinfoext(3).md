# VkDeviceFaultAddressInfoEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkDeviceFaultAddressInfoEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Members](#_members)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkDeviceFaultAddressInfoEXT - Structure specifying GPU virtual address information

The `VkDeviceFaultAddressInfoEXT` structure is defined as:

// Provided by VK_EXT_device_fault
typedef struct VkDeviceFaultAddressInfoEXT {
    VkDeviceFaultAddressTypeEXT    addressType;
    VkDeviceAddress                reportedAddress;
    VkDeviceSize                   addressPrecision;
} VkDeviceFaultAddressInfoEXT;

* 
`addressType` is either the type of memory operation that triggered
a page fault, or the type of association between an instruction pointer
and a fault.

* 
`reportedAddress` is the GPU virtual address recorded by the device.

* 
`addressPrecision` is a power of two value that specifies how
precisely the device can report the address.

The combination of `reportedAddress` and `addressPrecision` allow
the possible range of addresses to be calculated, such that:

lower_address = (pInfo->reportedAddress & ~(pInfo->addressPrecision-1))
upper_address = (pInfo->reportedAddress |  (pInfo->addressPrecision-1))

|  | It is valid for the `reportedAddress` to contain a more precise address
| --- | --- |
than indicated by `addressPrecision`.
In this case, the value of `reportedAddress` should be treated as an
additional hint as to the value of the address that triggered the page
fault, or to the value of an instruction pointer. |

Valid Usage (Implicit)

* 
[](#VUID-VkDeviceFaultAddressInfoEXT-addressType-parameter) VUID-VkDeviceFaultAddressInfoEXT-addressType-parameter

 `addressType` **must** be a valid [VkDeviceFaultAddressTypeEXT](VkDeviceFaultAddressTypeEXT.html) value

* 
[](#VUID-VkDeviceFaultAddressInfoEXT-reportedAddress-parameter) VUID-VkDeviceFaultAddressInfoEXT-reportedAddress-parameter

 `reportedAddress` **must** be a valid `VkDeviceAddress` value

[VK_EXT_device_fault](VK_EXT_device_fault.html), `VkDeviceAddress`, [VkDeviceFaultAddressTypeEXT](VkDeviceFaultAddressTypeEXT.html), [VkDeviceFaultInfoEXT](VkDeviceFaultInfoEXT.html), `VkDeviceSize`

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/debugging.html#VkDeviceFaultAddressInfoEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
