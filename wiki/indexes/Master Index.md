---
title: Master Index
created: 2026-05-31
updated: 2026-05-31
---

# Master Index

Central directory for the Byung-Chul Han Knowledge Base.

## Topic Indexes
- [[Shanzhai Index]]

## All Sources

```dataview
TABLE date as "Year", source_type as "Type", tags
FROM "wiki/sources"
SORT date DESC
```

## All Concepts

```dataview
TABLE tags
FROM "wiki/concepts"
SORT file.name ASC
```

## Orphaned Concepts
*Concepts with no backlinks — candidates for further development or deletion.*

```dataview
LIST
FROM "wiki/concepts"
WHERE length(file.inlinks) = 0
SORT file.name ASC
```

## Recently Modified

```dataview
TABLE file.mtime as "Modified"
FROM "wiki"
WHERE file.name != "Master Index"
SORT file.mtime DESC
LIMIT 15
```
