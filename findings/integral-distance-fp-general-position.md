---
id: integral-distance-fp-general-position
claim: |-
  General-position integral-distance sets over F_p²: exact maxima p=3..37 both residue classes; sqrt(p) growth law empirically supported; p≡3 mod 4 restriction shown non-load-bearing; NO finite-field obstruction at n=8; naive bounded-coordinate solver killed by a height wall
status: open
tier: gold
reality_score: 0.85
domain: math
# --- OEC DECLARATIONS (2026-07-26) ---
# HEADLINE IS THE EXHAUSTIVE ENUMERATION, NOT THE GROWTH LAW. The growth law is
# inductive and capped (see claims below); typing the file by it would mark three
# closed results as unproven. The enumeration is what this finding actually banks.
artifact_kind: enumeration
truth_mode: certified
scope_grade: bounded_family
inference: deductive
independence: independently_reverified   # search and witness-checker are separate code paths
reproducibility: artifact_verified
novelty: unchecked
claim_ir:
  claim_id: "integral_distance:fp2_exact_maxima"
  assertion_kind: enumeration
  display: "Exact maximum general-position integral-distance set sizes in F_p^2 for p = 3..37, both residue classes."
  scope:
    domain: finite_field_geometry
    label: "primes p <= 37, both classes mod 4"
  statement:
    op: exact_maximum_set_size
    args:
      - {op: const, args: ["general_position_integral_distance_set", "object"]}
      - {op: const, args: ["F_p^2", "ambient"]}
  definitions:
    general_position: "no 3 collinear and no 4 cocircular"
    integer_distance: "squared distance is a nonzero quadratic residue"
  tags: [erdos, integral_distance, finite_field, exhaustive]
# --- PER-CLAIM TYPING (schema v2, 2026-07-26) ---
# THIS FILE IS THE WORKED EXAMPLE FOR WHY ONE `inference` PER FILE IS WRONG.
# It holds two deductive (closed) claims and two inductive (open) ones. A single
# field would have stamped the whole file "inductive" and buried two real results.
claims:
  - id: exact_maxima
    statement: Exact maximum general-position integral-distance set sizes in F_p² for the ELEVEN primes p = 3..37.
    inference: deductive
    closure: closed
    basis: exhaustive branch-and-bound; every witness independently re-verified by a separate checker; p=37 added 2026-07-26 (receipt oracle/tools/epistemic/receipts/blade-p37.json)
    why: Exhaustive over each p. Asserts only the eleven values actually computed.
  - id: growth_law
    statement: "|S| <= C·sqrt(p) with C in [1.04, 1.21]."
    inference: inductive
    closure: open
    basis: exact_maxima (eleven primes, p <= 37)
    why: >-
      GENERALIZES from eleven primes to all p. The file says so itself: "an empirical fit,
      not a proof". MORE PRIMES CANNOT CLOSE THIS — computing p=53,67 hardens the fit
      and cannot promote it. Closure needs the Weil/character-sum argument.
  - id: firewall_catch
    statement: The p ≡ 3 (mod 4) restriction is not load-bearing; the theorem should be stated for all odd primes.
    inference: inductive
    closure: open
    basis: p=29 (1 mod 4) and p=31 (3 mod 4) both attain max 6, plus a null-line heuristic
    why: >-
      Generalizes from small p plus an unproved structural argument. Strong and
      probably right, but it is a recommendation about how to state a theorem, not a
      proved fact about all primes.
  - id: n8_no_local_obstruction
    statement: There is no finite-field obstruction to an 8-point general-position integral-distance set.
    inference: deductive
    closure: closed
    basis: explicit verified 8-point set in F_53², independently re-checked against all three constraints
    why: >-
      EXISTENCE BY EXPLICIT WITNESS. One verified example settles a non-existence
      question outright. Note the separate claim that F_p² contains n-point sets for
      EVERY n rests on growth_law and is therefore inductive — this claim does not.
  - id: height_wall
    statement: A naive bounded-coordinate/Cayley-Menger (Z3) search cannot produce an n=8 non-existence certificate.
    inference: deductive
    closure: closed
    basis: exact reachable heights H(4)<=20, H(5)<=100 computed, versus published H(7)≈15,700 (Kreisel-Kurz 2008)
    why: >-
      A barrier result. Reachable height is computed exactly; required height is a
      published theorem. The gap is decisive, not extrapolated. A citation is not a gap.
effect: |-
  Exact maxima by branch-and-bound for general-position integral-distance sets in F_p², p = 3..37, both residue classes, every witness independently re-verified by a separate code path. Ratio max/sqrt(p) in [1.043, 1.206]. FIREWALL CATCH: p=29 (1 mod 4) attains max 6, indistinguishable from p=31 (3 mod 4) — the p ≡ 3 (mod 4) restriction carries no information across the partition it claims to separate (same failure mode as the retracted eg411 cambie predicate, caught here pre-proof by direct computation). Explicit verified 8-point general-position set in F_53² proves there is NO local/finite-field obstruction to n=8; the R² wall is purely global Diophantine. HEIGHT WALL: exact max in-box integer-distance sets give H(4)<=20, H(5)<=100 against a required H(7)≈15,700 (Kreisel-Kurz 2008), so a naive bounded-coordinate Z3 search cannot reach n=7 and therefore cannot certify n=8 non-existence — "Action Step 2 (Z3 CM search)" is not viable as stated. The sqrt(p) growth law itself remains an empirical fit; a proof needs the Weil/character-sum argument.
inputs: |-
  $0, deterministic, zero-LLM. Exact integer arithmetic, no data acquisition, no network.
cohort: |-
  Primes p = 3,5,7,11,13,17,19,23,29,31,37 (both residue classes mod 4), plus F_53 for the n=8 witness. Integer boxes [0,H]² for H = 20,30,50,100.
receipts:
  - oracle/kbk/engine/integral_distance_fp.py
  - oracle/kbk/engine/integral_distance_fp2.py
  - oracle/kbk/engine/integral_distance_r2.py
open_threads:
  - {blade: weil-character-sum, value: high, data: in-hand, cost: high, why: "THE ONLY ROUTE TO CLOSING growth_law. It is inductive and capped — no quantity of additional primes can promote it. Requires the Weil/character-sum argument to make the generalization a read-off."}
  - {blade: extend_p, value: med, data: in-hand, cost: low, why: "SUPERSEDED 2026-07-26 — DO NOT COMPUTE p=53 OR p=67 FOR THE GROWTH LAW. Mechanism War over the 150 (a,b) pairs consistent with all ten measured maxima (18 observationally distinct theories) scores BOTH proposed primes at information gain 0.000, worst-case survivors 18/18: every consistent hypothesis predicts the same value there, so neither run can eliminate a single theory. Compute p=47 instead (info gain 8.889, eliminates 8 of 18, and cheapest of the three tied best: 47, 61, 109). p=41 and p=43 are also worthless (gain 0.000). Extending to 53/67 remains valid for the SEPARATE n=8 threshold question."}
  - {blade: compute_p_47, value: high, data: in-hand, cost: low, why: "THE DISCRIMINATING EXPERIMENT. Of 17 candidate primes, p=47 ties for maximum information gain (8.889) and is the cheapest to compute. UPDATED post-max(37): the 121 surviving theories split 59/62 on its predicted max (7 vs 8) - a near coin-flip, so either outcome halves the remaining class. p=61 and p=109 tie on information but cost more."}
  - {blade: restate-theorem-all-odd-primes, value: med, data: in-hand, cost: low, why: "Act on firewall_catch: restate the target theorem for all odd primes rather than p ≡ 3 (mod 4)."}
provenance: |-
  Session 2026-07-24, operator vector #1 (finite-field analogue of Erdos's Integral Distance Problem).
  Frontmatter added 2026-07-26 during the ledger typing pass; the mathematics is unchanged.
mathfire:
  # ⛔ THE F_p^2 LANE REMAINS UNSERVED, and that has not changed through MathFire 5.
  applicable: false
  why: |-
    MathFire's geometry ops decide collinearity with orientation(a,b,c)==0 -- the integer
    cross product over Z, NO modulus -- so they cannot speak about F_p^2, which is what this
    finding's primary claim is about. A preview scan of all 593 techniques in MathFire 5.0
    against a squared-distance matrix returns 0 applicable for GEOMETRY/PROVE and
    GEOMETRY/PROVE_NONEXISTENCE. Round 5 added nothing to this lane.
  planar_heptagon_independent_checks:
    # RELATED PLANAR RESULT, NOT this finding's F_p^2 witness. The Kreisel-Kurz heptagon H1
    # lives over Q(sqrt(2002)): each point is (x, y*sqrt(2002)) and the squared distance is
    # (dx)^2 + 2002*(dy)^2. Its COORDINATES are unreachable by every MathFire coordinate op
    # (they call int() on them); only the DISTANCE-MATRIX op accepts it.
    note: >-
      Both checks below were run against the published integer distance matrix D1 alone --
      no coordinates, no field embedding. Two independent engines, and the second was
      re-derived by hand.
    realizability_and_planarity:
      op: deep.discrete_geometry.euclidean_distance_matrix
      input_key: squared_distances
      result: valid=True, rank=2
      basis: exact rational centered Gram, 127 principal minors PSD-checked exactly
      means: the published matrix really is a Euclidean distance matrix of a PLANAR 7-point set
    full_general_position:
      # ⛔ CORRECTED 2026-07-26. The earlier row here recorded only "no three collinear" and
      # called that general position. THAT IS HALF THE DEFINITION. The Erdos integral point
      # set problem requires no three collinear AND NO FOUR CONCYCLIC -- Kreisel & Kurz put
      # it in their own title: "integral heptagons, no three points on a line, NO FOUR ON A
      # CIRCLE". The collinear half was verified exhaustively, by hand, twice, and the
      # missing half went unnoticed: a thorough check of the wrong condition.
      #
      # The omission produced a real false result elsewhere the same day -- a sweep reported
      # a SIX-POINT "general position" set that turned out to be six points on ONE CIRCLE,
      # the trivial family the condition exists to exclude. Retracted in fb870b4463.
      no_three_collinear:
        triples: 35
        collinear: 0
        basis: >-
          16*Area^2 = (a+b+c)(-a+b+c)(a-b+c)(a+b-c) from the integer side lengths; zero iff
          collinear. min |16*Area^2| = 54583758028800. Re-derived by hand in pure integer
          arithmetic. Valid in BOTH embeddings: sqrt(2002) factors out of the orientation
          determinant, so the verdict is identical for (x,y) and (x, y*sqrt(2002)).
      no_four_concyclic:
        quadruples: 35
        concyclic: 0
        basis: >-
          Exact determinant |x^2+2002y^2, x, y, 1| over Fractions, computed in the TRUE
          Q(sqrt(2002)) embedding. Unlike collinearity, this does NOT transfer from the naive
          (x,y) plane: the squared-norm column becomes x^2 + 2002y^2, so the check had to be
          redone in the field. sqrt(2002) factors out of the y-column alone, leaving an exact
          rational determinant.
      distances:
        pairs: 21
        integral_and_matching_D1: true
      verdict: >-
        The Kreisel-Kurz heptagon is in TRUE general position -- no three on a line, no four
        on a circle -- and all 21 distances are integers matching the published matrix D1.
        The paper's own titular claim, independently reconfirmed here under the full
        definition rather than half of it.
    eighth_point_oracle:
      what: >-
        Extending the 7x7 squared-distance matrix by a candidate row and re-running
        euclidean_distance_matrix REJECTS a candidate unless the Gram stays PSD and rank <= 2.
        3 bogus candidates rejected (rank 4), 1 genuine duplicate accepted -- not a rubber
        stamp in either direction.
      ⛔ scope: >-
        This tests ONE CANDIDATE AT A TIME. Nothing in the 593-technique armory enumerates the
        candidate space, so this is NOT a maximality proof and must never be recorded as one.
        The op named `conjecture_maximality_finite` does not help: it is QUARANTINED by this
        estate for returning REFUTED regardless of its input, and it ignores its own `universe`
        argument -- "maximal" there means maximal among a caller-supplied candidate list.
domain_lane: math
domain_lane_source: domain-exact
---

# Finding: √p growth law for general-position integral-distance sets over F_p²

**Status:** validated-observational (exact computation, self-verified)
**Date:** 2026-07-24
**Blade:** `oracle/kbk/engine/integral_distance_fp.py` (v1, exact B&B) + `integral_distance_fp2.py` (v2, incremental-prune, cross-checked vs v1)
**Target:** Finite-field analogue of Erdős's Integral Distance Problem in general position (operator vector #1).

## Setup

Points in F_p². Squared distance d(A,B) = (Δx)² + (Δy)² mod p. "Integer distance" ⟺ d is a nonzero
quadratic residue. "General position" ⟺ no 3 collinear AND no 4 cocircular (4×4 lift-determinant ≠ 0).
Exact maximum such set computed by branch-and-bound; **every returned witness independently re-verified**
against all three constraints (crystallise doctrine — search and checker are separate code paths).

## Result (exact maxima)

| p | p mod 4 | max | √p | max/√p | verified |
|---|---|---|---|---|---|
| 3 | 3 | 2 | 1.732 | 1.155 | ✓ |
| 7 | 3 | 3 | 2.646 | 1.134 | ✓ |
| 11 | 3 | 4 | 3.317 | 1.206 | ✓ |
| 19 | 3 | 5 | 4.359 | 1.147 | ✓ |
| 23 | 3 | 5 | 4.796 | 1.043 | ✓ |
| 31 | 3 | 6 | 5.568 | 1.078 | ✓ |
| 5 | 1 | 2 | 2.236 | 0.894 | ✓ |
| 13 | 1 | 4 | 3.606 | 1.109 | ✓ |
| 17 | 1 | 4 | 4.123 | 0.970 | ✓ |
| 29 | 1 | 6 | 5.385 | 1.114 | ✓ |

## Two findings

1. **The C√p growth law is empirically supported (strong).** Across p = 3…31 the exact maximum tracks
   √p tightly, ratio C ∈ [1.04, 1.21]. This is direct evidence for the conjectured upper bound
   |S| ≤ C√p — the target theorem of operator vector #1 — and is consistent with the Weil-bound /
   incidence-geometry heuristic that motivated it.

2. **FIREWALL CATCH — the "p ≡ 3 (mod 4)" hypothesis appears NOT load-bearing.** The p ≡ 1 (mod 4)
   ladder (isotropic form, where −1 is a square and null directions exist) obeys the *same* √p law:
   p=29 (1 mod 4) → max 6 is indistinguishable from p=31 (3 mod 4) → max 6. The general-position
   constraint (no 3 collinear) already forbids packing points on null lines, so isotropy buys nothing.
   **Recommendation:** the theorem should be stated for all odd primes, not restricted to p ≡ 3 (mod 4);
   the residue-class restriction over-specifies and carries little/no information across the partition it
   claims to separate — the same failure mode as the eg411 `cambie` retraction, caught here pre-proof by
   direct computation rather than by a Lean-clean-but-vacuous predicate.

## Connection to vector #4 (n=8 obstruction) — RESOLVED: no finite-field obstruction

An 8-point general-position square-distance set exists in F_p² iff max(p) ≥ 8. Because max(p) ≈ 1.2√p grows
without bound, F_p² contains n-point sets for EVERY n once p is large enough. **Explicit verified 8-set in
F_53²:** `[(28,14),(40,11),(16,5),(6,12),(1,0),(5,30),(17,11),(15,5)]` (all pairwise distances QR, no 3
collinear, no 4 cocircular — independently re-checked). Therefore **there is NO local/finite-field obstruction
to n=8** — vector #4's "prove local non-existence at small primes" cannot work for the existence question.
The R² wall is purely GLOBAL Diophantine (lifting F_p candidates to Z destroys almost all of them).

## The height wall (blade: integral_distance_r2.py) — kills the naive n=8 solver search

Exact max general-position INTEGER-distance set inside the box [0,H]² over Z²:

| H | max n |
|---|---|
| 20 | 4 |
| 30 | 4 |
| 50 | 4 |
| 100 | 5 |

Known ground truth: the smallest 7-point general-position integral set has diameter **22,270** (Kreisel-Kurz
2008). Required bounding-box height H(n) explodes: H(4)≤20, H(5)≤100, …, H(7)≈15,700. A naive bounded
coordinate / Cayley-Menger solver (Z3) search cannot even reach n=7 at attainable heights, so it cannot
produce an n=8 non-existence certificate. Only structured Pythagorean-parametrization (the K-K method) reaches
those heights. Honest verdict on "Action Step 2 (Z3 CM search)": **not viable as stated.**

## Witness→Family run on the exact maxima (2026-07-26, OEC 0.4.0 Genesis)

First swing of the Frontier/Genesis arsenal at real Oracle data. Tool:
`oracle_epistemic_compiler.witness_family.WitnessFamilySynthesizer` (exact rational
arithmetic, no fitting tolerance — it either fits exactly or refuses).

Input: the ten exact maxima above, `p = 3..31`, both residue classes.

| test | degrees tried | result |
|---|---|---|
| polynomial family `max = f(p)` | ≤1, ≤2, ≤3, ≤4, ≤6 | **refused at every degree** |
| linearized growth law `max² = f(p)` | ≤1, ≤2, ≤3 | **refused at every degree** |
| linear recurrence in the sequence | order ≤4 | **refused** |
| `p ≡ 3 (mod 4)` alone (6 pts) | ≤4 | **refused** |
| `p ≡ 1 (mod 4)` alone (4 pts) | ≤2 | **refused** |

**Two results, both negative and both real:**

1. **No low-degree polynomial or linear recurrence describes the exact maxima.** This is
   consistent with — and mechanically corroborates — the √p shape, since √p is not polynomial
   in p. It is NOT a proof of the growth law; it removes a family of alternatives.
   Degree bound matters: with 10 data points a degree-9 polynomial interpolates *anything*, so
   only low degrees are a real test. Degrees ≤6 (7 coefficients) all refuse.

2. **`firewall_catch` is mechanically corroborated.** Split by residue class, **neither** class
   admits a meaningful polynomial fit. The two classes behave alike under this test — supporting
   the recommendation to state the theorem for all odd primes rather than `p ≡ 3 (mod 4)`.

**A VACUOUS FIT WAS CAUGHT AND DISCARDED.** The 4-point `p ≡ 1 (mod 4)` class initially
"fitted" a degree-3 polynomial (`-523/256 + 851/768·p - 17/256·p² + 1/768·p³`). **4 points with
4 coefficients is guaranteed interpolation** — it fits any 4 points and proves nothing. Reported
here because it would have read as "the residue class IS load-bearing", i.e. the exact opposite
of the truth. Only degree ≤2 is a real test on 4 points, and it refuses.

**What this does NOT do:** it does not close `growth_law`. That still requires the
Weil/character-sum argument. Ruling out low-degree polynomials is not proving a √p bound.

## ⭐ NEW EXACT VALUE: max(37) = 7 (computed 2026-07-26)

**First new exact maximum added to this finding since it was written.**

```
oracle/tools/epistemic/receipts/blade-p37.json
  prime 37 -> max 7    exhaustive branch-and-bound, 906.4 s
  witness independently_rechecked: true   (separate checker, crystallise doctrine)
```

| p | 3 | 5 | 7 | 11 | 13 | 17 | 19 | 23 | 29 | 31 | **37** |
|---|---|---|---|---|---|---|---|---|---|---|---|
| max | 2 | 2 | 3 | 4 | 4 | 4 | 5 | 5 | 6 | 6 | **7** |

**Why p=37 and not p=53/67** (which the earlier `extend_p` thread proposed): Mechanism War scored
p=53 and p=67 at **information gain 0.000** — every consistent hypothesis predicts the same value
there. p=37 was selected on **information per CPU-hour** (148/h vs 1.3/h for p=47).

**What it eliminated:** of the 150 `floor(a·√p+b)` pairs consistent with the previous ten maxima,
**29 are now dead; 121 survive.** Surviving band `a ∈ [1.06, 1.22]`, `b ∈ [−0.04, 0.60]`.

**`max(p) = floor(1.21·√p)` SURVIVED** — it predicted 7 and had every chance to be killed.
**Now exact on eleven primes.** Single-constant band unchanged at `a ∈ [1.2060, 1.2127)`.

**This does NOT close `growth_law`.** Still inductive; the Anti-Target barrier stands. Eleven points
is not a proof.

**Next experiment is now near-optimal:** at p=47 the 121 survivors split **59 / 62** (predicting 7 vs 8)
— close to a perfect coin-flip, so either outcome halves the remaining class. Estimated 2.6 CPU-h;
cost model validated at two points (p=23 error ×1.578, p=37 error ×1.23, band ±1.7).

> **Provenance note:** this run was **operator-initiated**, not selected and launched by the autonomy
> loop. The loop *did* independently select p=37 over the weapon's own pick of p=47 on
> information-per-hour, which is why p=37 was the prime computed.

## Genesis arsenal run (2026-07-26, OEC 0.4.0) — a sharper empirical law

**`max(p) = floor(1.21 · sqrt(p))` is EXACT on all ten measured primes.**

Found by Method Chemistry's fit stage (3-operator chain `fit_constant → repair_scope →
anti_target_barrier`; `single_operator_solution_exists: False`), then verified independently:

| p | 3 | 5 | 7 | 11 | 13 | 17 | 19 | 23 | 29 | 31 |
|---|---|---|---|---|---|---|---|---|---|---|
| `floor(1.21·√p)` | 2 | 2 | 3 | 4 | 4 | 4 | 5 | 5 | 6 | 6 |
| measured | 2 | 2 | 3 | 4 | 4 | 4 | 5 | 5 | 6 | 6 |

**The admissible constant band for a single-constant floor law is `a ∈ [1.2060, 1.2127)`** —
0.55% wide. This finding previously recorded only the ratio spread `max/√p ∈ [1.043, 1.206]`
and never derived that a *floor* law pins the constant this tightly. This law predicts
**max(47) = 8**, which is exactly the discriminating measurement identified above.

**It does NOT close `growth_law`.** Still inductive, still a fit to ten points; the Anti-Target
barrier below stands unchanged.

Related Genesis results on this data:
- **Theorem Repair** took the weaker `floor(1.2·√p)` (which fails at p=11) and repaired it to
  hold for `p ≥ 13` — exact on 6/6 there. Superseded by the 1.21 law, which needs no scope cut.
- **Move Genesis** invented the symmetry `(x,y) → (y, −x)` — a 90° rotation, which preserves
  `x²+y²` and hence the QR norm class. 7 of 1351 candidate affine maps preserve validity.
  **Usable to prune the search in `integral_distance_fp.py`.**
- **Mechanism Genesis** found no exact polynomial mechanism — the third independent tool
  (with Witness→Family and the consistency grid) agreeing the law is not polynomial in p.
- **Representation Genesis** found no exact quotient (3 candidates rejected for goal mixing,
  7 for transition mismatch). Honest "not found".

## Honest scope

Exact and verified, but small p (≤31 confirmed both classes). The growth law is an *empirical* fit, not a
proof; the constant C≈1.2 is not pinned. A proof would still need the Weil/character-sum argument. Larger p
(53, 67, …) would harden the fit and test the n=8 threshold.
