---
id: erdos738-promotion-contract-executed
claim: |-
  ERDOS-738 bank promotion contract executed: 14 of 74 statements clear clause 2, all 14 novelty-run, 0 eligible to leave the bank
status: validated-observational
tier: silver
reality_score: 0.8
effect: |-
  Clause 1: 74 statements frozen with SHA-256 (62 PROVED_IN_PACKET + 12 UNPROVED_CHECKABLE_TARGET); source md hash matches the shipped manifest byte-exact. Clause 2: the shipped finite audit executes 58,511 assertions but covers only 14 of 74 statements (11 by direct assertion over all triangle-free graphs n<=5, N14 via 89 vertex-critical graphs n<=6, T08/T09 via parity hosts d=3 k<=4); the other 60 carry proof routes only, so manifest finite_audit_status=PASS is true for 14 items, not 62. Clause 3: all 14 eligible statements novelty-run on the exact frozen statement -- 13 NOVEL (core 0.645-0.799), 1 INCREMENTAL (M01 First-Transition Arm Lemma, 0.616, the only item the corpus discriminated); 13 of 14 terminal NOVELTY_INADMISSIBLE_NOT_A_DISCOVERY. Clause 4: band recorded separately from truth. Clause 5: T11 Sibling-Selection Sterility invokes the type-uniform framework without stating it as a hypothesis -- it inherits from T10 but standing alone reads as a universal claim; X02 was a false positive of the audit regex and does state it. Net: 0 statements satisfy all five clauses, because 13 of 14 clause-2 survivors are terminal-refused on clause 3 and Lean remains unverified throughout
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/evidence/erdos738-import/clause3-novelty-summary.json
  - oracle/evidence/erdos738-import/frozen-statements.json
  - oracle/evidence/erdos738-import/RERUN-VERIFICATION.json
open_threads: []
provenance: |-
  (not provided)
---

# ERDOS-738 bank promotion contract executed: 14 of 74 statements clear clause 2, all 14 novelty-run, 0 eligible to leave the bank

**Status: validated-observational** · tier `silver` · reality_score 0.8

**Effect / numbers.**

Clause 1: 74 statements frozen with SHA-256 (62 PROVED_IN_PACKET + 12 UNPROVED_CHECKABLE_TARGET); source md hash matches the shipped manifest byte-exact. Clause 2: the shipped finite audit executes 58,511 assertions but covers only 14 of 74 statements (11 by direct assertion over all triangle-free graphs n<=5, N14 via 89 vertex-critical graphs n<=6, T08/T09 via parity hosts d=3 k<=4); the other 60 carry proof routes only, so manifest finite_audit_status=PASS is true for 14 items, not 62. Clause 3: all 14 eligible statements novelty-run on the exact frozen statement -- 13 NOVEL (core 0.645-0.799), 1 INCREMENTAL (M01 First-Transition Arm Lemma, 0.616, the only item the corpus discriminated); 13 of 14 terminal NOVELTY_INADMISSIBLE_NOT_A_DISCOVERY. Clause 4: band recorded separately from truth. Clause 5: T11 Sibling-Selection Sterility invokes the type-uniform framework without stating it as a hypothesis -- it inherits from T10 but standing alone reads as a universal claim; X02 was a false positive of the audit regex and does state it. Net: 0 statements satisfy all five clauses, because 13 of 14 clause-2 survivors are terminal-refused on clause 3 and Lean remains unverified throughout

**Receipts.**

- `oracle/evidence/erdos738-import/clause3-novelty-summary.json`
- `oracle/evidence/erdos738-import/frozen-statements.json`
- `oracle/evidence/erdos738-import/RERUN-VERIFICATION.json`


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
