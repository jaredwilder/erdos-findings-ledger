---
id: erdos-203-covering-refutation-closed
claim: |-
  Erdos-Graham 203: covering-system refutation route closed (Sylow-2 obstruction); Lean closure mod 2 count-bound axioms
status: validated-observational
tier: gold
reality_score: 0.85
# --- OEC DECLARATIONS (2026-07-26) ---
# A BARRIER IS A RESULT. truth_mode 'barrier' exists precisely so a proof that an
# attack cannot work is not filed as a failure to prove the target.
artifact_kind: barrier
truth_mode: barrier
scope_grade: universal
inference: deductive
independence: single_path
reproducibility: artifact_verified
novelty: unchecked
claim_ir:
  claim_id: "eg203:covering_refutation_route_dead"
  assertion_kind: barrier
  display: "The Sierpinski-style covering-system refutation route cannot resolve EG203: a 1/128 sublattice is persistently uncovered."
  scope:
    domain: number_theory
    label: "all covering systems of the stated form"
  statement:
    op: attack_cannot_reach_target
    args:
      - {op: const, args: ["covering_system_refutation", "method"]}
      - {op: const, args: ["erdos_graham_203", "target"]}
  definitions:
    obstruction: "Sylow-2/Lagrange: odd-order fiber orbits cannot contain the order-2 element -1"
  tags: [erdos, covering_systems, barrier, lean]
# --- PER-CLAIM TYPING (schema v2, 2026-07-26) ---
claims:
  - id: sylow2_obstruction
    statement: The Sierpinski-style covering-system refutation route cannot work — a 1/128 sublattice is persistently uncovered.
    inference: deductive
    closure: closed
    basis: Sylow-2 / Lagrange argument (odd-order fiber orbits cannot contain the order-2 element −1)
    why: >-
      A BARRIER THEOREM, and it is a proof, not a measurement. It kills the only known
      refutation mechanism. Barriers are results — do not file this as "still open".
  - id: bounded_closure
    statement: Bounded closure holds for all m <= 10^6, with an explicit prime witness for each.
    inference: deductive
    closure: closed
    basis: Lean, native_decide, explicit witness per case, zero math axioms
    why: >-
      Exhaustive over a finite range with a witness each. Deductive but SCOPED to
      m <= 10^6; the scale ladder to 10^19 is a separate structure, not this claim.
  - id: noncovering_certificates
    statement: The densest adversary primorial(22)−1 blankets at most 0.848 < 1.
    inference: deductive
    closure: closed
    basis: exact non-covering certificates
    why: An exact computation with a certificate; asserts only what was computed.
  - id: empirical_ordinary_m
    statement: 3.33x10^9 ordinary m up to 10^10 with zero failures.
    inference: inductive
    closure: open
    basis: enumeration to 10^10
    why: >-
      Supporting evidence only. As a statement about ALL m it generalizes past the
      enumerated range. It is NOT the headline and must not be cited as one.
  - id: problem_status
    statement: EG#203 itself remains open behind the parity barrier (kappa = 1).
    inference: deductive
    closure: open
    basis: the parity barrier
    why: A stated boundary, not a claim of progress. Kept explicit so the barrier is never lost.
effect: |-
  Kernel-verified: bounded closure m<=10^6 (explicit prime witness each, native_decide, zero math axioms); scale ladder to 10^19; the ONLY known refutation mechanism (Sierpinski-style covering system) is measured dead - persistent 1/128=2^-7 uncovered sublattice {k0=0 mod 8, l0=0 mod 16} of the base 2520x5040 (99225 cells), proven by Sylow-2/Lagrange (odd-order fiber orbits cannot contain the order-2 element -1); exact non-covering certificates (densest adversary primorial(22)-1 blankets <=0.848<1). Problem itself OPEN behind the parity barrier (kappa=1). Empirical: 3.33x10^9 ordinary m to 10^10, zero failures.
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/math/EG203Formal/EG203Formal/EG203BoundedClosure.lean
  - oracle/math/EG203Formal/EG203Formal/Persistence.lean
open_threads: []
provenance: |-
  (not provided)
domain_lane: math
domain_lane_source: claim-ir-scope-domain
---

# Erdos-Graham 203: covering-system refutation route closed (Sylow-2 obstruction); Lean closure mod 2 count-bound axioms

**Status: validated-observational** · tier `gold` · reality_score 0.85

**Effect / numbers.**

Kernel-verified: bounded closure m<=10^6 (explicit prime witness each, native_decide, zero math axioms); scale ladder to 10^19; the ONLY known refutation mechanism (Sierpinski-style covering system) is measured dead - persistent 1/128=2^-7 uncovered sublattice {k0=0 mod 8, l0=0 mod 16} of the base 2520x5040 (99225 cells), proven by Sylow-2/Lagrange (odd-order fiber orbits cannot contain the order-2 element -1); exact non-covering certificates (densest adversary primorial(22)-1 blankets <=0.848<1). Problem itself OPEN behind the parity barrier (kappa=1). Empirical: 3.33x10^9 ordinary m to 10^10, zero failures.

**Receipts.**

- `oracle/math/EG203Formal/EG203Formal/EG203BoundedClosure.lean`
- `oracle/math/EG203Formal/EG203Formal/Persistence.lean`


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
