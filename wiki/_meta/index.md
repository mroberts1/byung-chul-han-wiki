---
title: Spatial Intelligence Wiki Index
type: meta
created: 2026-05-08
updated: 2026-05-08
---

# Spatial Intelligence Wiki Index

Content catalog. Every wiki page listed under its type with a one-line summary. Read this first to find relevant pages for any query.

**Last updated:** 2026-05-08 | **Total concepts:** 6 | **Total sources:** 3

---

## Concepts

### Core Concepts (Foundational Definitions)

- **[[Spatial Intelligence]]** — The cognitive ability to perceive, reason about, and interact with physical and virtual space. Foundational to human cognition, evolution, and the next frontier for AI.
- **[[World Models]]** — Generative AI systems with three core capabilities: generative (consistent worlds), multimodal (diverse inputs), interactive (action-based outputs). The enabling technology for spatial AI.
- **[[3D Representations]]** — Structured, external encodings of spatial information serving as the interface between humans and machines. Code for spatial systems.

### Implementation Concepts (Technical Depth)

- **[[Neural Graphics]]** — Machine learning approaches for generating and rendering 3D content. Plays the role of "programming language" in the spatial stack.
- **[[3D Gaussian Splatting]]** — Rendering via semi-transparent ellipsoids; efficient, practical implementation of neural graphics. Supports interactive editing, dynamic animation, and real-time performance on consumer devices.

### Application Concepts (Use Cases)

- **[[Embodied AI]]** — Intelligent systems grounded through interaction with environments. Perception-action loop as the foundation for intelligence. Applications: robotics, manipulation, human-robot collaboration.

---

## Sources

- **[[3D as Code]]** (World Labs) — Establishes 3D representations as the spatial equivalent of code; neural graphics as programming language; simulation engines as chips.
- **[[From Words to Worlds]]** (Fei-Fei Li, World Labs) — Spatial intelligence as AI's next frontier beyond language. World models as three-pillar architecture. Applications: creativity, robotics, discovery.
- **[[Streaming 3DGS Worlds on the Web]]** (World Labs / Spark team) — Technical deep dive into scaling 3DGS rendering. Level-of-Detail systems, progressive streaming (.RAD format), virtual memory for infinite worlds.

---

## Research Threads (Emerging Themes)

- **The spatial stack:** 3D representations (code) → Neural graphics (language) → Simulation engines (chips). Connects world generation (Marble) to rendering (Spark) to downstream applications.
- **Scaling neural graphics to production:** How do LoD systems, compression, streaming, and virtual memory enable massive 3D worlds on consumer devices? Tension between visual fidelity and real-time performance.
- **Multimodal world modeling:** How do systems integrate text, images, video, depth, and action into consistent spatial understanding? Where do current approaches fail?
- **Embodied learning via simulation:** World models as training data generators for robotics. Sim-to-real transfer. Breaking the data bottleneck.
- **Spatial intelligence beyond language:** What can spatial representations do that text cannot? Where do current VLMs fail at spatial reasoning?

---

## Open Questions (For Next Eval)

*Identified after ingesting 3 sources:*

- How do multimodal world models actually integrate diverse inputs, and where do they fail at physical consistency?
- What makes LoD systems and virtual memory for splats fundamentally better than naive approaches, and what are their scaling limits?
- How does spatial intelligence in embodied AI systems relate to spatial cognition in animals and humans — similar mechanisms or different solutions to same problems?
- What are the standard benchmarks for spatial reasoning in vision-language models, and where do current models systematically fail?
- How do simulation engines integrate with learned neural components in hybrid world models — what is the design space of tradeoffs?

---

## Candidates (Awaiting Sources)

*Topics frequently mentioned but not yet grounded in sources:*

- **Marble** — World Labs' multimodal world model; needs technical architecture paper/article
- **RTFM / Learned Rendering** — Real-time frame-based rendering using learned effects; needs source
- **Sim-to-real transfer** — How robots transfer from simulation to physical world; needs robotics papers
- **Spatial reasoning benchmarks** — Datasets evaluating spatial capabilities of vision-language models; needs benchmark papers
- **Digital twins** — High-precision, continuously-updated physical replicas; needs application/case study sources
- **Photogrammetry & 3D reconstruction** — Capturing real-world scenes into 3D; needs technical sources
- **Neuroscience grounding** — Place cells, grid cells, spatial memory in biological systems; needs neuro papers
- **Physics simulation & constraints** — Integration of real-time physics with generative models; needs technical sources

---

## Statistics & Trends

| Metric | Value | Trend |
|--------|-------|-------|
| Concept pages | 6 | Growing (3→6 after 3-source ingest) |
| Source summaries | 3 | Stable |
| Candidates | 8 | Growing (identified new gaps) |
| Cross-references (wikilinks) | 15+ | Strong connectivity forming |

**Evaluation Status:** Not yet run (waiting for 8-12 sources before first eval)

---

## Next Ingest Priorities

*Based on Open Questions and Candidates:*

1. **Multimodal world model architecture** — Find Marble or similar technical paper showing how different modalities integrate
2. **Sim-to-real robotics** — Ground embodied AI applications in concrete robotics research
3. **Spatial reasoning benchmarks** — Understand how spatial cognition is measured in AI systems
4. **Physics integration in neural systems** — How simulation and learning coexist in hybrid pipelines
