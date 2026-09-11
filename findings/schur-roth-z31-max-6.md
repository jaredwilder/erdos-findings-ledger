---
id: schur-roth-z31-max-6
claim: |-
  A subset of Z/31Z that is simultaneously sum-free (A+A disjoint from A, INCLUDING doublings a+a)
  and free of nontrivial three-term arithmetic progressions has at most 6 elements. Sharp:
  {1,3,7,15,20,24}. The complete extremal layer is 330 six-element sets and zero seven-element sets,
  falling into exactly 12 orbits under unit dilation, of sizes 15, 15 and 30 (ten times).
status: closed
tier: gold
reality_score: 0.95
domain: math
origin: external_drop
artifact_kind: classification
truth_mode: certified
scope_grade: bounded_family
inference: deductive
independence: independently_reverified
reproducibility: artifact_verified
novelty: cleared
claim_ir:
  claim_id: "additive_combinatorics:schur_roth_z31_max"
  assertion_kind: classification
  display: "Max size of a simultaneously sum-free and 3-AP-free subset of Z/31Z is 6; 330 extremizers in 12 unit-dilation orbits."
  scope:
    domain: additive_combinatorics
    label: "the single cyclic group Z/31Z - a finite exhaustive result, NOT a general-n theorem"
  definitions:
    sum_free: "(A+A) INTERSECT A empty, where A+A ranges over ALL ordered pairs INCLUDING a+a"
    three_ap_free: "no a, a+d, a+2d all in A with d nonzero mod 31; 31 odd prime so all three terms are automatically distinct"
    heredity: "both conditions are universally quantified over elements, so every subset of a valid set is valid"
  tags: [additive_combinatorics, sum_free, arithmetic_progression, extremal, exhaustive]
novelty_receipt:
  tool: "oracle.reality.noveltyforge"
  band: NOVEL
  terminal_mode: NOVEL_CLEAR_TO_PURSUE
  ip_verdict: PAPER_AND_PATENT_PATH_OPEN
  corpus_size: 110
  receipt_hash: "840f9609e455cd3b9674a0ff0644068e2268c1e8b30d37b8b0fe2b1f5f24c76c"
  top_collision: "US10133620 (a patent, unrelated to the mathematics)"
  note: "OUR verdict, not the vendor's. The vendor ran their own search; the system decides novelty."
claims:
  - id: max_cardinality_6
    inference: deductive
    truth_mode: certified
    status: closed
  - id: extremal_layer_330
    inference: deductive
    truth_mode: certified
    status: closed
  - id: twelve_unit_dilation_orbits
    inference: deductive
    truth_mode: certified
    status: closed
---

# Simultaneously sum-free and 3-AP-free subsets of Z/31Z: the maximum is 6

## THEOREM

Let `A` be a subset of `Z/31Z` such that

1. `(A + A)` is disjoint from `A` — **including the doubling case `a + a`**, and
2. `A` contains no nontrivial three-term arithmetic progression.

Then `|A| <= 6`. The bound is **sharp**: `{1, 3, 7, 15, 20, 24}` attains it.

Moreover the complete extremal layer is: exactly **330** valid 6-element subsets, exactly **0**
valid 7-element subsets, partitioned into exactly **12** orbits under the unit-dilation action of
`(Z/31Z)*`, of sizes **15, 15, and 30 with multiplicity ten**.

`|A| <= 6` follows from the empty 7-layer by **heredity**: both conditions are universally
quantified over the elements of `A`, so every subset of a valid set is valid. A set of size `>= 7`
would contain a valid 7-subset, and there are none.

## ORIGIN AND INDEPENDENCE — read this before citing

This theorem was **produced by MathFire 7.0.0**, an external deterministic drop
(release zip sha256 `a3a653f7d8948a66c3a242c7e8d5d0755cdc742c4d03cc705ef4d402a70ec95f`, verified
on receipt). **It is not this estate's discovery.** What this estate contributes is an
INDEPENDENT re-derivation and an independent novelty verdict.

`oracle/library/patents/artifacts/verify_schur_roth_z31.py` was written from the English statement
alone, before reading any vendor source, and shares no code with the vendor implementation. It
enumerates all `C(31,6) = 736,281` and `C(31,7) = 2,629,575` subsets with no pruning, no symmetry
reduction and no early exit. It reproduces:

| quantity | vendor | this estate |
|---|---|---|
| valid 6-subsets | 330 | **330** |
| valid 7-subsets | 0 | **0** |
| first witness | `{1,3,7,15,20,24}` | **identical** |
| unit-dilation orbits | 12, sizes 15/15/30x10 | **12, `{30: 10, 15: 2}`** |

The verifier also carries **negative controls** — sets it must REJECT (`{1,2,3}` has a 3-AP;
`{1,2,4}` fails sum-freeness via `2+2=4`) — because a gate that never fires is not a gate.
11/11 checks pass.

## THE DEFINITIONS ARE THE WHOLE BALLGAME

An English phrase like "sum-free" hides two forks, and the other branch gives a different answer.
Pinned here because a mismatch between prose and code is the likeliest place for an inflated claim:

- **Doubling is included.** `(A+A)` ranges over all ordered pairs including `a+a`, so `2a mod 31`
  is forbidden from `A` for every `a in A`. Restricting to distinct summands is a weaker condition.
- **Nontrivial 3-AP** means `a, a+d, a+2d` with `d != 0`. Since 31 is an odd prime, `d != 0` already
  forces all three terms distinct, so this is exactly the degenerate-free reading.
- **`0` is admissible in principle** and self-excluding in practice: `0 in A` gives `0+0 = 0 in A`.
- The two conditions are **independent** — sum-freeness forbids `a+b` from landing in `A`; the 3-AP
  condition forbids a middle-term pattern. Neither implies the other.

The vendor's prose and the vendor's code agree with each other and with this reading; that was
checked, not assumed.

## Digest — RESOLVED, and it was worth chasing

MathFire publishes `8fdf96cadc52fee0a0b6f8543a15d993489bf00ac12a2ac312cff93cccef2605` for the
canonical extremal layer. The first estate verifier computed
`a237ce11cd091c0f1905147a40ec1386946c6bcba0864a73fa3a0d8e9545595c` for the same 330 sets — a
different **serialisation** (newline-joined, comma-separated tuples), not different mathematics.

**A second, independent estate implementation then reproduced `8fdf96ca…2605` exactly.** So the
digest is confirmed, and by a path that is not the vendor's. This mattered: the vendor's own C
verifier corroborates **counts and orbit structure only** and never computes a digest, so before
this the published hash rested on the vendor's two Python paths alone.

A digest binds a byte encoding, not a mathematical object. Recorded rather than smoothed over,
because a hash mismatch that turns out to be benign still has to be *shown* to be benign.

## The doubling convention is LOAD-BEARING — measured, not argued

Excluding the `a + a` case (i.e. requiring only distinct summands) does not weaken the theorem
slightly. It **breaks it**: the count becomes **1740** six-element sets and the maximum becomes
**7**. Every figure in this finding depends on doubling being included.

The vendor's `NOVEL_RESULT.md` states "with repeated summands allowed" explicitly, and the code
(`frontier7/linear_avoidance.py:120-123`, iterating `values[i:]`) matches. Prose and implementation
agree. All four definitional variants were run to confirm which one produces the published numbers.

## ⛔ THE THEOREM IS TRUE. THE OPERATIONS THAT "PROVE" IT ARE NOT A PROOF OF IT.

Three Round-7 operations — `schur_roth_z31_theorem`, `schur_roth_z31_independent_replay`,
`schur_roth_z31_orbit_classification` — are **constant-verdict**. `solve` reads
`n = int(data.get("modulus", 31))` and never uses it; `verify` hardcodes 330/0/12.

Measured through the real planner: change the modulus to 7, or to 12 with the statement reworded
to Z/12Z, or swap in an unrelated vacuous pattern — every run still returns `goal_verdict: proved`,
`goal_satisfied: True`, `result.modulus: 31`. **The certificate binds the problem hash of a Z/12Z
problem to a Z/31Z proof.**

This is worse than a false theorem, because the answer is correct and so nothing downstream looks
wrong. It is the same disease this estate keeps catching in itself: **a right answer to a question
nobody asked.** All three are quarantined in `oracle/reality/frontier_arsenal/mathfire_blade.py`.

The theorem stands on the two independent estate re-derivations, not on those operations.

## Scope — what this is NOT

- **This is one modulus.** It is a finite exhaustive result about `Z/31Z`, not a theorem about
  `Z/nZ` for general `n`, and nothing here establishes a growth law or an asymptotic.
- No claim is made that the maximum is 6 for any other modulus.
- The vendor's own `LIMITS.md` states the generic forge defaults to cyclic moduli at most 18
  because several operations enumerate all subsets; this result at 31 is a special-cased lane.

## Falsifier

Exhibit a 7-element subset of `Z/31Z` that is sum-free (including doublings) and free of nontrivial
3-APs. Or produce a published source stating the maximum 6, the count 330, or the 12-orbit
classification for this simultaneous condition.

## Receipts

| artifact | value |
|---|---|
| MathFire 7.0.0 release zip | `a3a653f7d8948a66c3a242c7e8d5d0755cdc742c4d03cc705ef4d402a70ec95f` |
| independent verifier | `oracle/library/patents/artifacts/verify_schur_roth_z31.py` (11/11, with negative controls) |
| novelty verdict (ours) | `840f9609e455cd3b9674a0ff0644068e2268c1e8b30d37b8b0fe2b1f5f24c76c` |
| vendor theorem certificate | `receipts/round7-novel-result-proof.json` inside the drop |
