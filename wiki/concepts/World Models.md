---
title: World Models
aliases: [generative world models, spatial world models]
tags: #spatial-intelligence #world-models #generative-models
created: 2026-05-08
updated: 2026-05-08
---

## Definition

A world model is a generative AI system capable of understanding, reasoning about, and generating consistent simulations of physical or virtual environments. Unlike language models that operate sequentially on text, world models must maintain coherent representations of spatial, geometric, physical, and dynamic properties.

## Three Core Capabilities (Fei-Fei Li)

### 1. Generative
- Generate worlds with perceptual, geometric, and physical consistency
- Produce diverse environments following semantic instructions
- Maintain geometric and physical coherence (not just visual plausibility)
- Represent explicit, observable state (not just implicit latent vectors)
- History-aware: past states inform understanding of present state

### 2. Multimodal
- Accept diverse input modalities: images, video, text instructions, gestures, actions
- Predict or generate complete world states from partial information
- Blend visual fidelity with semantic understanding
- Enable both human and machine communication about world state

### 3. Interactive
- Predict next world states based on agent actions
- Given action + optional goal, output physically and semantically consistent next state
- Support agent planning and action refinement
- Maintain consistency with world's physical laws and dynamics

## Technical Dimensions

### Representation
- **Implicit vs. Explicit**: whether world structure is encoded in learned weights or externalized as geometric data
- **Pixel-based vs. Structured**: pixel generation (entangled state/dynamics) vs. 3D representations (factorized components)
- Current trend: structured 3D output enables composability and external tool integration

### Training Signal
- Challenge: no simple universal task function like "next-token prediction" for LLMs
- Must honor geometry, physics, and dynamics constraints
- Requires multi-scale loss functions capturing perceptual, geometric, and physical accuracy

### Data Sources
- Internet-scale images and videos (abundant but 2D)
- Synthetic simulation data (geometry and physics guaranteed)
- Sensor data (depth, tactile, thermal)
- Human demonstrations
- Challenge: extracting 3D information from 2D signals at scale

### Architecture
- Current approaches: MLLMs and diffusion models (tokenize to 1D/2D sequences)
- Emerging: 3D/4D-aware tokenization, spatial memory systems
- Example: RTFM (real-time frame-based model) uses spatially-grounded frames as memory

## The Simulation Stack Analogy

By analogy to the software stack:

- **Code** ↔ **3D Representations** (durable abstractions)
- **Programming Language** ↔ **Neural Graphics** (NeRF, Gaussian splatting)
- **Chips/Hardware** ↔ **Simulation Engines** (physics, collision, rendering)

This architecture ensures:
- Inspectability and debuggability
- Composability with external tools
- Persistence and reproducibility
- Human and machine interpretability

## Applications

- **Creativity**: Generate explorable 3D environments for film, games, architecture
- **Robotics**: Simulation-based training data, behavioral cloning
- **Scientific Discovery**: Molecular simulation, climate modeling, material discovery
- **Healthcare**: Drug discovery, diagnostic imaging, surgical simulation
- **Education**: Immersive learning experiences

## Challenges

1. **Task Function**: No elegant universal objective like next-token prediction
2. **Data Extraction**: Learning 3D structure from 2D images and video
3. **Architecture**: Moving beyond sequential tokenization
4. **Scale**: Training world models at internet scale
5. **Consistency**: Maintaining physical and semantic consistency over long horizons

## Comparison to Current AI

| Aspect | LLMs | World Models |
|--------|------|--------------|
| Input | Text (1D sequence) | Multimodal spatial data |
| Output | Next token | Next world state |
| Constraints | Linguistic coherence | Geometric, physical, dynamic consistency |
| Persistence | Context window limited | Persistent world state |
| Interaction | Stateless generation | State + action → next state |

## Sources

- [[3D as Code]] — world models as spatial programming systems
- [[From Words to Worlds]] — Fei-Fei Li's vision and technical framing
