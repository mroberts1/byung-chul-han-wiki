---
title: 3D Representations
aliases: [3D models, spatial representations, geometric representations]
tags: #spatial-intelligence #3d-graphics #representations
created: 2026-05-08
updated: 2026-05-08
---

## Definition

3D representations are structured, external encodings of spatial information—the digital equivalent of the spatial world. They serve as interfaces between humans and machines for reasoning about, creating, and simulating environments.

## Role in Spatial AI

### As a Universal Interface

Just as **code** serves as the interface between humans and software systems:
- Humans can write, read, debug, and modify code
- AI can generate and reason about code
- Code integrates with compilers, runtimes, and existing infrastructure

Similarly, **3D representations** are the interface for spatial systems:
- Humans can open models in familiar tools, edit geometry, adjust constraints
- AI can generate and reason about spatial structures
- 3D outputs integrate with rendering engines, simulation systems, robotics stacks, CAD tools

### Properties of Effective 3D Representations

1. **Externalization**: State explicitly represented outside the model's weights
   - Enables inspection, validation, versioning, testing
   - Allows modification and iteration
   - Supports composable pipelines

2. **Structuredness**: Explicit, interpretable components
   - Geometry (shapes, positions, transforms)
   - Materials and appearance properties
   - Physics constraints and dynamics
   - Semantic labels and relationships

3. **Interoperability**: Works with existing software ecosystems
   - Game engines (Unity, Unreal)
   - Rendering engines (ray tracers, rasterizers)
   - Simulation systems (physics engines, GIS systems)
   - Design tools (CAD, 3D modeling software)

4. **Human Alignment**: Matches how humans think about space
   - Objects with persistent identity
   - Spatial relationships ("chair under table", "door connects rooms")
   - Natural for manipulation and editing

## Formats and Techniques

### Traditional Representations
- **Meshes**: Collections of vertices, edges, and polygons
- **Voxels**: 3D grid of discrete volumetric units
- **Point Clouds**: Discrete sets of 3D coordinates
- **CAD Formats**: Precise geometric and topological specifications

### Neural/Generative Representations
- **NeRF (Neural Radiance Fields)**: Implicit continuous function mapping 3D position + viewing direction → color and density
- **Gaussian Splatting**: Efficient rendering via 3D Gaussians with learned parameters
- **Implicit Functions**: Neural networks representing continuous surface geometry

## 3D as Spatial Code

The analogy to software code suggests evolution in 3D workflows:

**Before**: Hand-authored static assets, memory and compute constraints
- Simplified geometry
- Limited diversity
- Time-consuming iteration

**After**: Generative, dynamic, data-driven 3D
- Neural graphics enables high-fidelity generation
- Automatic updates (digital twins)
- Rapid iteration and exploration

## Digital Twins

A critical application: high-precision, continuously-updated digital mirrors of physical systems.

**Traditional approach**: Simplified, manually-maintained mockups

**Modern approach**: Dynamic, data-driven twins enabled by neural graphics
- Real-time sensor integration
- Physics-consistent simulation
- Safety-critical decision support
- Monitoring and control

## Challenges

1. **Scale**: Generating world-scale environments in memory and compute
2. **Consistency**: Maintaining geometric and physical coherence
3. **Editability**: Enabling human modification and control
4. **Integration**: Compatibility with diverse downstream systems

## Hardware Trends Enabling 3D

- **GPU evolution**: Originally for rendering triangles, now hosting large neural networks
- **Memory**: Modern GPUs with large VRAM for models and datasets
- **Specialization**: New GPU generations explicitly designed for AI + graphics workloads

These trends enable techniques like NeRF and Gaussian splatting to move from research prototypes to practical tools.

## Sources

- [[3D as Code]] — establishes 3D representations as spatial programming interface
- [[World Models]] — role of 3D in generative spatial systems
