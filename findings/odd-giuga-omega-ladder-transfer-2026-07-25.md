---
id: odd-giuga-omega-ladder-transfer-2026-07-25
claim: |-
  No odd Giuga number with <=11 prime factors; EG411 machinery transfers cold to an unseen open problem
status: validated-observational
tier: silver
reality_score: 0.65
domain: number-theory
effect: |-
  TRANSFER TEST + computational result. A Giuga number is composite n with p|(n/p - 1) for every p|n; all known ones are even (30, 858, 1722, 66198, ...) and whether an ODD one exists is OPEN. The EG411 omega-ladder skeleton (squarefree + multiplicative balance + monotone cap on the smallest part) was pointed at it cold. GROUND-TRUTH GATE PASSED FIRST: the enumerator rediscovered 30=(2,3,5), 858=(2,3,11,13) and 1722=(2,3,7,41) from scratch before any odd claim. RESULT: odd k=3..11 all EMPTY (exhaustive, exact rational arithmetic, two independent conditions checked - the sum form sum(1/p)-1/n in Z and the divisibility form p|(n/p-1)). k=12 TIMED OUT at 14.38M nodes - NO VERDICT, not empty. SECOND TRANSFER: when brute force hit the wall, EG411's terminal-solve trick ported too - the last two variables satisfy (Ds-P)(Dt-P) = P^2 - D, structurally the same object as EG411's (r-36)(s-36)=1261, collapsing two enumeration levels into one. So TWO independent pieces of the machinery moved to an unseen target. HONEST BOUNDARY: novelty of the >=12 bound is UNVERIFIED (MathWorld plus three searches, no primary literature read) - do not claim it as new; the standard reference records >=9. The transferable claim is the METHOD moving, not the bound.
inputs: |-
  0 dollars, deterministic, no network, no LLM
cohort: |-
  (see effect)
receipts:
  - oracle/math/EG411Formal/EG411Formal/MultiplicativeBalance.lean
blades: |-
  cap_kill_balance, terminal-solve elimination
open_threads:
  - {blade: complete k=12 odd Giuga (timed out at 14.38M nodes, no verdict), value: med, data: in-hand, cost: med, why: ""}
  - {blade: verify the >=12 bound against primary literature before any novelty claim, value: med, data: in-hand, cost: med, why: ""}
provenance: |-
  session 2026-07-25, 0 dollar deterministic zero-LLM
mathfire:
  # VERIFIED BEFORE BEING WRITTEN: route_task math.compute -> [[2,1],[3,1],[7,1],[41,1]].
  # This finding's ground-truth recoveries include the Giuga number 1722 = 2*3*7*41.
  # MathFire's exact factorization reproduces that factorisation independently.
  # SCOPE: this is a GROUND-TRUTH REGRESSION FIXTURE, not a test of the finding's claim.
  # The claim is that odd Giuga numbers with k = 3..11 prime factors do not exist
  # (exhaustive, k=12 timed out with NO verdict). Factorisation cannot speak to that.
  # It guards the engine against silently breaking on the one object we can check exactly.
  kind: number_theory
  data: {operation: factorization, n: 1722, expected_result: [[2, 1], [3, 1], [7, 1], [41, 1]]}
  verified: exact match with this finding's stated ground truth
domain_lane: math
domain_lane_source: domain-exact
---

# No odd Giuga number with <=11 prime factors; EG411 machinery transfers cold to an unseen open problem

**Status: validated-observational** · tier `silver` · reality_score 0.65 · domain number-theory

**Effect / numbers.**

TRANSFER TEST + computational result. A Giuga number is composite n with p|(n/p - 1) for every p|n; all known ones are even (30, 858, 1722, 66198, ...) and whether an ODD one exists is OPEN. The EG411 omega-ladder skeleton (squarefree + multiplicative balance + monotone cap on the smallest part) was pointed at it cold. GROUND-TRUTH GATE PASSED FIRST: the enumerator rediscovered 30=(2,3,5), 858=(2,3,11,13) and 1722=(2,3,7,41) from scratch before any odd claim. RESULT: odd k=3..11 all EMPTY (exhaustive, exact rational arithmetic, two independent conditions checked - the sum form sum(1/p)-1/n in Z and the divisibility form p|(n/p-1)). k=12 TIMED OUT at 14.38M nodes - NO VERDICT, not empty. SECOND TRANSFER: when brute force hit the wall, EG411's terminal-solve trick ported too - the last two variables satisfy (Ds-P)(Dt-P) = P^2 - D, structurally the same object as EG411's (r-36)(s-36)=1261, collapsing two enumeration levels into one. So TWO independent pieces of the machinery moved to an unseen target. HONEST BOUNDARY: novelty of the >=12 bound is UNVERIFIED (MathWorld plus three searches, no primary literature read) - do not claim it as new; the standard reference records >=9. The transferable claim is the METHOD moving, not the bound.

**Inputs.**

0 dollars, deterministic, no network, no LLM

**Receipts.**

- `oracle/math/EG411Formal/EG411Formal/MultiplicativeBalance.lean`

**Blades.**

cap_kill_balance, terminal-solve elimination

**Open threads (next blades).**

- **complete k=12 odd Giuga (timed out at 14.38M nodes, no verdict)** (value med · data in-hand · cost med) — 
- **verify the >=12 bound against primary literature before any novelty claim** (value med · data in-hand · cost med) — 

**Provenance.**

session 2026-07-25, 0 dollar deterministic zero-LLM


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
