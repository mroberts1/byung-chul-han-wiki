# Instructions for Claude (and other agents)

This file is the authoritative governance document for the **Spatial Intelligence** Foundry vault. Read it in full before performing any operation on this vault. The rules below are non-negotiable.

Before acting, also read:
1. `wiki/_meta/index.md` — catalog of pages, keywords, open questions, candidates
2. `wiki/_meta/log.md` — last 20-30 entries for recent vault state
3. `wiki/_meta/eval.md` — stable evaluation questions (read only; don't answer unless running `/foundry-eval`)
4. `wiki/_meta/eval-usage.md` — explains the eval loop

If you're unsure, ask the user before doing anything destructive or structural.

---

This is an autonomous knowledge vault maintained by Claude. It follows the Karpathy wiki pattern: raw sources are ingested and compiled into a wiki of concepts, connections, and open questions. This file is the single source of truth for how Claude operates inside it.

**v2 changes from v1:** adds source tiering, conflict handling, freshness/re-ingest, pruning, voice anchor, query→concept promotion, cross-wiki linking, and an eval loop. See `## Changes from v1` at the bottom for a concise diff.

---

## Voice anchor

This vault tracks AI spatial intelligence as a technical and industrial frontier: world models, neural graphics, 3D representations, embodied AI, and the computational stack that makes machines reason about space. Write like someone who takes both the engineering depth (rendering pipelines, LoD systems, sim-to-real transfer, multimodal architectures) and the broader paradigm claims seriously — skeptical of hype but not dismissive of genuine technical novelty. Avoid: reducing spatial intelligence to navigation benchmarks, conflating marketing claims with architectural substance, breathless capability announcements without grounding in what the systems actually do. The productive tension in this domain is between what current models demonstrably achieve and what the spatial intelligence framing promises — hold that gap open rather than closing it prematurely.

---

## Companion vault (optional)

If you keep a personal vault (a commonplace, Zettelkasten, or notes folder), you can link it alongside this one. The contract:

- **Your vault** — read-only for Claude. Never write, edit, move, or delete anything there. Cross-link into it with `[[YourVault/Path/Note Title]]` style references when a Foundry note is informed by your writing.
- **Foundry** — Claude writes, maintains, reorganises. You read, query, and occasionally correct.

One-way read, cross-linkable. That's the contract.

## Sibling vaults

- ~/generative-art — most relevant sibling; neural graphics has direct lineage in generative/computational art history

Other vaults (~/interasia-pop, ~/tiwchh) are not directly linked — cross-reference only if a specific concept genuinely bridges domains.

Sibling vaults are **read-only** to Claude from this vault's perspective. Cross-link with `[[SiblingVaultName/wiki/Concept Title]]`. Never edit a sibling vault from inside another. Use a concept's home vault as the canonical location; all others link inward.

---

## Scope

This vault covers **AI spatial intelligence**: the technical systems, architectures, representations, and applications that constitute the current frontier in machines reasoning about, generating, and interacting with 3D space. Core threads:

- **World models** — generative, multimodal, interactive systems that simulate physical and virtual environments
- **Neural graphics** — ML approaches to generating and rendering 3D content (NeRF, 3DGS, neural rendering)
- **3D representations** — structured encodings of spatial information (explicit vs. implicit, editable vs. learned)
- **Embodied AI** — intelligent systems grounded through physical or simulated environmental interaction
- **Spatial reasoning in LLMs/VLMs** — where current models succeed and fail at spatial tasks

**Cognitive science and neuroscience** (place cells, cognitive maps, Gibson, Merleau-Ponty) are in scope only as grounding or contrast — when they illuminate what AI systems are or aren't doing, or when a source explicitly bridges the two domains. They are not a primary research thread. If that thread grows to warrant its own vault, split it then.

---

## Directory structure

| Directory | Purpose | Who writes |
|---|---|---|
| `inbox/` | Staging for unprocessed drops (PDFs, URLs, screenshots, pasted text) | You drop, Claude clears |
| `raw/` | Raw articles clipped via Obsidian Web Clipper or pasted text | You drop; Claude reads but does not restructure |
| `sources/` | Immutable atomic source notes — one per article/paper/transcript | Claude on ingest; minor edits only after creation |
| `wiki/` | LLM-maintained pages: concepts, sources, indexes, log | Claude maintains |
| `wiki/_archive/` | Superseded or pruned content, kept for provenance | Claude on prune; never deleted |

**Note on current structure:** The MacBook-side ingest established wiki/concepts/, wiki/sources/, and wiki/indexes/ subdirectories with Title Case filenames. This is the active convention for this vault. See `## File naming` below.

Special files in `wiki/_meta/`:
- **`index.md`** — catalog of every page, keyword glossary, research threads, open questions, candidates. Claude reads this first when answering a query. Updated on every operation.
- **`log.md`** — append-only chronological record. Each entry: `## [YYYY-MM-DD] operation | Title`. Never rewritten, only appended.
- **`health.md`** — lint dashboard. Overwritten each `/foundry-lint` run.
- **`eval.md`** — evaluation questions and latest answers. Overwritten each `/foundry-eval` run.

---

## File naming

- **Source notes** (`wiki/sources/`): Title Case — `Marble - A Multimodal World Model.md`, `From Words to Worlds.md`
- **Concept articles** (`wiki/concepts/`): Title Case — `3D Gaussian Splatting.md`, `World Models.md`, `Embodied AI.md`
- **Index files** (`wiki/indexes/`): Title Case — `Master Index.md`
- **Queries**: `YYYY-MM-DD-slug.md` in `wiki/concepts/` or a dedicated `wiki/queries/` dir
- **Archived**: original name preserved, moved into `wiki/_archive/YYYY-MM/`
- No emoji, no unicode hacks, no date prefixes in titles (dates go in front-matter)

---

## Front-matter

YAML front-matter block (as used by Obsidian). Blank line then `---` then body.

### Source notes (`wiki/sources/`)

```yaml
---
title: Article or Paper Title
source_type: article | paper | repo | dataset
url: https://...
authors: Name, Name
date: YYYY
tags: [#spatial-intelligence, #world-models]
tier: peer-reviewed | primary | journalism | secondary | informal
last_verified: YYYY-MM-DD
superseded_by:
---
```

`tier` is mandatory and picks exactly one of:

| Tier | When to use |
|---|---|
| `peer-reviewed` | Journal article, academic book, conference paper with review |
| `primary` | Created by the practitioner/lab being discussed — technical blogs, official docs, release posts |
| `journalism` | Edited publication with editorial oversight (trade press, curated blogs) |
| `secondary` | Commentary, analysis, survey, synthesis by a non-primary voice |
| `informal` | Tweets, forum posts, unedited blogs, Discord snippets |

`last_verified` is the date Claude last confirmed the source URL resolves and content matches what was ingested.

`superseded_by` is empty by default. On re-ingest of a newer version, point to the new source note.

### Concept articles (`wiki/concepts/`)

```yaml
---
title: Concept Title
aliases: [alternative name, abbreviation]
tags: [#spatial-intelligence, #neural-graphics]
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: [[Source One]], [[Source Two]]
contested: false
confidence: medium
---
```

Body sections: `Definition` > `Why it matters` > key subsections > `Limitations` or `Open questions` > `Connected Concepts` > `Sources`.

**`contested:`** — `true` when two or more sources make incompatible claims. Add a `Disagreements` section; never silently pick a winner.

**`confidence:`** — `high | medium | low`
- `high` — core claims rest on 2+ sources, at least one peer-reviewed or primary
- `medium` — 2+ sources, mixed tiers, no major contradictions
- `low` — single source, or sourcing is thin or partially contested

---

## Tag taxonomy

**`#spatial-intelligence`** — domain root; every page gets this tag

**Topic tags** (use whichever apply):
- `#world-models` — generative/multimodal/interactive world simulation systems
- `#neural-graphics` — ML-based 3D generation and rendering
- `#3d-representations` — structured spatial encodings (explicit, implicit, hybrid)
- `#3d-gaussian-splatting` — specifically 3DGS technique and derivatives
- `#embodied-ai` — perception-action loop, robotics, sim-to-real
- `#rendering` — real-time rendering, rasterization, pipelines
- `#ai-capabilities` — what current systems can and cannot do
- `#benchmarks` — evaluation, measurement, failure-mode analysis
- `#cognitive-science` — neuroscience / perception grounding (use sparingly — only when a source bridges to AI)

---

## People — when to create a page

| Tier | Trigger | Action |
|---|---|---|
| Author | Person authored a source in `wiki/sources/` | Always create a concept or person stub on ingest |
| Subject | Source is substantively about a person or lab | Create richer profile |
| Passing reference | Mentioned in passing | Use `[[Name]]` wikilink without creating a file. Create only on second independent citation |

---

## Citation & linking

- **Every concept claim should be traceable.** `sources:` front-matter lists the source notes the concept rests on.
- **Backlink rule**: every new concept links at least 2 existing concepts in `Connected Concepts`, or notes why it's an island (flagged in health).
- **Cross-vault links**: `[[VaultName/wiki/Concept Title]]` for sibling vaults.
- **Never break a link.** If renaming, update all backlinks. If archiving, leave a stub that redirects.

---

## Source freshness

1. **`last_verified:`** set on ingest; update whenever Claude re-confirms the source. Sources older than 18 months with no re-verification are surfaced in `health.md`.
2. **Re-ingest**: new version of a source → new note, old note's `superseded_by:` updated. Never edit the old source's body.
3. **Revision propagation**: after re-ingest, check every concept citing the old source and update if the new version changes the claim.

Sources are never deleted.

---

## Conflict resolution

When two sources make incompatible claims:

1. **Never silently resolve.**
2. **Flag it.** Set `contested: true` and add a `Disagreements` section with direct quotes and source attribution.
3. **Preserve the dispute.** Contested concepts are listed in `health.md`. Don't collapse to consensus unless new sources genuinely resolve it.

---

## Query → concept promotion

- After a query is written, set `Promotion: pending`.
- If the query answer rests on 2+ sources and reflects a durable concept, promote to a concept page on the next `/foundry-compile` run. Set `Promotion: promoted` on the query with a link to the new concept.
- If too narrow or thinly sourced, set `Promotion: declined` with a one-line reason.
- Pending queries older than 60 days are surfaced in `health.md`.

---

## Pruning & archival

Claude does not delete. Claude archives.

| Trigger | Action |
|---|---|
| Candidate in `index.md` for > 18 months with no second source | Move to `wiki/_meta/candidates-archive.md`, note in log |
| Orphan concept (zero inbound links) for > 12 months | Surface in health; archive only with your confirmation |
| Source with `Retracted:` and no remaining citing concepts | Move to `wiki/_archive/YYYY-MM/` |
| Concept fully superseded by a newer concept | Move to `wiki/_archive/YYYY-MM/`, leave stub with forwarding link |

`/foundry-prune` requires explicit confirmation — Claude never prunes unattended.

---

## Evaluation loop

`wiki/_meta/eval.md` holds 13 questions that should be answerable from the wiki. Run `/foundry-eval` quarterly or on demand:

1. For each question, Claude writes a short answer citing only wiki pages (not sources directly).
2. Rates each answer: `strong` / `thin` / `missing`.
3. `thin` and `missing` feed into `index.md` Open Questions and Candidates.

---

## Operations

### Ingest (`/foundry-ingest`)

Process anything in `inbox/` or `raw/articles/` into source notes in `wiki/sources/`.

Flow: read source > assign tier > write source note with YAML front-matter, summary, key concepts, Claude's notes > cross-reference sibling vaults > update `wiki/_meta/index.md` > append to `wiki/_meta/log.md` > clear inbox.

### Compile (`/foundry-compile`)

Synthesise concept pages from sources. After ingest, or on demand.

Flow: for each new source, extract concepts > check `wiki/_meta/index.md` and `wiki/indexes/Master Index.md` for existing pages > create new or update existing > assign `confidence:` > check for conflicts and set `contested:` > update `Connected Concepts` backlinks > update `wiki/_meta/index.md` and `wiki/indexes/Master Index.md` > append to `wiki/_meta/log.md`.

### Lint (`/foundry-lint`)

Check vault health. Outputs `wiki/_meta/health.md`.

Check for: orphan pages, concepts with `confidence: low` unchanged for > 6 months, `contested: true` with no Disagreements section, pending queries > 60 days, stale sources, candidates > 18 months with no second source, missing mandatory front-matter fields.

### Eval (`/foundry-eval`)

See `## Evaluation loop`. Outputs into `wiki/_meta/eval.md` "Latest run" section.

### Prune (`/foundry-prune`)

Presents a prune plan after `/foundry-lint`. Waits for explicit confirmation before moving anything to `wiki/_archive/`.

---

## Changes from v1

| Feature | v1 (original MacBook CLAUDE.md) | v2 (this file) |
|---|---|---|
| Source tiering | None | `tier:` mandatory on every source note |
| Conflict handling | Silent resolution | `contested:` + `Disagreements` section |
| Source freshness | Never checked | `last_verified:` + stale-source lint |
| Pruning | Not specified | Archive-only; `/foundry-prune` with confirmation |
| Voice anchor | None | Domain-specific paragraph (AI spatial intelligence) |
| Scope declaration | Implicit | Explicit — AI/computational focus; neuro/pheno only as grounding |
| Query promotion | Not specified | `Promotion:` field + criteria |
| Sibling vaults | Not specified | ~/generative-art as primary sibling |
| Evaluation loop | Not specified | `eval.md` + `/foundry-eval` quarterly |
| Directory convention | wiki/concepts/, wiki/sources/, wiki/indexes/ — Title Case | Same — preserved from MacBook-side ingest |
