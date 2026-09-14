---
id: hadamard-668-direct-assault-2026-07-25
claim: |-
  Hadamard order 668: route reduction to the four-sequence Williamson/Goethals-Seidel (SDS) branch. Cyclic difference-set and tensor routes unavailable under their stated constructions. Bounded CP-SAT attacks all UNKNOWN; no exact completion. NOT an existence or nonexistence result.
status: open
tier: gold
domain: math
reality_score: 0.75
# --- FRONTMATTER ADDED 2026-07-26 ---------------------------------------------
# This file had NO frontmatter at all, which made a real Hadamard attack INVISIBLE to
# every tool the estate owns: the ledger's domain filter returned 4 math findings when
# 13 are math-bearing, and this was one of the 9 it could not see. Nothing about the
# science changed here; only its visibility. 21 of 133 finding files are in this state.
artifact_kind: measurement
truth_mode: observed
scope_grade: instance
inference: computational
independence: single_source
reproducibility: artifact_verified   # receipts listed in the body, replayed
novelty: unchecked
# assertion_kind is DELIBERATELY ABSENT. The body sets a hard claim ceiling -- "No
# Hadamard-668 existence or nonexistence claim follows; UNKNOWN means the bounded solver
# run did not settle the branch." Declaring `theorem`, `refutation` or `barrier` would
# route this to a CLOSING goal (verify / find_witness / prove_nonexistence) and let a
# bounded UNKNOWN be reported as a settled result. The absence is the honest typing.
mathfire:
  applicable: false
  why: |-
    All three Hadamard techniques in MathFire 4.0.0 -- matrix.hadamard_divisibility,
    matrix.hadamard_compatibility_clique, matrix.sylvester_power_of_two -- declare
    composition_inputs=('sign_matrix',). They operate on a GIVEN +/-1 matrix; none accepts a
    bare order. For 668 the matrix is exactly what is unknown, so there is no admissible
    payload. Measured 2026-07-26 by running all three, not by reading docs.
  route_when_a_matrix_exists: |-
    A real chain now exists and is machine-findable (composition_bus, 2026-07-26):
      matrix.hadamard_compatibility_clique -> row_compatibility_graph
        -> [adapter compatibility_graph_to_adjacency] -> adjacency
        -> graph.exact_independence | graph.exact_coloring | graph.component_factorization
    This is the estate's own stated next step -- reduce the construction to an exact clique
    problem -- wired to the exact solvers. Before 2026-07-26 that edge did not exist:
    row_compatibility_graph was an output port nothing consumed.
open_threads:
  - exact four length-167 SDS/PAF equations with multiplier/orbit restrictions
  - integer lifting has not preserved the clean 13-shift defect support
domain_lane: math
domain_lane_source: domain-exact
---

# Hadamard 668 direct assault — receipt-backed status (2026-07-25)

## Finding

The transport audit reduces the unrestricted order-668 target to the live four-sequence Williamson/Goethals–Seidel (SDS) route. The cyclic difference-set route and the tensor route are not available under their stated constructions. This is a route reduction, not a nonexistence proof for Hadamard 668.

The published 64-modular scaffold was reproduced exactly: 153 of 166 checked conditions pass, with squared defect 839680. It is therefore a verified modular scaffold, not an integer Hadamard matrix. Integer lifting has not preserved its clean 13-shift defect support: the fixed-q checkpoint reaches exact defect score 11008 with 57 nonzero defects, while the free-q checkpoint reaches 11440 with 67 nonzero defects. The free-q relaxation is weaker in this bounded comparison.

Direct bounded attacks have produced no exact completion:

- symmetric CP-SAT signatures `(1,1,15,21)` and `(23,11,3,3)`: `UNKNOWN`, no completion;
- skew CP-SAT signature `(1,1,15,21)`: `UNKNOWN`, no completion;
- inverse-PAF CP-SAT completion checks for all four blocks of the best portfolio candidate: `UNKNOWN`, no completion;
- the round-2 representation/control matrix: 25 independently replayed bounded results, zero exact constructions, best bounded defect 656.

## Claim ceiling

No Hadamard-668 existence or nonexistence claim follows. `UNKNOWN` means the bounded solver run did not settle the branch. The modular scaffold and lift checkpoints are computational state and negative/near-miss evidence only. The unrestricted target remains open.

## Next mathematical consequence

The modular-lift route has not yielded a stable integer invariant. Further progress should attack the exact four length-167 SDS/PAF equations with arithmetic multiplier/orbit restrictions and certificate extraction, rather than treating the 64-modular defect support as an exact integer pattern.

## Receipts

- `oracle/runtime/state/frontier-math-solve-by-transport.json`
- `oracle/runtime/state/frontier-hadamard-668-mod64-scaffold.json`
- `oracle/runtime/state/frontier-hadamard-668-mod64-lift.json`
- `oracle/runtime/state/direct-mod64-lift-500k.json`
- `oracle/runtime/state/direct-mod64-free-q-100k.json`
- `oracle/runtime/state/direct-symmetric-1-1-15-21.json`
- `oracle/runtime/state/direct-symmetric-23-11-3-3.json`
- `oracle/runtime/state/direct-skew-1-1-15-21.json`
- `oracle/runtime/state/direct-inverse-paf-b0.json` through `direct-inverse-paf-b3.json`

