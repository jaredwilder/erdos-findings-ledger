---
id: rapid-fire-sidon-c3-divergence-20260729
claim: |-
  Sidon∩C₃ divergence: for n≤34, max|Sidon| = max|Sidon∩C₃-free|.
  At n=35, max|Sidon|=8 but max|Sidon∩C₃-free|=7. The C₃ constraint becomes binding.
status: validated-observational
tier: bronze
domain: sidon-c3-intersection
domain_lane: math
domain_lane_source: receipt-router-manual
receipts:
  - oracle/evidence/rapid-fire/intersections-operator-20260729T010540Z.json
  - oracle/evidence/rapid-fire/SIDON-C3-NONBINDING-REFUTED.json
open_threads: []
provenance: |-
  CP-SAT computed max|Sidon| and max|Sidon∩C₃-free| independently for n=1..39.
  Values agree for n≤34. At n=35, pure Sidon grows to 8 but joint constraint stays at 7.
  The broader claim "Sidon∩C₃ = Sidon for all N" is REFUTED.
  The bounded claim "non-binding for n≤34" is VALIDATED.
auto_banked: false
---

# Sidon∩C₃ Divergence at n=35

**Status:** validated-observational · tier bronze · domain sidon-c3-intersection

**Result.** The C₃-avoidance constraint [1,-3,3,-1]·x=0 is non-binding on Sidon sets for n ≤ 34 — every maximum Sidon set in {1..34} is automatically C₃-free. At n=35, the constraints diverge: max|Sidon| = 8 (witness: {1,3,13,20,26,31,34,35}) but max|Sidon∩C₃-free| = 7.

**Refutation.** The universal hypothesis "Sidon ∩ C₃ = Sidon for all N" is FALSE.

**What survives.** The bounded result "non-binding for n ≤ 34" is a validated computational observation.

**Evidence.** `oracle/evidence/rapid-fire/SIDON-C3-NONBINDING-REFUTED.json`

_Manually recorded. Status is receipt-backed._
