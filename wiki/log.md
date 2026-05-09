---
title: Knowledge Base Log
tags: #log
created: 2026-05-08
updated: 2026-05-08
---

# Knowledge Base Log

Chronological record of ingests, queries, compilations, and maintenance operations on the Spatial Intelligence knowledge base.

## [2026-05-08] ingest | 3D as Code + From Words to Worlds

**Source Articles**:
- [[3D as Code]] (World Labs) — 3D representations as spatial programming interface
- [[From Words to Worlds]] (Fei-Fei Li) — Spatial intelligence as AI's next frontier

**Concepts Created**:
- [[Spatial Intelligence]] — Foundational human and machine capability
- [[World Models]] — Three-pillar architecture (generative, multimodal, interactive)
- [[3D Representations]] — Structured interfaces for spatial reasoning
- [[Neural Graphics]] — Machine learning for 3D generation and rendering
- [[Embodied AI]] — Intelligence grounded through world interaction

**Key Takeaways**:
1. **3D as the interface**: Just as code mediates human-machine software collaboration, 3D representations enable human-machine spatial collaboration
2. **World models as the frontier**: AI's next major advance requires generative models with spatial consistency, multimodal inputs, and interactive simulation
3. **Applications span domains**: Creativity (film, design), robotics, scientific discovery, healthcare, education
4. **Technical stack**: 3D representations (code) + neural graphics (language) + simulation engines (chips)
5. **Embodied learning**: Robots require spatial intelligence; world models enable sim-to-real training at scale

## [2026-05-08] ingest | Streaming 3DGS Worlds on the Web

**Source Article**:
- [[Streaming 3DGS Worlds on the Web]] (World Labs / Spark team) — Technical deep dive into scaling 3DGS rendering

**Concepts Created/Updated**:
- [[3D Gaussian Splatting]] (new) — Rendering via ellipsoids; practical neural graphics implementation
- [[Neural Graphics]] (reference) — 3DGS as practical realization

**Key Insights**:
1. **3DGS as neural graphics substrate**: Natural output for NeRF/diffusion models; efficient real-time rendering
2. **Level-of-Detail splat tree**: Continuous LoD enabling adaptive detail based on viewpoint; runs in O(budget) time
3. **Progressive streaming**: .RAD format enables coarse-to-fine loading; spatial chunking prioritizes visible regions
4. **Virtual memory for splats**: GPU page table manages unlimited worlds with fixed GPU memory
5. **Production-ready scaling**: 40M+ splat worlds streaming to mobile/VR/desktop via Spark 2.0

**Architectural Coherence**:
- 3D Representations (code) ← [[3D Gaussian Splatting]] (language) → [[World Models]] (generation)
- Spark renders Marble-generated worlds
- Enables interactive 3D experiences at scale

**Status**: Core spatial AI stack visible. Ready for:
- Additional source ingestion (Marble architecture, RTFM rendering, physics integration)
- Deep dives into specific technical papers
- Application domain exploration (robotics, scientific discovery, creative tools)
