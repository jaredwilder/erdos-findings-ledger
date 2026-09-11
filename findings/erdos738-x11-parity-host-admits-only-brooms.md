---
id: erdos738-x11-parity-host-admits-only-brooms
claim: |-
  X11 executed: the parity-defect host admits exactly n-1 induced rooted trees on n vertices, and they are exactly the brooms
status: validated-observational
tier: silver
reality_score: 0.82
effect: |-
  DP over depth-parity assignments using T12's criterion verbatim. Rooted trees occurring induced in the parity host: 1,1,2,3,4,5,6,7,8 for n=1..9 -- exactly n-1 for n>=2 -- against 1,1,2,4,9,20,48,115,286 rooted trees total. Linear versus exponential. Structural classification computed from the enumeration: the admissible trees are exactly the BROOMS, a root path of height h ending in a star of the remaining n-h leaves, one per height h=1..n-1. Every non-broom rooted tree on >=4 vertices is obstructed (first obstruction at n=4)
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/evidence/erdos738-import/X11-parity-host-catalogue.json
  - oracle/evidence/erdos738-import/frozen-statements.json
open_threads: []
provenance: |-
  (not provided)
---

# X11 executed: the parity-defect host admits exactly n-1 induced rooted trees on n vertices, and they are exactly the brooms

**Status: validated-observational** · tier `silver` · reality_score 0.82

**Effect / numbers.**

DP over depth-parity assignments using T12's criterion verbatim. Rooted trees occurring induced in the parity host: 1,1,2,3,4,5,6,7,8 for n=1..9 -- exactly n-1 for n>=2 -- against 1,1,2,4,9,20,48,115,286 rooted trees total. Linear versus exponential. Structural classification computed from the enumeration: the admissible trees are exactly the BROOMS, a root path of height h ending in a star of the remaining n-h leaves, one per height h=1..n-1. Every non-broom rooted tree on >=4 vertices is obstructed (first obstruction at n=4)

**Receipts.**

- `oracle/evidence/erdos738-import/X11-parity-host-catalogue.json`
- `oracle/evidence/erdos738-import/frozen-statements.json`


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
