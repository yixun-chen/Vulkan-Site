# vkCmdEndRenderPass(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkCmdEndRenderPass.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkCmdEndRenderPass - End the current render pass

To record a command to end a render pass instance after recording the
commands for the last subpass, call:

|  | This functionality is superseded by [Vulkan Version 1.2](../../../../spec/latest/appendices/versions.html#versions-1.2). See [Legacy Functionality](../../../../spec/latest/appendices/legacy.html#legacy-renderpass2) for more information. |
| --- | --- |

// Provided by VK_VERSION_1_0
void vkCmdEndRenderPass(
    VkCommandBuffer                             commandBuffer);

* 
`commandBuffer` is the command buffer in which to end the current
render pass instance.

Ending a render pass instance performs any multisample resolve operations on
the final subpass.

Valid Usage

* 
[](#VUID-vkCmdEndRenderPass-None-00910) VUID-vkCmdEndRenderPass-None-00910

The current subpass index **must** be equal to the number of subpasses in
the render pass minus one

* 
[](#VUID-vkCmdEndRenderPass-None-02351) VUID-vkCmdEndRenderPass-None-02351

This command **must** not be recorded when transform feedback is active

* 
[](#VUID-vkCmdEndRenderPass-None-06170) VUID-vkCmdEndRenderPass-None-06170

The current render pass instance **must** not have been begun with
[vkCmdBeginRendering](vkCmdBeginRendering.html)

* 
[](#VUID-vkCmdEndRenderPass-None-07004) VUID-vkCmdEndRenderPass-None-07004

If `vkCmdBeginQuery`* was called within a subpass of the render
pass, the corresponding `vkCmdEndQuery`* **must** have been called
subsequently within the same subpass

* 
[](#VUID-vkCmdEndRenderPass-None-10653) VUID-vkCmdEndRenderPass-None-10653

This command **must** not be recorded when
[per-tile execution model](../../../../spec/latest/chapters/renderpass.html#renderpass-per-tile-execution-model) is
enabled

Valid Usage (Implicit)

* 
[](#VUID-vkCmdEndRenderPass-commandBuffer-parameter) VUID-vkCmdEndRenderPass-commandBuffer-parameter

 `commandBuffer` **must** be a valid [VkCommandBuffer](VkCommandBuffer.html) handle

* 
[](#VUID-vkCmdEndRenderPass-commandBuffer-recording) VUID-vkCmdEndRenderPass-commandBuffer-recording

 `commandBuffer` **must** be in the [recording state](../../../../spec/latest/chapters/cmdbuffers.html#commandbuffers-lifecycle)

* 
[](#VUID-vkCmdEndRenderPass-commandBuffer-cmdpool) VUID-vkCmdEndRenderPass-commandBuffer-cmdpool

 The `VkCommandPool` that `commandBuffer` was allocated from **must** support `VK_QUEUE_GRAPHICS_BIT` operations

* 
[](#VUID-vkCmdEndRenderPass-renderpass) VUID-vkCmdEndRenderPass-renderpass

 This command **must** only be called inside of a render pass instance

* 
[](#VUID-vkCmdEndRenderPass-suspended) VUID-vkCmdEndRenderPass-suspended

 This command **must** not be called between suspended render pass instances

* 
[](#VUID-vkCmdEndRenderPass-videocoding) VUID-vkCmdEndRenderPass-videocoding

 This command **must** only be called outside of a video coding scope

* 
[](#VUID-vkCmdEndRenderPass-bufferlevel) VUID-vkCmdEndRenderPass-bufferlevel

 `commandBuffer` **must** be a primary `VkCommandBuffer`

Host Synchronization

* 
Host access to `commandBuffer` **must** be externally synchronized

* 
Host access to the `VkCommandPool` that `commandBuffer` was allocated from **must** be externally synchronized

Command Properties
| [Command Buffer Levels](../../../../spec/latest/chapters/cmdbuffers.html#VkCommandBufferLevel) | [Render Pass Scope](../../../../spec/latest/chapters/renderpass.html#vkCmdBeginRenderPass) | [Video Coding Scope](../../../../spec/latest/chapters/videocoding.html#vkCmdBeginVideoCodingKHR) | [Supported Queue Types](../../../../spec/latest/chapters/devsandqueues.html#VkQueueFlagBits) | [Command Type](../../../../spec/latest/chapters/fundamentals.html#fundamentals-queueoperation-command-types) |
| --- | --- | --- | --- | --- |
| Primary | Inside | Outside | VK_QUEUE_GRAPHICS_BIT | Action

State

Synchronization |

Conditional Rendering

vkCmdEndRenderPass is not affected by [conditional rendering](../../../../spec/latest/chapters/drawing.html#drawing-conditional-rendering)

[VK_VERSION_1_0](VK_VERSION_1_0.html), [VkCommandBuffer](VkCommandBuffer.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/renderpass.html#vkCmdEndRenderPass).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
