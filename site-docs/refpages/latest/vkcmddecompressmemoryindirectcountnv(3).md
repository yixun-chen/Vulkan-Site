# vkCmdDecompressMemoryIndirectCountNV(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkCmdDecompressMemoryIndirectCountNV.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkCmdDecompressMemoryIndirectCountNV - Indirect decompress data between memory regions

To decompress data between one or more memory regions by specifying
decompression parameters indirectly in a buffer, call:

// Provided by VK_NV_memory_decompression
void vkCmdDecompressMemoryIndirectCountNV(
    VkCommandBuffer                             commandBuffer,
    VkDeviceAddress                             indirectCommandsAddress,
    VkDeviceAddress                             indirectCommandsCountAddress,
    uint32_t                                    stride);

* 
`commandBuffer` is the command buffer into which the command will be
recorded.

* 
`indirectCommandsAddress` is the device address containing
decompression parameters laid out as an array of
[VkDecompressMemoryRegionNV](VkDecompressMemoryRegionNV.html) structures.

* 
`indirectCommandsCountAddress` is the device address containing a
32-bit integer value specifying the decompression count.

* 
`stride` is the byte stride between successive sets of decompression
parameters located starting from `indirectCommandsAddress`.

Each region specified in `indirectCommandsAddress` is decompressed from
the source to destination region based on the specified
`decompressionMethod`.

Valid Usage

* 
[](#VUID-vkCmdDecompressMemoryIndirectCountNV-None-07692) VUID-vkCmdDecompressMemoryIndirectCountNV-None-07692

The [`memoryDecompression`](../../../../spec/latest/chapters/features.html#features-memoryDecompression) feature
**must** be enabled

* 
[](#VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsAddress-07694) VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsAddress-07694

The [VkBuffer](VkBuffer.html) that `indirectCommandsAddress` comes from **must**
have been created with the `VK_BUFFER_USAGE_INDIRECT_BUFFER_BIT`
usage flag set

* 
[](#VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsAddress-07695) VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsAddress-07695

`indirectCommandsAddress` **must** be a multiple of `4`

* 
[](#VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsCountAddress-07697) VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsCountAddress-07697

The [VkBuffer](VkBuffer.html) that `indirectCommandsCountAddress` comes from
**must** have been created with the
`VK_BUFFER_USAGE_INDIRECT_BUFFER_BIT` usage flag set

* 
[](#VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsCountAddress-07698) VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsCountAddress-07698

`indirectCommandsCountAddress` **must** be a multiple of `4`

* 
[](#VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsCountAddress-07699) VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsCountAddress-07699

The count stored in `indirectCommandsCountAddress` **must** be less
than or equal to
`VkPhysicalDeviceMemoryDecompressionPropertiesEXT`::`maxDecompressionIndirectCount`

* 
[](#VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsAddress-11794) VUID-vkCmdDecompressMemoryIndirectCountNV-indirectCommandsAddress-11794

All device addresses between `indirectCommandsAddress` and
`indirectCommandsAddress` +  (`stride` × (count
stored in `indirectCommandsCountAddress`)) - 1 **must** be in the
buffer device address range of the same buffer

* 
[](#VUID-vkCmdDecompressMemoryIndirectCountNV-stride-11770) VUID-vkCmdDecompressMemoryIndirectCountNV-stride-11770

`stride` **must** be a multiple of `4` and **must** be greater than or
equal to sizeof([VkDecompressMemoryRegionNV](VkDecompressMemoryRegionNV.html))

[VK_NV_memory_decompression](VK_NV_memory_decompression.html), [VkCommandBuffer](VkCommandBuffer.html), `VkDeviceAddress`

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/memory_decompression.html#vkCmdDecompressMemoryIndirectCountNV).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
