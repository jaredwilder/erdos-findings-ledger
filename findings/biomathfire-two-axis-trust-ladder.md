---
id: biomathfire-two-axis-trust-ladder
claim: |-
  BioMathFire: the estate's two-axis trust ladder, wired to the ledger
status: open
tier: silver
reality_score: 0.6
domain: math-to-biology
effect: |-
  oracle/biomathfire (82 TS files, 51/53 own tests passing) defines the ONLY graded trust vocabulary in the estate: math axis M0_IDEA..M5_FORMAL_MODEL_THEOREM and biology axis B0_UNVALIDATED..B5_PROSPECTIVE_MULTISITE, with enforceEarnedStatus making both monotone (an over-request is recorded as a demotion, never granted) and evaluateBioMathFirePromotion as a separate append-only decision over an immutable receipt. It had ZERO ledger presence until now despite being load-bearing. Routed the 14 EG#203/EG#411 transfers through its bridge: 2x M5_FORMAL_MODEL_THEOREM, 2x M3_INDEPENDENTLY_VERIFIED_BOUNDED, 10x M2_BOUNDED_COMPUTATIONAL, all at B0. Promotion needs math>=M3 AND bio>=B1, so 4 of 14 clear the math axis and 10 do not. TWO DEFECTS FOUND, NOT FIXED: (1) 2 failing tests, both 'returns a placeholder instead of doing the work' (representation compiler registry; exact representation solver portfolio); (2) blade_verifiers.py:197 asserts biologicalValidity=='B0_UNVALIDATED' as a CORRECTNESS condition, so a legitimately promoted transfer would be rejected as invalid. The Python contract math_biology_transfer.py knows nothing of B1-B5 and the canonical runner invention_ratchet.py:226 inherits that flat grade. ADDITIVE ONLY: the 14 already cleared NoveltyForge 14/14 NOVEL 0-collision on a live keyed corpus and that result is not conditional on any of this.
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/biomathfire/contracts/trust-class.ts
  - oracle/biomathfire/promotion-policy.ts
  - oracle/biomathfire/eg-campaign-bridge.ts
  - oracle/evidence/biomathfire/EG-BIOMATHFIRE-GRADED-2026-07-26.json
open_threads: []
provenance: |-
  session 2026-07-26, $0 deterministic zero-LLM
domain_lane: math-to-biology
domain_lane_source: domain-exact
---

# BioMathFire: the estate's two-axis trust ladder, wired to the ledger

**Status: open** · tier `silver` · reality_score 0.6 · domain math-to-biology

**Effect / numbers.**

oracle/biomathfire (82 TS files, 51/53 own tests passing) defines the ONLY graded trust vocabulary in the estate: math axis M0_IDEA..M5_FORMAL_MODEL_THEOREM and biology axis B0_UNVALIDATED..B5_PROSPECTIVE_MULTISITE, with enforceEarnedStatus making both monotone (an over-request is recorded as a demotion, never granted) and evaluateBioMathFirePromotion as a separate append-only decision over an immutable receipt. It had ZERO ledger presence until now despite being load-bearing. Routed the 14 EG#203/EG#411 transfers through its bridge: 2x M5_FORMAL_MODEL_THEOREM, 2x M3_INDEPENDENTLY_VERIFIED_BOUNDED, 10x M2_BOUNDED_COMPUTATIONAL, all at B0. Promotion needs math>=M3 AND bio>=B1, so 4 of 14 clear the math axis and 10 do not. TWO DEFECTS FOUND, NOT FIXED: (1) 2 failing tests, both 'returns a placeholder instead of doing the work' (representation compiler registry; exact representation solver portfolio); (2) blade_verifiers.py:197 asserts biologicalValidity=='B0_UNVALIDATED' as a CORRECTNESS condition, so a legitimately promoted transfer would be rejected as invalid. The Python contract math_biology_transfer.py knows nothing of B1-B5 and the canonical runner invention_ratchet.py:226 inherits that flat grade. ADDITIVE ONLY: the 14 already cleared NoveltyForge 14/14 NOVEL 0-collision on a live keyed corpus and that result is not conditional on any of this.

**Receipts.**

- `oracle/biomathfire/contracts/trust-class.ts`
- `oracle/biomathfire/promotion-policy.ts`
- `oracle/biomathfire/eg-campaign-bridge.ts`
- `oracle/evidence/biomathfire/EG-BIOMATHFIRE-GRADED-2026-07-26.json`

**Provenance.**

session 2026-07-26, $0 deterministic zero-LLM


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
