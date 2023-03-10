---
title: "Aster"
date: 2020-10-19
cover: "images/aster/sunrise.png"
---

Vulkan is a pain to really toy with, and I want to add some way to allow rapid prototyping + some framework for describing render pipelines as models.
Thus I plan for Aster. The idea is to contain a core abstraction over vulkan which I'll iteratively improve to completely abstract away vulkan-specific details.

Second would be to integrate Lua based descriptions for pipelines that allow easy re-configuration and experimentation as well as live reload. This is not a Vulkan-in-Lua situation but more of just describing a pipeline as a Lua configuration file, and a renderpass as a textual representation of a framegraph.

I use:

Some C++20 features (And tl::expected for errors)
Vulkan 1.2
Some really nice libraries:  
    
- GLFW  
- GLM  
- Vulkan Memory Allocator  
- DearImGUI  
- spirv-reflect  

******

I do it in my free time so here are the features I've planned on so far:

- [x] Pipeline caching
- [x] Descriptor Set as Resource creation
- [x] Easy Buffer writing
- [x] Complete debug info + Optick profiling
- [x] Multi-GPU configuration
- [ ] Abstraction to hide Vulkan details.
- [ ] Lua integration
- [x] Atmospheric Raymarched Rendering Experiment
- [ ] Blaze re-write.

