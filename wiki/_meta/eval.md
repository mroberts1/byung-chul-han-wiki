---
title: AI Spatial Intelligence — Foundry Evaluation Questions
created: 2026-05-08
updated: 2026-05-08
type: meta
---

# AI Spatial Intelligence — Foundry Evaluation

Stable questions that probe vault maturity. Re-run on `/foundry-eval`. Thin/missing findings feed back into `wiki/_meta/index.md` as Open Questions and Candidates.

See `wiki/_meta/eval-usage.md` for how this document is actually used.

**Ratings:**
- `strong` — wiki has the concepts and cites ≥2 sources (ideally mixed tiers)
- `thin` — wiki has the concepts but sourcing is weak or single-source
- `missing` — wiki can't answer

Questions are grouped by what they probe. **Do not reorder or renumber existing questions** — that breaks comparability across runs. Add new questions at the bottom with the next number. To retire a question, strike it through but leave it in place.

---

## Definitional / Framing (does the wiki know what it's about?)

**Q1. What is spatial intelligence in the context of AI — how do cognitive science (Fei-Fei Li's embodied perception), graphics (3D as code), robotics (sim-to-real), and neuroscience (place cells, grid cells) framings each characterize it, and where do they genuinely conflict?**
Probes: domain scope, ability to hold competing definitions. Expected early rating: thin.

**Q2. What are the three pillars of world models — generative, multimodal, interactive — and how do current implementations (Marble, video diffusion, RL-based agents) instantiate each pillar?**
Probes: architectural clarity, ability to dissect vague claims. Expected early rating: thin.

**Q3. How does 3D representation (as code) bridge the gap between human creativity and machine reasoning — and what makes 3D a better interface than pixels alone?**
Probes: design rationale, ability to articulate tradeoffs. Expected early rating: thin.

## Technical Depth (does the wiki go deep on the implementations?)

**Q4. What are Level-of-Detail systems in 3D Gaussian Splatting, how do they scale to 40M+ splats on mobile devices, and what is the computational complexity of continuous LoD tree traversal?**
Probes: technical depth on neural graphics. Expected early rating: thin.

**Q5. How do multimodal world models handle diverse inputs (text, images, video, actions, depth) and produce physically consistent outputs — and where do current approaches fail?**
Probes: architectural understanding, ability to identify failure modes. Expected early rating: missing.

**Q6. What is the role of simulation engines (physics, collision, dynamics) in world model pipelines — and how do hybrid systems (learned perception + explicit simulation) differ from end-to-end pixel generation?**
Probes: systems thinking, ability to weigh engineering tradeoffs. Expected early rating: missing.

## Applications and Transfer (can the vault connect concepts to real use cases?)

**Q7. What are the concrete applications of spatial intelligence to robotics — sim-to-real training, human-robot collaboration, manipulation in constrained spaces — and what data bottlenecks remain?**
Probes: application grounding, knowledge of bottlenecks. Expected early rating: thin.

**Q8. How are world models used in creative tools (film, game design, architecture) — what capabilities do they unlock that traditional 3D tools cannot, and what is still out of reach?**
Probes: creative-domain understanding, ability to articulate capability boundaries. Expected early rating: thin.

**Q9. What scientific domains stand to benefit most from spatial intelligence — molecular dynamics, climate modeling, drug discovery, medical imaging — and what are the blocking challenges in each?**
Probes: breadth across domains. Expected early rating: missing.

## Benchmarks and Measurement (can the vault assess progress?)

**Q10. What are standard benchmarks for evaluating spatial reasoning in vision-language models (spatial relationships, object rotation, physics prediction, navigation)— and where do current models (GPT-4V, Gemini, Claude) fail systematically?**
Probes: measurement rigor, knowledge of failure modes. Expected early rating: missing.

**Q11. How is progress in world models measured — perceptual quality metrics (LPIPS, FID), physical consistency, interactive accuracy, human preference studies — and which metrics best predict downstream task performance?**
Probes: ability to distinguish outcome measures from capability probes. Expected early rating: missing.

## Open Problems and Grounding (does the vault acknowledge what's unknown?)

**Q12. What are the fundamental challenges in building world models — task function design, data efficiency, long-horizon consistency, alignment with human intent — and why are these harder than language modeling?**
Probes: problem formulation clarity. Expected early rating: thin.

**Q13. How does spatial intelligence in AI relate to spatial cognition in humans and animals — are we building similar mechanisms, or solving the same problems with different architectures?**
Probes: grounding in cognitive science, ability to articulate genuine unknowns. Expected early rating: missing.

---

## Latest run

*Not yet run. Run `/foundry-eval` to populate.*
