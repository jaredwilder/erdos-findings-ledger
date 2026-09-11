---
id: transport-graph-status-hub-false-connectivity-2026-07-24
claim: |-
  Transport-graph status-label hubs inflate blade connectivity
status: validated-observational
tier: silver
reality_score: 0.7
domain: infrastructure
effect: |-
  CAPABILITY/INTEGRITY finding, not frontier movement: mathematical_claim stays OPEN. The five founding 'marooned blade islands' in ORACLE-IOU-MASTER (sizes 1158/1482/702/268/109) are exactly five semantic label hub nodes plus their dependents: status:NONE deg 1157, status:OPEN deg 1481, status:EXISTS deg 701, status:UNDECIDED deg 267, status:EXISTS_UNIQUE deg 108 (+1 for the hub itself in each case). Every SRG sharing a STATUS STRING was union-found together through a node that states an answer, not a theorem, so no transport could ever bridge them and one legitimate edge into a hub teleports every dependent into the target component at once. Measured on the live 671772-node/7411249-edge oracle-math.db: excluding hub-incident edges (3783) and INCOMPARABLE edges (5743, which assert NON-comparability yet were being traversed), blade nodes in the giant component fall 2891 -> 2. The 2 survivors are real: srg:99,14,1,2 (Conway 99-graph) and srg:99,84,71,72 (its complement), via the one genuine SAME_PROPOSITION identity to Mathlib decl:SimpleGraph.conway_99. True largest blade-bearing component is 22 nodes, not 2891. Fixed at source in build_db.py via joins_components(); oracle_db.COMPOSABLE reconciled to include SAME_PROPOSITION. mathlib_armory.py already guarded this hub pathology on the Mathlib import path; these edges arrive via the Brouwer/facts path and were unguarded. Materialized component column still carries the inflated values until build_db.py is re-run.
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/kbk/codex-handoff-graph-bridge/true-connectivity-audit.json
  - oracle/tools/transport-import/audit_true_connectivity.py
open_threads: []
provenance: |-
  session 2026-07-24, $0 deterministic, no network, no LLM; audit selftest 5/5 on a synthetic hub graph
domain_lane: infrastructure
domain_lane_source: domain-exact
---

# Transport-graph status-label hubs inflate blade connectivity

**Status: validated-observational** · tier `silver` · reality_score 0.7 · domain infrastructure

**Effect / numbers.**

CAPABILITY/INTEGRITY finding, not frontier movement: mathematical_claim stays OPEN. The five founding 'marooned blade islands' in ORACLE-IOU-MASTER (sizes 1158/1482/702/268/109) are exactly five semantic label hub nodes plus their dependents: status:NONE deg 1157, status:OPEN deg 1481, status:EXISTS deg 701, status:UNDECIDED deg 267, status:EXISTS_UNIQUE deg 108 (+1 for the hub itself in each case). Every SRG sharing a STATUS STRING was union-found together through a node that states an answer, not a theorem, so no transport could ever bridge them and one legitimate edge into a hub teleports every dependent into the target component at once. Measured on the live 671772-node/7411249-edge oracle-math.db: excluding hub-incident edges (3783) and INCOMPARABLE edges (5743, which assert NON-comparability yet were being traversed), blade nodes in the giant component fall 2891 -> 2. The 2 survivors are real: srg:99,14,1,2 (Conway 99-graph) and srg:99,84,71,72 (its complement), via the one genuine SAME_PROPOSITION identity to Mathlib decl:SimpleGraph.conway_99. True largest blade-bearing component is 22 nodes, not 2891. Fixed at source in build_db.py via joins_components(); oracle_db.COMPOSABLE reconciled to include SAME_PROPOSITION. mathlib_armory.py already guarded this hub pathology on the Mathlib import path; these edges arrive via the Brouwer/facts path and were unguarded. Materialized component column still carries the inflated values until build_db.py is re-run.

**Receipts.**

- `oracle/kbk/codex-handoff-graph-bridge/true-connectivity-audit.json`
- `oracle/tools/transport-import/audit_true_connectivity.py`

**Provenance.**

session 2026-07-24, $0 deterministic, no network, no LLM; audit selftest 5/5 on a synthetic hub graph


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
