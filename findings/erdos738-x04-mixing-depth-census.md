---
id: erdos738-x04-mixing-depth-census
claim: |-
  X04 executed: shielded mixing-depth census over all free trees to n=12
status: validated-observational
tier: bronze
reality_score: 0.65
effect: |-
  Census over all unlabeled free trees n<=12, generator self-calibrated against A000055 (1,1,1,2,3,6,11,23,47,106,235,551 -- exact match). Best-root shielded mixing depth per M08/M09/M12: range 1..6 by n=12. Depth grows slowly against tree count -- at n=12, 551 trees occupy only 6 depth classes, and the modal class is d3_b3 (113 trees). Stars are always d1 (one region per leaf, no recursion); paths drive the maximum depth (d6_b2 at n=12 is unique)
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/evidence/erdos738-import/X04-mixing-depth-census.json
open_threads: []
provenance: |-
  (not provided)
---

# X04 executed: shielded mixing-depth census over all free trees to n=12

**Status: validated-observational** · tier `bronze` · reality_score 0.65

**Effect / numbers.**

Census over all unlabeled free trees n<=12, generator self-calibrated against A000055 (1,1,1,2,3,6,11,23,47,106,235,551 -- exact match). Best-root shielded mixing depth per M08/M09/M12: range 1..6 by n=12. Depth grows slowly against tree count -- at n=12, 551 trees occupy only 6 depth classes, and the modal class is d3_b3 (113 trees). Stars are always d1 (one region per leaf, no recursion); paths drive the maximum depth (d6_b2 at n=12 is unique)

**Receipts.**

- `oracle/evidence/erdos738-import/X04-mixing-depth-census.json`


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
