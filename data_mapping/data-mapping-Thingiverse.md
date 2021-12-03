---
title: Ontology Mapping | Thingiverse → OKH-LOSHv1
...

# General

get only projects with:

- free/open license
  - = from the SPDX list, approved either by the OSI or the FSF
  - from LOSH license allowlist
- at least one source file (no image or README etc. file)
- the following fields _not_ empty:
  - "name"
  - "creator":"name"

# Direct Mapping

```
"name" = name
"license" = license [SPDX-ID]
"creator" = licensor
"public_url" = repo
"thumbnail" = image
```

What about:

- short description?
  - if unavailable → construct from "tags":"name"
- version?
- any sort of category?
