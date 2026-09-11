---
id: erdos142-exact-envelope-n9-54
claim: |-
  erdos:142 exact r_3(n) envelope: 46 values n=9..54 machine-proven optimal, first unproven n=55
status: validated-observational
tier: silver
reality_score: 0.7
effect: |-
  46 exact values of r_3(n) for n=9..54, every row optimalityProven=true from the registered max_subset_avoiding/sequence_scan executor, all 46 agreeing with A003002 (full-envelope known-answer calibration, not discovery). First unproven n=55; rows 55..60 are LOWER BOUNDS and the receipt refuses to call them sequence terms. Envelope boundary is budget-dependent: 52 in one contended-CPU trial, 54 in three subsequent 600s runs; the size values themselves are trial-invariant. $0, 0 paid calls, no network, no LLM
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/evidence/erdos142-exact-envelope/scan-9-60.json
  - oracle/evidence/erdos142-exact-envelope/all-campaign-lower-bounds.json
  - oracle/evidence/erdos142-exact-envelope/derived-theorems.json
open_threads: []
provenance: |-
  (not provided)
---

# erdos:142 exact r_3(n) envelope: 46 values n=9..54 machine-proven optimal, first unproven n=55

**Status: validated-observational** · tier `silver` · reality_score 0.7

**Effect / numbers.**

46 exact values of r_3(n) for n=9..54, every row optimalityProven=true from the registered max_subset_avoiding/sequence_scan executor, all 46 agreeing with A003002 (full-envelope known-answer calibration, not discovery). First unproven n=55; rows 55..60 are LOWER BOUNDS and the receipt refuses to call them sequence terms. Envelope boundary is budget-dependent: 52 in one contended-CPU trial, 54 in three subsequent 600s runs; the size values themselves are trial-invariant. $0, 0 paid calls, no network, no LLM

**Receipts.**

- `oracle/evidence/erdos142-exact-envelope/scan-9-60.json`
- `oracle/evidence/erdos142-exact-envelope/all-campaign-lower-bounds.json`
- `oracle/evidence/erdos142-exact-envelope/derived-theorems.json`


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
