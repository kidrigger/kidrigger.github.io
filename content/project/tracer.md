---
title: "Tracer"
date: 2018-08-31
cover: "images/tracer/cover.png"
---

Tracer is a set of Monte Carlo Ray Tracing programs that I sometimes work to better understand raytracing concepts.

There's multiple versions of it - to the point where I may just create a new 'Tracer' in a new language for fun.

Different Version of Tracer with varying degrees of completeness:

1. [C#](https://www.github.com/kidrigger/Tracer)
2. [C++](https://www.github.com/kidrigger/tracer-cpp)
3. [rust](https://www.github.com/kidrigger/tracer-rs)
4. [OpenGL/C++](https://www.github.com/kidrigger/TracerGL)

TracerGL is the **most advanced** Tracer, while the **tracer-cpp** is the one that's the one I'm actively working on.

Tracer is completely based on Peter Shirley's Raytracing in One Weekend series of mini-books. I haven't yet been able to finish everything unfortunately.
But here's to the future!

******

Features:

- Ray-Shape interactions

    - [x] Sphere
    - [x] Axis Aligned Planes
    - [x] Axis Aligned Cuboid
    - [ ] Triangles

- Acceleration Structures

    - [x] Bounding Volume Hierarchy
    - [ ] KD Trees
    - [ ] Binary Space Partition
    - [ ] Octrees

- Noise Reduction Measures

    - [ ] Blue Noise Sampling
    - [ ] Post-process Denoising

- Shaders

    - [x] Lambertian
    - [x] Dielectric
    - [x] Metallic
    - [x] Isotropic Volumes
    - [x] Emissive
    - [ ] Non-isotropic volumes
    - [ ] Mix shaders
    - [ ] BSDF to replace all