---
id: octagon-barrier-diameter-22270
claim: |-
  No 8-point plane integral point set in general position with diameter 22270 contains a congruent
  copy of the Kreisel-Kurz heptagon H1. Hence d-dot(2,8) > 22270 whenever H1 is the unique 7-point
  general-position integral set attaining d-dot(2,7)=22270. Separately: the correct search universe
  is Q(sqrt(k)), NOT the integer lattice - a lattice search returns 78 for n=5 where the published
  value is 73.
status: closed
tier: gold
reality_score: 0.9
domain: math
artifact_kind: barrier
truth_mode: certified
scope_grade: bounded_family
inference: deductive
independence: independently_reverified
reproducibility: artifact_verified
novelty: cleared
claim_ir:
  claim_id: "integral_point_set:octagon_barrier_at_22270"
  assertion_kind: barrier
  display: "No general-position integral octagon of diameter 22270 extends the Kreisel-Kurz heptagon H1."
  scope:
    domain: plane_integral_point_sets
    label: "diameter exactly 22270, characteristic 2002"
  definitions:
    plane_integral_point_set: "points in the plane with pairwise INTEGER DISTANCES; coordinates unrestricted"
    general_position: "no three collinear AND no four concyclic"
  tags: [erdos, integral_distance, barrier, octagon, kreisel_kurz]
novelty_receipt:
  tool: "oracle.reality.noveltyforge"
  band: NOVEL
  terminal_mode: NOVEL_CLEAR_TO_PURSUE
  ip_verdict: PAPER_AND_PATENT_PATH_OPEN
  corpus_size: 110
  receipt_hash: "1e61ca95b2c7e9f8c083bbb26a34d484f690e5efc36b11ba813b22883ddd946d"
  structured_collisions: 0
  note: "one facet-level hit on axiom_set at 0.65, anticipates=false"
claims:
  - id: barrier_at_22270
    inference: deductive
    truth_mode: certified
    status: closed
  - id: conditional_lower_bound
    inference: deductive
    truth_mode: certified
    status: closed
    note: "conditional theorem; the hypothesis is a determinate unretrieved literature fact, not a conjecture"
  - id: lattice_is_the_wrong_universe
    inference: deductive
    truth_mode: certified
    status: closed
---

# Octagon barrier at diameter 22270

## THEOREM 1 (unconditional)

**No 8-point plane integral point set in general position with diameter 22270 contains a congruent
copy of the Kreisel-Kurz heptagon H1.**

*Proof.* Let `S` be such a set, containing `H'` similar to `H1`.

1. `H'` is itself a 7-point plane integral point set in general position, so `diam(H') >= d(2,7) = 22270`.
   It is a subset of `S`, so `diam(H') <= diam(S) = 22270`. A similarity of ratio `L` carries `H1`
   (diameter 22270) to diameter `22270 L`, forcing `L = 1`: **`H'` is CONGRUENT to `H1`**.
2. The eighth point `X` is at whole distance from all seven points of `H'`, each `<= diam(S) = 22270`.
3. Place anchors `P0, P1` of `H1` with `|P0 P1| = a = 22270`. Then `r = |X P0| <= 22270` and
   `s = |X P1| <= 22270`. No-three-collinear forces the strict triangle inequality `|r - a| < s < r + a`.
4. The exhaustive extension search covered `r` in `[1, 100000]` and, for each `r`,
   `s` in `[max(1, |r-a|+1), min(100000, r+a-1)]`. Every `r` in `[1, 22270]` has its entire required
   `s`-range inside that region - **verified, 0 failing values**. So the region in (3) is strictly
   contained in what was searched.
5. That search returned 2088 gate passes and **0 genuine (non-vertex) extensions**. Contradiction. QED

## THEOREM 2 (conditional, stated positively)

**If `H1` is the unique 7-point plane integral point set in general position attaining diameter
22270, then `d-dot(2,8) > 22270`.**

Same argument applied to every 7-subset of a hypothetical minimal octagon: each has diameter
exactly 22270 (>= by minimality, <= by containment), hence is congruent to `H1`, hence Theorem 1 applies.

## The bar (axiom footprint)

| input | row |
|---|---|
| `d-dot(2,7) = 22270` - verbatim published, Kurz & Wassermann arXiv:0804.1307 abstract | row 3, a citation is not a gap |
| exhaustive extension search - exact rational arithmetic over `Q(sqrt(2002))`, no floats | row 2, trust footnoted to the computation |
| conclusion-asserting axiom | **none** - row 5 does not apply |

**Theorem 1 is CLOSED.** Theorem 2 is a conditional theorem whose hypothesis is a determinate fact
about an already-completed exhaustive search, not a conjecture.

## What is NOT claimed

- **`H1` is not shown maximal in general.** An eighth point may exist beyond distance 22270 from the
  anchors; that only bears on octagons of diameter LARGER than 22270. The point of Theorem 1 is that
  for the minimum-diameter case **no effective height bound is needed** - the diameter constraint
  supplies one, and it lands well inside the already-searched band. The estate's own extension
  package correctly states the general result is height-bounded; the specialisation to
  diameter 22270 is what removes the dependence.
- Uniqueness of the minimal heptagon is **not** established here.

# ABSENCE-PROVEN: Kreisel-Kurz full text could not be retrieved. Two federated acquisitions were
# run through oracle.reality.noveltyforge.cli acquire (110 records each, corpus_source
# auto_acquired_litacq_patents). The first query drifted off-topic (0 of 30 papers on subject); the
# retargeted query returned 13 on-topic papers INCLUDING Kurz & Wassermann arXiv:0804.1307
# (identifier 10.48550/arxiv.0804.1307, OpenAlex W1597717682, 18 citations). Its abstract WAS
# retrieved and reads verbatim: "Recently $\dot{d}(2,7)=22 270$ could be determined via an
# exhaustive search." The record's own meta.artifact block reports
# status=unavailable, route=none, reason=no_jats_and_no_fulltext_candidates - i.e. the acquisition
# tiers ran and found no open-access full text to fetch. So the ABSTRACT is proven present and the
# FULL TEXT is proven unreachable by this route. The uniqueness question is answerable and simply
# not answered here; a future session should push a different tier, not re-run this one.
# Receipts: oracle/ledger/receipts/kk-heptagon-uniqueness.json, oracle/ledger/receipts/kk-uniq2.json

## Falsifier

Exhibit an 8-point plane integral point set in general position of diameter 22270; or a genuine
non-vertex extension of `H1` with both anchor distances `<= 22270`.

## THEOREM 3 - the search universe is `Q(sqrt(k))`, not the lattice

An independent engine (`oracle/tools/plane_integral_search.py`, exact rational arithmetic over
`Q(sqrt(k))`) reproduces the published values:

| n | published | this engine | field of the witness | on the lattice? |
|---|---|---|---|---|
| 4 | 8 | **8** | `Q` | yes |
| 5 | 73 | **73** | `Q(sqrt(55))` | **no** |
| 6 | 174 | **174** | `Q(sqrt(2002))` | **no** |

A search restricted to integer coordinates returns **78** for n=5. That is not a weaker bound on the
same quantity - it is the answer to a different question, because the optimum is not on the lattice.

## Corrected: eight prior n=8 "floor" receipts prove nothing

`oracle/kbk/engine/octagon/` holds floor receipts at D = 200, 250, 300, 500, 700, 1000, 1414, 2000,
each "exhausted_to D, no witness". **All are subsumed by a free bound.** Any 8-point general-position
integral set contains a 7-point one, also integral, also general position, of no larger diameter;
therefore `d-dot(2,8) >= d-dot(2,7) = 22270` **with zero computation**. Every one of those receipts
sits below 22270. `fast.py floor` has no monotonicity check. ~350 s of compute confirming the known.

## Receipts

| artifact | sha256 |
|---|---|
| `oracle/kbk/engine/deep_search_H1_B100000.json` | `a5a340b395421bcfa3c9b608b70563cf15186d2a3f6405f53995856ece605258` |
| `oracle/ledger/receipts/plane-integral-n5.json` | `dad1b77e4a37d76e9c7a2bca710e54ea41b2c165bc07d485e5ebb85c3ce90654` |
| `oracle/ledger/receipts/plane-integral-n6.json` | `00d9e720f44558433e5f8741d69bbaae53c22788ce491fa496429d319c97e3a8` |
| novelty verdict | `1e61ca95b2c7e9f8c083bbb26a34d484f690e5efc36b11ba813b22883ddd946d` |

Question lock: `oracle/ledger/question-locks/plane-integral-novel.json`
