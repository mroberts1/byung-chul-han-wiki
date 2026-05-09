---
title: 3D Gaussian Splatting
aliases: [3DGS, splat rendering, Gaussian splatting]
tags: #neural-graphics #3d-gaussian-splatting #rendering
created: 2026-05-08
updated: 2026-05-08
---

## Definition

3D Gaussian Splatting (3DGS) is a rendering technique that represents 3D scenes using millions of semi-transparent, colored ellipsoids (splats) instead of triangle meshes. Each splat is a 3D Gaussian function—defined by position, covariance (scale and rotation), color (RGB), and opacity.

## Why 3DGS Matters

### Efficiency Breakthrough

Traditional 3D graphics use texture-mapped triangles, which require:
- Complex geometric data structures
- Careful lighting and material simulation
- Significant memory and compute overhead

3DGS achieves similar visual quality with:
- Simple splatting algorithm (project Gaussians, compute opacity)
- Efficient GPU implementation
- Faster render times on consumer hardware

### Natural for Neural Graphics

3DGS is the natural output format for neural graphics models:
- [[NeRF]] and diffusion models naturally produce volumetric/implicit representations
- 3DGS provides an explicit, rasterizable form of implicit neural functions
- Enables real-time interaction and editing (critical for creative tools)

### High Fidelity at Interactive Speeds

- Photogrammetry scans with millions of splats render in real-time
- Supports dynamic animation and real-time relighting
- Mobile-compatible (phones, VR headsets)

## Technical Foundation

### Splat Representation

Each splat is parameterized by:

- **Position** (μ): 3D center location
- **Covariance** (Σ): 3×3 matrix encoding scale and rotation
  - Equivalent to ellipsoid radii + orientation
- **Color** (RGB): Linear RGB values
- **Opacity** (α): 0-1 transparency

### Rendering Pipeline

**Painter's Algorithm**:

1. **Sort splats back-to-front** from camera viewpoint
   - Splats closer to camera rendered last (on top)
   - Required for correct transparency blending

2. **Project to 2D**
   - Each 3D Gaussian projects to 2D ellipse on screen
   - Covariance transforms via camera intrinsics

3. **Rasterize**
   - For each pixel in projected ellipse
   - Compute 2D Gaussian opacity value
   - Blend with framebuffer using alpha compositing ("over" operator)

### Computational Properties

- **Time per splat**: O(1) per pixel in projected area
- **Sorting**: O(n log n) where n = number of splats
- **Frame time**: Scales with number of visible splats (not scene complexity)

## Scaling to Large Worlds: Spark 2.0

The core challenge: Real scenes contain tens of millions of splats, but devices can only render 1-5M at interactive frame rates.

### Solution: Level-of-Detail (LoD) Splat Tree

[[Streaming 3DGS Worlds on the Web]] describes Spark 2.0's innovations:

**Continuous LoD**:
- Hierarchical tree where interior nodes are merged versions of children
- Root = single splat (entire scene)
- Render adaptive "tree cut" based on viewpoint
- No popping artifacts when detail level changes

**LoD Tree Traversal**:
- Priority queue selects N best splats within budget
- Algorithm runs in O(B) where B = splat budget
- Independent of total scene size
- Foveated rendering biases detail toward gaze direction

**Progressive Streaming (.RAD format)**:
- Coarse-to-fine: first 64K splats load instantly
- Spatial chunking: refine visible regions as data arrives
- Random-access: fetch any chunk in any order
- Compression: column-oriented data compresses well

**Virtual Memory**:
- Fixed GPU pool (16M splats)
- Page table manages mapping to disk chunks
- LRU eviction automatically swaps data
- Enables infinite worlds with fixed GPU memory

## Limitations

1. **Sorting dependency**: Full scene sort required each frame (bottleneck for very large scenes)
2. **View-dependent**: Tree cut changes as camera moves (recomputation overhead)
3. **No geometry for collision detection**: Splats are visual-only; simulation requires separate collision geometry
4. **Memory overhead**: Each splat stores covariance + color + opacity (larger per-element than mesh vertices)

## Future Directions

### Dynamic 3DGS
- **4DGS** (animated splats): Splats change over time (position, covariance, color)
- Applications: Video generation, dynamic world simulation

### Hybrid Systems
- Combine splatting with simulation physics
- Splats for rendering, traditional geometry for dynamics
- Enables interactive physics-based effects

### Scalability Beyond Virtual Memory
- Further optimize tree traversal
- Exploit spatial and temporal coherence across frames

## Applications

### Creative Tools
- **Marble**: Generate 3DGS worlds from text/images using [[World Models]]
- **Starspeed**: Multiplayer sci-fi game with 100M+ splat streaming
- **Dormant Memories**: Interactive scans blending captured + generated spaces

### Robotics & Simulation
- Training environments for [[Embodied AI]]
- High-fidelity visual feedback for sim-to-real transfer

### Scientific Visualization
- Molecular visualization
- Medical imaging (CT/MRI reconstruction)
- Astronomical data visualization

### Digital Twins
- High-fidelity, continuously-updated replicas
- Efficient representation of complex scenes

## Software Ecosystem

- **Spark.js**: Open-source THREE.js + WebGL2 renderer with LoD, streaming, shader graphs
- **Marble**: World Labs' generative 3DGS creation tool
- **Training**: Gaussian splatting from images/video (various open-source implementations)
- **Plugins**: COLMAP, reality capture software support

## Historical Context

**2023**: Original 3DGS paper (Kerbl et al., SIGGRAPH 2023)
- Breakthrough in neural graphics efficiency
- Made implicit neural representations rasterizable

**2024**: Spark 2.0 + related work
- LoD systems (Tiny-LoD, NanoGS)
- Progressive streaming (.RAD format)
- Mobile and web deployment

## Connected Concepts

- [[Neural Graphics]] — 3DGS as the language for spatial generation
- [[World Models]] — Marble generates 3DGS worlds
- [[3D Representations]] — Explicit, editable spatial data
- [[Streaming 3DGS Worlds on the Web]] — Technical implementation details

## Sources

- [[Streaming 3DGS Worlds on the Web]] — Spark 2.0 technical deep dive
- [[Neural Graphics]] — Role in the spatial graphics stack
