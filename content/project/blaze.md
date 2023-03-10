---
title: "Blaze"
date: 2019-06-06
cover: "images/blaze/csm-vis.png"
---

Blaze is my lovely little toy renderer that I wholly use as a lab-rat for new techniques and to learn computer graphics
in Vulkan.

<center><iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/gmUxLgRCC1o" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>

There are a lot of goals - lot of things to learn. Blaze get's a lot of love - but she's not the only project I'm
working on.

I use:

Some C++17 features (or did and refactored them out after my newfound love for simpler older C++ features)  
Vulkan 1.1 (Will upgrade to 1.2 once I switch to an RTX card)  
Some really nice libraries:  
    
- GLFW  
- GLM  
- Vulkan Memory Allocator  
- DearImGUI  
- spirv-reflect  
- tiny-glTF
- STB  

******

I do it in my free time so here are the features I've planned or completed on so far:

- glTF 2.0 Model loading.
    - [x] Position, Normal, UV, Materials etc.
    - [ ] Animations and Skeletons.
    - [ ] Extension support.
- Physically Based Shading.
- Forward Rendering
    - [x] Simple
    - [ ] Tiled
- Omni-directional (point) Shadow Maps
    - [x] Cubemap
    - [ ] Dual Paraboloid
- Directional Shadow Maps
    - [x] Simple Directional Shadows
    - [x] Cascaded Shadow Maps
    - [ ] Cascaded Perspective Shadow Maps
- Shader Reflection
    - [x] Pipeline Layout creation.
    - [x] Graphics Pipeline creation.
    - [ ] Easy Descriptor Set creation.
    - [ ] Compute Pipeline creation.
- Deferred Rendering
    - [x] Simple
    - [ ] Visibility Buffers
    - [ ] Tiled
- Reflections
    - [ ] Screen Space Reflection
    - [ ] Raytraced
- Ambient Occlusion
    - [x] SSAO
    - [ ] HBAO
- Post Processing
    - [x] Bloom
    - [ ] Auto-adjusing exposure
    - [ ] Filters
- Global Illumination
    - [ ] Voxel Cone Tracing
    - [ ] Precomputed Radiance Transfer
    - [ ] Raytraced 

******

## Screen Space Ambient Occlusion
![SSAO](/images/blaze/ssao.png)

## Cascaded Shadow Maps
![CSM](/images/blaze/csm-vis.png)

