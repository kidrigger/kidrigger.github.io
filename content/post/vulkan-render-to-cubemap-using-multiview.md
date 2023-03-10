---
title: "Vulkan Render to Cubemap Using Multiview"
date: 2019-11-29T21:12:00+05:30
---

While writing Blaze, and heavily referring [Sascha Willem’s Vulkan Samples](https://github.com/SaschaWillems/Vulkan), I came across the part of writing to cubemaps (PBR-IBL calculations, Shadow Mapping etc)
Sascha used a 2D framebuffer attachment to render to, and then copy to a face of the cubemap. But, back when I used [learnopengl.com](https://www.learnopengl.com) Joey de Vries used Geometry shader for Omni-directional Shadow Mapping. So I ended up researching alternatives - since I've read Geometry shaders are nasty business (they are slower in quite a few cases) and the one face at a time felt boring.

## Alternatives
- 2D framebuffer + copy to face (as in the samples)
- Geometry Shader (old wisdom from LearnOpenGL.com days)
- Multiview (What I ended up choosing)

## Why not Geometry Shader?

OpenGL allowed us to use Geometry Shader and gl_Layer to actually render to a face of the cubemap – therefore Vulkan should too. One search worth of digging later, I found an [issue](https://github.com/SaschaWillems/Vulkan/issues/50) on the repo where case against Geometry shaders was made.

Whilst digging more resources on why so, I found this [gem of an analysis](http://www.joshbarczak.com/blog/?p=667) by Joshua Barczak. It concludes that unless you’re using an Intel GPU, Geometry Shader would probably be slower (It is very workload and implementation dependent)

Now, while I could have tried and tested it (maybe sometime in the future?)
I decided to just go with the MultiView approach instead – as it was something commented on the GS issue.

## What is Multi-view?

Initially an [OpenGL OVR Extention](https://www.khronos.org/registry/OpenGL/extensions/OVR/OVR_multiview.txt), Multi View allows reducing draw calls by allowing multiple layers of a Framebuffer Attachment to be written to from a single draw call.

Of course, the aim of Multi View is to be used for multi-Viewport rendering (VR / Stereoscopic). But since multiview has no restrictions on number of layers on the attachment, we can just as well write to the Cubemap.

## How to Multi-view?

I’m using a 2D attachment RenderPass and Pipeline as the starting point.

### 1. Enabling the Extension

Simply enable the VK_KHR_multiview (VK_KHR_MULTIVIEW_EXTENSION_NAME) extension while creating the Logical Device.

### 2. Creating a Multi-View RenderPass

Creating a Multi-View RenderPass only requires a slight addition to the existing VkRenderPassCreateInfo.
The `pNext` field needs to be set to a `VkRenderPassMultiviewCreateInfo`

```cpp
VkRenderPassMultiviewCreateInfo createInfo{};
createInfo.sType = VK_STRUCTURE_TYPE_RENDER_PASS_MULTIVIEW_CREATE_INFO;
createInfo.subpassCount = 1;
createInfo.pViewMasks = &viewMask;
createInfo.correlationMaskCount = 1;
createInfo.pCorrelationMasks = &correlationMask;
```

#### Quick Explanation:

1. `subpassCount` is not only the number of subpasses in the render pass but also the number of view masks in `pViewMasks`
2. Each view mask is an unsigned int, where ith least significant bit denotes the layer number. 0b0011 means write to layer 0 and 1.
3. For our cubemap, we will have only one subpass, writing to all the faces (viewMask = 0b00111111)
4. According to the spec, correlation masks denote which views have high spatial coherence – since our cubemaps will be ideally facing 6 completely different directions – I think they should be left to null (I’ll update this if I’m wrong)

### 3 Attaching the Cubemap to the Framebuffer

Ideally the simplest part – standard framebuffer, just set createInfo.layers = 6

### 4 Views Uniform Buffer

For each face of the cubemap, you will need a View. This should be easy. Just create the 6 view matrices and put them on a uniform buffer.

### 5 Shaders

The fragment shader does not change for this. The only difference is in the vertex shader.
Instead of having one view matrix coming in, we would now index a view matrix from the uniform buffer using the gl_ViewIndex variable.

## That’s it!

With all these changes, instead of a simple 2D attachment, you can now attach a cubemap and get it running.

## Perf?
Performance comparison between separate passes vs multiview is in the graph below.

![performance-compare](/images/vk-cubemap/perf.png)

Consistently Multi-View outperforms having separate render passes. I would guess that the lack of copy operations and draw submits should save the time.

