---
title: Evaluation Loop — How It Works
type: meta
created: 2026-05-08
updated: 2026-05-08
---

# What the Eval Questions Are For

Short version: the questions in `eval.md` are a measuring stick, not a to-do list. You don't answer them manually. Claude answers them, on demand, and rates its own answers. The ratings tell you whether the vault is getting better.

## The Loop, Concretely

1. **Ingest sources into the vault** — Add papers, articles, technical write-ups to `raw/articles/` and `raw/papers/`. Claude processes them into `wiki/sources/` and concept articles in `wiki/concepts/`.

2. **Every 8-12 sources or quarterly, run `/foundry-eval`.** Claude:
   - Takes each question in `eval.md`
   - Tries to answer using only wiki pages (not raw sources directly)
   - Rates: `strong` / `thin` / `missing`
   - Writes answers and ratings into `eval.md` "Latest run" section
   - Feeds `thin` and `missing` findings into `wiki/_meta/index.md` as Open Questions and Candidates

3. **Read the answers.** Two things happen:
   - **Trend shows if vault is improving.** If Q4 (LoD systems) was `missing` after 3 sources, `thin` after 6, and `strong` after 12, the vault is maturing. If everything stays `missing` for a year, ingest has drifted.
   - **Thin/missing findings direct next ingest.** If Q5 (multimodal inputs) is still `missing` after 8 sources, that's a signal: find a multimodal world model source and ingest it.

That's it. It's a feedback loop, not homework.

## Why This Structure

Without eval, wikis rot predictably: you ingest whatever crosses your desk, the vault grows but doesn't sharpen, and you can't tell quality is declining until it's too late. Lint stats (page count, orphans, keyword drift) are quantitative but don't catch *quality* drift. Eval questions are the qualitative counterweight.

The "Expected early rating" on each question gives the first run a baseline. If the first eval comes back better than expected, something valuable happened early. If worse, something's wrong with how sources are being synthesized.

## Concrete Example

Say in three months you've ingested 10 more sources (Marble papers, robotics work, benchmark studies). You run `/foundry-eval`. It comes back:

- Q1 (definition): `thin` — have Fei-Fei Li's vision, missing neuroscience grounding  
- Q4 (LoD systems): `strong` — Spark 2.0 article well-sourced, technical depth solid
- Q5 (multimodal inputs): `thin` — have architectural overview, missing failure mode analysis  
- Q11 (evaluation metrics): `missing` — no benchmark papers ingested yet

That output *is* your research agenda for next quarter: Find sources on spatial cognition grounding. Find multimodal model failure analysis. Find benchmark papers.

## When to Run It

**Not yet on cold start.** With 3 sources ingested, eval would show mostly `missing`—expected, not useful. First meaningful run is after ~8-12 sources, probably 2-3 months in.

## How to Add or Change Questions

1. New questions go at the bottom of `eval.md`
2. Numbering is append-only (never reuse numbers)
3. Each question should probe one capability and identify missing sources/synthesis that would strengthen an answer
4. Avoid "yes/no" questions; prefer open-ended framing that reveals conceptual gaps

## How to Update Index

As sources are ingested, `wiki/_meta/index.md` should be manually updated or auto-generated:

- Add new sources to the **Sources** section
- Add new concept pages to **Concepts**
- Move candidates from **Candidates** to **Concepts** when their sources appear
- Update **Research Threads** when new connections emerge
