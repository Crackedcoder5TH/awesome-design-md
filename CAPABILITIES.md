# Awesome Design MD — Verified Capabilities

This repo's piece of the [ecosystem](../Void-Data-Compressor/CAPABILITIES.md).

Last verified: 2026-04-30, branch `claude/audit-remembrance-ecosystem-xaaUr`.

---

## Role in ecosystem

Curated collection of design + architecture markdown documents.
Functions as the **non-code substrate input** — design rationales,
architectural decisions, and reference material that coherency-aware
agents can pull when they need design-quality patterns rather than
runtime-quality code patterns.

Not currently in `cross_repo_function_records.json` (the void's
substrate indexer focuses on functions in code repos), but the
markdown documents here are valid `coh://` substrate candidates
when admitted via the oracle pipeline.

---

## ✅ Verified

| # | Capability | Test |
|---|---|---|
| 1 | Repo present locally | `[ -d /home/user/awesome-design-md ]` returns 0 |
| 2 | Has `design-md/` curated content | `ls /home/user/awesome-design-md/design-md/ \| wc -l` returns >0 |
| 3 | Not in code-substrate (deliberate) | `python3 -c "import json; d=json.load(open('../Void-Data-Compressor/cross_repo_function_records.json')); repos=set(r['repo'] for r in d['records']); print('awesome-design-md' in repos or 'design' in repos)"` → False |

---

## Integration path (if needed)

To bring design markdown into the remembrance substrate, the path is:

1. Each markdown file gets registered via the oracle CLI with
   appropriate atomic properties (likely `domain: 'documentation'`
   or `domain: 'design'`)
2. The void's `cross_repo_introspect.py` would need a markdown
   walker (currently extracts only Python/JS function definitions)
3. The pattern would carry a `text_score` from oracle's text scorer
   but no `waveform_score` from void (no executable bytes to slice)

This is an **integration not yet built**, not a missing capability.

---

## ❌ Out of scope here

- Substrate / scoring math — void
- Atomic table / covenant — oracle
- Pattern publication — blockchain

---

*Cross-cutting capabilities: see [`Void-Data-Compressor/CAPABILITIES.md`](../Void-Data-Compressor/CAPABILITIES.md).*
