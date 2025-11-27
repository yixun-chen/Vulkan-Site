# vkQueueSignalReleaseImageOHOS(3)

## Metadata

- **Component**: refpages
- **Version**: latest
- **URL**: /refpages/latest/refpages/source/vkQueueSignalReleaseImageOHOS.html

## Table of Contents

- [Name](#_name)
- [C Specification](#_c_specification)
- [Parameters](#_parameters)
- [Description](#_description)
- [See Also](#_see_also)
- [Document Notes](#_document_notes)

## Content

vkQueueSignalReleaseImageOHOS - Inform the system hardware buffer that the image is released for further use

To obtain the ownership of a swapchain image, call:

// Provided by VK_OHOS_native_buffer
VkResult vkQueueSignalReleaseImageOHOS(
    VkQueue                                     queue,
    uint32_t                                    waitSemaphoreCount,
    const VkSemaphore*                          pWaitSemaphores,
    VkImage                                     image,
    int32_t*                                    pNativeFenceFd);

* 
`queue` is a handle of `VkQueue`.

* 
`waitSemaphoreCount` is the number of semaphores to wait on.

* 
`pWaitSemaphores` is a pointer to an array of [VkSemaphore](VkSemaphore.html)
handles upon which to wait before signaling the native fence.

* 
`images` is a handle of the [VkImage](VkImage.html) to be released.

* 
`pNativeFenceFd` is a pointer to either a negative value or the file
descriptor of a native fence.
A negative value indicates that the processing workflow has been
completed, and the calling party is not required to perform additional
waiting before subsequent processes.
Otherwise, a native fence will be created and be signaled when the image
is ready for release.

Valid Usage (Implicit)

* 
[](#VUID-vkQueueSignalReleaseImageOHOS-queue-parameter) VUID-vkQueueSignalReleaseImageOHOS-queue-parameter

 `queue` **must** be a valid [VkQueue](VkQueue.html) handle

* 
[](#VUID-vkQueueSignalReleaseImageOHOS-pWaitSemaphores-parameter) VUID-vkQueueSignalReleaseImageOHOS-pWaitSemaphores-parameter

 `pWaitSemaphores` **must** be a valid pointer to an array of `waitSemaphoreCount` valid [VkSemaphore](VkSemaphore.html) handles

* 
[](#VUID-vkQueueSignalReleaseImageOHOS-image-parameter) VUID-vkQueueSignalReleaseImageOHOS-image-parameter

 `image` **must** be a valid [VkImage](VkImage.html) handle

* 
[](#VUID-vkQueueSignalReleaseImageOHOS-pNativeFenceFd-parameter) VUID-vkQueueSignalReleaseImageOHOS-pNativeFenceFd-parameter

 `pNativeFenceFd` **must** be a valid pointer to an `int32_t` value

* 
[](#VUID-vkQueueSignalReleaseImageOHOS-waitSemaphoreCount-arraylength) VUID-vkQueueSignalReleaseImageOHOS-waitSemaphoreCount-arraylength

 `waitSemaphoreCount` **must** be greater than `0`

* 
[](#VUID-vkQueueSignalReleaseImageOHOS-commonparent) VUID-vkQueueSignalReleaseImageOHOS-commonparent

 Each of `image`, `queue`, and the elements of `pWaitSemaphores` **must** have been created, allocated, or retrieved from the same [VkDevice](VkDevice.html)

Command Properties
| [Command Buffer Levels](../../../../spec/latest/chapters/cmdbuffers.html#VkCommandBufferLevel) | [Render Pass Scope](../../../../spec/latest/chapters/renderpass.html#vkCmdBeginRenderPass) | [Video Coding Scope](../../../../spec/latest/chapters/videocoding.html#vkCmdBeginVideoCodingKHR) | [Supported Queue Types](../../../../spec/latest/chapters/devsandqueues.html#VkQueueFlagBits) | [Command Type](../../../../spec/latest/chapters/fundamentals.html#fundamentals-queueoperation-command-types) |
| --- | --- | --- | --- | --- |
| - | - | - | Any | - |

Return Codes

[Success](../../../../spec/latest/chapters/fundamentals.html#fundamentals-successcodes)

* 
`VK_SUCCESS`

[Failure](../../../../spec/latest/chapters/fundamentals.html#fundamentals-errorcodes)

* 
`VK_ERROR_INITIALIZATION_FAILED`

* 
`VK_ERROR_UNKNOWN`

* 
`VK_ERROR_VALIDATION_FAILED`

[VK_OHOS_native_buffer](VK_OHOS_native_buffer.html), [VkImage](VkImage.html), [VkQueue](VkQueue.html), [VkSemaphore](VkSemaphore.html)

For more information, see the [Vulkan Specification](../../../../spec/latest/chapters/resources.html#vkQueueSignalReleaseImageOHOS).

This page is extracted from the Vulkan Specification.
Fixes and changes should be made to the Specification, not directly.
