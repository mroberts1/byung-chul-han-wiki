---
title: Shanzhai Index
tags:
  - shanzhai
created: 2026-05-31
updated: 2026-05-31
---

# Shanzhai

Topic index for everything tagged `#shanzhai` — covers Han's *Shanzhai: Deconstruction in China* and related concepts.

## Sources

```dataview
TABLE date as "Year", authors
FROM "wiki/sources"
WHERE contains(tags, "shanzhai")
SORT date DESC
```

## Concepts

```dataview
TABLE tags
FROM "wiki/concepts"
WHERE contains(tags, "shanzhai")
SORT file.name ASC
```
