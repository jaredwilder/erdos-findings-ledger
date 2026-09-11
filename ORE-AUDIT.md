# An audit of our own ore

A 30,438-object ore corpus was mined out of this estate's own output, carrying 2,260 objects marked
`PROVED`, 278 `COMPUTED` and 53 `REFUTED`, plus 66,330 edges and 1,043 "multi-hop implication
chains". On 2026-09-11 an independent pass read it adversarially.

**The corpus is worth less than its headline numbers suggest, and the reasons are specific.**

Three of the findings below were re-checked directly against the files before publishing here, and
are marked **[re-checked]**. The rest are the audit's, reported as its findings.

---

## 1. There are no implication chains. **[re-checked]**

The 66,330 edges carry exactly five relation types:

| relation | count |
|---|---|
| `OCCURS_IN` | 33,213 |
| `COMPOSES` | 17,258 |
| `DERIVED_FROM` | 11,369 |
| `DUPLICATES` | 4,033 |
| `USES` | 457 |

**Every one is text provenance, not mathematics.** The most common evidence strings are file paths,
and `DERIVED_FROM` edges carry evidence of the form `container->contained: object read from ...` —
meaning a substring was extracted from a longer string, not that a theorem follows from another.

The audit built the graph and walked it: **338 edges connect two `PROVED` nodes, and there are zero
3-hop paths among `PROVED` nodes.**

A name like `DERIVED_FROM` invites exactly the misreading this note exists to prevent.

## 2. The 1,043 "multi-hop implication chains" are a lexical artifact.

They are built by overlapping-text similarity, with mean stitch similarity around 0.39 to 0.51. In
the length-2 chains, both steps are **literally the same sentence, taken from two copies of the same
file** (`campaign-log.json` and `results.json`). In the length-5 chains, the same three sentence
fragments reappear in permuted order.

Length distribution: 784 of length 2, 200 of length 3, 53 of length 4, 6 of length 5. The audit
reports that no chain it inspected is a mathematical derivation.

## 3. 54 of 362 rows marked `VERIFIED` carry a non-zero exit code. **[re-checked]**

The orphan-declaration verdict table holds 664 rows: 362 `VERIFIED`, 273 `FAILED`, 29
`VERIFIED_DIRTY`. Of the 362 marked `VERIFIED`, **54 have `exit_code != 0`**, across 14 problems
including erdos101, erdos145, erdos218, erdos406, erdos413, erdos595, erdos600, erdos1049 and
erdos1104.

Reported failure modes include `unsolved goals`, `Type mismatch`, and parse errors from a harness
bug that emits `theorem <wrapper> : theorem <real_name> ...`.

**Anything sourced from that column needs the exit code checked before it is cited.**

## 4. Five files declare a published theorem as an axiom, and carry `sorryAx`. **[re-checked]**

| file | the axiom it declares |
|---|---|
| `erdos101/lap_fmz_...` | `axiom MelchiorGreenTao_OrdinaryLineBounds` |
| `erdos1104/lap_fmz_...` | `axiom PublishedTheorem_Kim1995` |
| `erdos145/lap_fmz_...` | `axiom PublishedTheorem_Mirsky1949` |
| `erdos406/lap_fmz_...` | `axiom PublishedTheorem_SengeStraus1971` |
| `erdos600/lap_fmz_...` | `axiom PublishedTheorem_Rodl1985` |

Each of their axiom footprints also mentions `sorryAx` — one to five times.

Asserting a cited theorem as an axiom is a legitimate technique **when it is labelled**, because the
result is then conditional on the citation rather than kernel-proved. Combined with `sorryAx` in the
footprint, these files cannot support an unqualified claim of kernel verification.

**None of these five files, and none of the contaminated verdict table, is in any public
repository.** This audit was run before they could become one.

## 5. The ore is heavily duplicated and internally contradictory.

Of 2,591 `PROVED`/`COMPUTED`/`REFUTED` objects, the audit found 211 pure infrastructure and 275
carrying no number at all. One problem, Erdos 400, holds 32 `PROVED` objects of which roughly 20
restate the same trivial witness.

Several problems carry mutually inconsistent `PROVED` claims: Erdos 653 asserts both `g(n) >= n-1`
and `g(n) <= n-2`; Erdos 683 carries a counterexample at (10,3) alongside a claim that the same
inequality holds for all n <= 12; Erdos 170 contradicts itself throughout, and **all 53 `REFUTED`
objects in the entire corpus belong to that one problem**, several of them refuting each other.

## 6. One constant the audit could not reproduce

An object derives `c <= 0.20905` from the instance (10,5). The audit could not reproduce it, noting
that `min(n-k+1, k^(1+c)) = min(6, 5^(1+c)) <= 6 <= P = 7` holds for every c, so the instance
appears to force nothing. **That constant should be treated as unverified until someone re-derives
it.**

---

## What survived, and it is real

The same pass identified six files whose Lean it read in full and found genuinely clean, with
footprint exactly `[propext, Classical.choice, Quot.sound]`, `sorry = 0`, `axiom = 0`:
**Erdos 477, 700, 885, 936, 479 and 456.** All six are already published in
[erdos-theorems](https://github.com/jaredwilder/erdos-theorems).

The best single line in the whole corpus is a self-correction attached to Erdos 700. The kernel
proved `gcd(21, C(21,7)) = 3`, and the object records that this **contradicts a standing record in
this estate which claimed f(21) = 7 via `gcd(21, C(21,7)) = 9` — impossible, since 9 does not divide
21.**

## Why publish an audit of your own corpus

Because the headline numbers — 30,438 objects, 2,260 proved, 66,330 edges, 1,043 chains — are the
numbers someone would quote, and four of those five are misleading without this page. A corpus that
reports its own duplication rate, its own contaminated column and its own contradictions is worth
more than one that reports only its size.
