# VkDeviceFaultAddressTypeEXT(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/VkDeviceFaultAddressTypeEXT.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

VkDeviceFaultAddressTypeEXT - Page fault access types

Possible values of [VkDeviceFaultAddressInfoEXT](VkDeviceFaultAddressInfoEXT.html)::`addressType` are:

// Provided by VK_EXT_device_fault
typedef enum VkDeviceFaultAddressTypeEXT {
    VK_DEVICE_FAULT_ADDRESS_TYPE_NONE_EXT = 0,
    VK_DEVICE_FAULT_ADDRESS_TYPE_READ_INVALID_EXT = 1,
    VK_DEVICE_FAULT_ADDRESS_TYPE_WRITE_INVALID_EXT = 2,
    VK_DEVICE_FAULT_ADDRESS_TYPE_EXECUTE_INVALID_EXT = 3,
    VK_DEVICE_FAULT_ADDRESS_TYPE_INSTRUCTION_POINTER_UNKNOWN_EXT = 4,
    VK_DEVICE_FAULT_ADDRESS_TYPE_INSTRUCTION_POINTER_INVALID_EXT = 5,
    VK_DEVICE_FAULT_ADDRESS_TYPE_INSTRUCTION_POINTER_FAULT_EXT = 6,
} VkDeviceFaultAddressTypeEXT;

* 
`VK_DEVICE_FAULT_ADDRESS_TYPE_NONE_EXT` specifies that
[VkDeviceFaultAddressInfoEXT](VkDeviceFaultAddressInfoEXT.html) does not describe a page fault, or an
instruction address.

* 
`VK_DEVICE_FAULT_ADDRESS_TYPE_READ_INVALID_EXT` specifies that
[VkDeviceFaultAddressInfoEXT](VkDeviceFaultAddressInfoEXT.html) describes a page fault triggered by an
invalid read operation.

* 
`VK_DEVICE_FAULT_ADDRESS_TYPE_WRITE_INVALID_EXT` specifies that
[VkDeviceFaultAddressInfoEXT](VkDeviceFaultAddressInfoEXT.html) describes a page fault triggered by an
invalid write operation.

* 
`VK_DEVICE_FAULT_ADDRESS_TYPE_EXECUTE_INVALID_EXT` describes a page
fault triggered by an attempt to execute non-executable memory.

* 
`VK_DEVICE_FAULT_ADDRESS_TYPE_INSTRUCTION_POINTER_UNKNOWN_EXT`
specifies an instruction pointer value at the time the fault occurred.
This may or may not be related to a fault.

* 
`VK_DEVICE_FAULT_ADDRESS_TYPE_INSTRUCTION_POINTER_INVALID_EXT`
specifies an instruction pointer value associated with an invalid
instruction fault.

* 
`VK_DEVICE_FAULT_ADDRESS_TYPE_INSTRUCTION_POINTER_FAULT_EXT`
specifies an instruction pointer value associated with a fault.

|  | The instruction pointer values recorded may not identify the specific
| --- | --- |
instruction(s) that triggered the fault.
The relationship between the instruction pointer reported and triggering
instruction will be vendor-specific. |

[VK_EXT_device_fault](VK_EXT_device_fault.html), [VkDeviceFaultAddressInfoEXT](VkDeviceFaultAddressInfoEXT.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/debugging.html#VkDeviceFaultAddressTypeEXT).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
