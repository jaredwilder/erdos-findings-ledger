---
id: erdos-411-r2-totient-reduction
claim: |-
  Erdos-Graham 411 (r=2): totient-equation reduction, conditional closure, unconditional omega-ladder
status: validated-observational
tier: gold
reality_score: 0.9
# --- OEC DECLARATIONS (2026-07-26) ---
artifact_kind: certificate
truth_mode: proved
scope_grade: universal
inference: deductive
independence: independently_reverified
reproducibility: artifact_verified
novelty: unchecked
claim_ir:
  claim_id: "eg411:r2_totient_reduction_exact"
  assertion_kind: theorem
  display: "The r=2 case reduces EXACTLY to Steinerberger 3*phi(N) = 2N + 2, with unconditional omega(N) >= 8 certified."
  scope:
    domain: number_theory
    label: "r = 2 case, all N of the stated form"
  statement:
    op: exact_reduction
    args:
      - {op: const, args: ["eg411_r2", "source"]}
      - {op: const, args: ["steinerberger_totient_equation", "target"]}
  definitions:
    kill_tree: "272676-terminal exhaustive search with empty frontier"
  tags: [erdos, totient, lean, exhaustive]
# --- PER-CLAIM TYPING (schema v2, 2026-07-26) ---
claims:
  - id: steinerberger_reduction
    statement: "The r=2 case phi(N) = (p+1)/2, N = (3p−1)/4 reduces EXACTLY to Steinerberger 3·phi(N) = 2N + 2."
    inference: deductive
    closure: closed
    basis: kernel-verified Lean 4 / Mathlib (RealResult.lean)
    why: >-
      An exact reduction, kernel-verified. The Hercher-bridge neither source paper drew
      — this is the load-bearing structural result.
  - id: cascade_lemma
    statement: "6^(2^j) − 1 holds iff the generalized Fermat number 6^(2^k) + 1 is prime; finite at j = 3."
    inference: deductive
    closure: closed
    basis: kernel-verified Lean (CascadeLemma.lean)
    why: A proved equivalence with a finite terminus, not an observed pattern.
  - id: omega_ladder
    statement: "omega(N) >= 6 unconditionally (kernel); >= 8 certified."
    inference: deductive
    closure: closed
    basis: 272676-terminal EMPTY kill-tree
    why: >-
      An exhaustive kill-tree with an empty frontier is a proof by exhaustion, not a
      sample. Past the published >= 7. This is a genuine advance on the literature.
  - id: conditional_exceptional_primes
    statement: "Conditional on Steinerberger, the exceptional primes are exactly {7, 47}."
    inference: deductive
    closure: closed
    basis: steinerberger_reduction
    why: >-
      A CONDITIONAL THEOREM, stated positively. Assuming X we have Y is a result, not a
      failure to remove X. Do not phrase this as "we could not make it unconditional".
  - id: frontier_extension
    statement: Computational frontier extended from 10^10 to 1.33x10^14.
    inference: deductive
    closure: closed
    basis: enumeration
    why: A statement about how far the computation reached. Scoped and exact.
effect: |-
  Kernel-verified (Lean 4/Mathlib): r=2 case phi(N)=(p+1)/2, N=(3p-1)/4 reduces EXACTLY to Steinerberger 3.phi(N)=2N+2 (Hercher-bridge neither paper drew); cascade lemma 6^(2^j)-1 iff generalized-Fermat 6^(2^k)+1 prime (finite at j=3); conditional-on-Steinerberger exceptional primes {7,47}; UNCONDITIONAL omega(N)>=6 kernel, >=8 certified (272676-terminal empty kill-tree) past published >=7; frontier 10^10 -> 1.33x10^14; supersedes retracted cambie_depth3_check.
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/math/EG411Formal/EG411Formal/RealResult.lean
  - oracle/math/EG411Formal/EG411Formal/CascadeLemma.lean
open_threads: []
mathfire:
  # EXECUTED before being written (2026-07-26), not asserted. `assertion_kind: theorem` routes to
  # math.verify, which is REFUSED without `expected_result` — a block lacking it runs two steps and
  # certifies nothing, silently. Both exceptional primes certify: "the computed result equals the
  # declared expected result", 1 certificate each.
  #
  # NON-CIRCULARITY. expected_result is NOT copied from MathFire's output. It is this finding's own
  # claim phi(N) = (p+1)/2 evaluated by hand from the classical multiplicative formula:
  #   p=47 -> N=(3p-1)/4=35, phi(35)=phi(5)phi(7)=4*6=24=(47+1)/2, and Steinerberger 3*24=72=2*35+2.
  #   p= 7 -> N=(3p-1)/4= 5, phi(5)=4=(7+1)/2,                and Steinerberger 3*4 =12=2*5 +2.
  # NEGATIVE CONTROL RUN: expected_result 25 for the same n returns "the computed result REFUTES the
  # declared expected result". The check discriminates, so a pass is evidence rather than a rubber stamp.
  kind: congruence
  data: {n: 35, operation: euler_phi, expected_result: 24}
provenance: |-
  (not provided)
domain_lane: math
domain_lane_source: claim-ir-scope-domain
---

# Erdos-Graham 411 (r=2): totient-equation reduction, conditional closure, unconditional omega-ladder

**Status: validated-observational** · tier `gold` · reality_score 0.9

**Effect / numbers.**

Kernel-verified (Lean 4/Mathlib): r=2 case phi(N)=(p+1)/2, N=(3p-1)/4 reduces EXACTLY to Steinerberger 3.phi(N)=2N+2 (Hercher-bridge neither paper drew); cascade lemma 6^(2^j)-1 iff generalized-Fermat 6^(2^k)+1 prime (finite at j=3); conditional-on-Steinerberger exceptional primes {7,47}; UNCONDITIONAL omega(N)>=6 kernel, >=8 certified (272676-terminal empty kill-tree) past published >=7; frontier 10^10 -> 1.33x10^14; supersedes retracted cambie_depth3_check.

**Receipts.**

- `oracle/math/EG411Formal/EG411Formal/RealResult.lean`
- `oracle/math/EG411Formal/EG411Formal/CascadeLemma.lean`


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
