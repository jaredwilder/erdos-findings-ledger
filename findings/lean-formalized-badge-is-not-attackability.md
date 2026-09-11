---
id: lean-formalized-badge-is-not-attackability
claim: |-
  786 of 3218 Lean frontier statements are answer(sorry) holes; the attackability badge never read the statement
status: validated-observational
tier: silver
reality_score: 0.75
effect: |-
  24.4% of formal-conjecture declarations (786/3218) encode the unknown answer INSIDE the statement, so no solver can attack them; 140 files are 100% holed, mapping to 90 live targets that were scoring +250 for 'attackable with no translation step' -- including erdos:3 at rank 2 of 9,926 with a $5,000 prize. erdos:142 at rank 1 has 1 attackable arm of 4. Badge now computed from the statement; selftest 30/30; exactly 90 targets stripped
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/evidence/targets/lean-attackability-audit.json
  - oracle/evidence/targets/lean-badge-misdirection.json
open_threads: []
provenance: |-
  (not provided)
---

# 786 of 3218 Lean frontier statements are answer(sorry) holes; the attackability badge never read the statement

**Status: validated-observational** · tier `silver` · reality_score 0.75

**Effect / numbers.**

24.4% of formal-conjecture declarations (786/3218) encode the unknown answer INSIDE the statement, so no solver can attack them; 140 files are 100% holed, mapping to 90 live targets that were scoring +250 for 'attackable with no translation step' -- including erdos:3 at rank 2 of 9,926 with a $5,000 prize. erdos:142 at rank 1 has 1 attackable arm of 4. Badge now computed from the statement; selftest 30/30; exactly 90 targets stripped

**Receipts.**

- `oracle/evidence/targets/lean-attackability-audit.json`
- `oracle/evidence/targets/lean-badge-misdirection.json`


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
