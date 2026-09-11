# Where the mathematics goes: a sweeper that cannot see its own best work

**An audit of all 226 transcript-bearing campaigns, 2026-09-11. 12,065 records streamed.**

This is the explanation for something that took two days to notice. Across this release, the richest
unpublished seam was always refutations — results whose value is closing off a route. I had assumed
a filter trained on "did we get something" discarded them.

**That was wrong, and the real reason is worse.**

---

## The finding

Of 25 results verified individually in this pass, **zero reached a human findings document in
recognisable form.** Nine reached the machine's VAULT only. Twelve reached neither.

The mechanism: **the sweeper reads `LEMMA_VERDICT` lines.** But the machine does its actual
constructing inside `BOUNDARY_AUDIT`, `TESTS` and `COUNTEREXAMPLES` prose — and none of that is a
verdict line. The best mathematics in the estate is produced in exactly the place the promotion
pipeline does not look.

351 non-`NONE` `COUNTEREXAMPLES` fields exist across 206 campaigns. **About 60 were read.** A second
pass over the same field would likely yield another fifteen of comparable quality.

## The VAULT is not append-safe

> **Corrected 2026-09-11, same day, after re-reading the VAULT directly.** The first version of this
> section said "fifteen VAULT rows" for Erdős 943 and implied the supersession machinery was
> unused. **Both were wrong**, and the corrected version is narrower. The original text is kept
> below the correction so the overstatement stays visible.

**The supersession machinery is in use.** `superseded_by` is set on **4,242 of 6,882 rows**, and all
221 problems holding a `REFUTED` row have at least one link set somewhere. Any claim that the field
"exists and is simply not set" is false.

**A screen that flags 198 of 225 problems is not a finding.** Keying on the problem id flags every
problem where a refuted row and an unsuperseded higher-tier row coexist — but a problem legitimately
holds a refuted claim and a proved claim about **different sub-statements**, and mathematics here is
done per lemma, not per problem. Spot-checking two of the worst-flagged:

- **Erdős 479** (3 refuted, 19 unsuperseded higher) — the refuted rows are about a verifier abort, a
  parity claim, and a truncated standing lemma. The kernel rows are about `k=0` witnesses,
  congruence algebra, and a 2-adic valuation. **Different statements. Not a conflict.**
- **Erdős 936** (9 refuted, 18 higher) — the kernel row already carries `{9, 25, 121, 5041}`, which
  is exactly the list the refutation corrected. **The correction had already propagated.**

**One inversion survives and is confirmed by hand.** Erdős 943 holds a `REFUTED` row giving
`f(153) = 8` against `τ(153) = 6`, while an unsuperseded `PROVED_BY_SPEAKER` row in the same VAULT
still asserts `f(n) ≤ τ(n) for ALL n exactly`. Same statement, both live, no link between them. The
true tier counts for that problem are 5 `PROVED_BY_SPEAKER` and 8 `COMPUTATION_SUPPORTED`, not
fifteen.

<details>
<summary>The original, overstated version</summary>

> Two campaigns carry a **refuted claim at a higher tier than its own correction**:
>
> - **Erdős 943** — fifteen VAULT rows still stand at `PROVED_BY_SPEAKER` or
>   `COMPUTATION_SUPPORTED` asserting a bound that a later row refutes.
> - **Erdős 9** — the incorrect characterisation sits at `COMPUTATION_SUPPORTED`, its correction
>   sits *below* it at `UNTESTED`.
>
> **Anything reading the VAULT by rank picks the wrong row.**

The Erdős 943 row count was wrong, and the section generalised one confirmed case into a structural
claim about the VAULT that the row data does not support.

</details>

## The strongest single item, verified here

**Erdős 943.** A `status=PROVED` close was filed asserting `f(n) ≤ τ(n)`, on the argument that
`a ↦ a` injects a representation `n = ab` into the divisors of `n`.

The auditor's counterexample, re-verified independently:

```
153 = 9 + 144 = 25 + 128 = 32 + 121 = 72 + 81
```

Every part is powerful — `9=3²`, `144=2⁴·3²`, `25=5²`, `128=2⁷`, `32=2⁵`, `121=11²`, `72=2³·3²`,
`81=3⁴`. That is **8 ordered representations**, against

```
τ(153) = τ(3² · 17) = 6
```

**8 > 6. The bound fails.**

The error is exact and instructive: `1_A ∗ 1_A` counts `n = a + b`, not `n = a · b`. The injection is
valid for products and invalid for sums. **An additive statement read as a multiplicative one** —
and it was filed as PROVED by the most expensive model in the fleet, then refuted two records later
in the same transcript, and the refutation never left the file.

## Eight more that never reached a findings document

| problem | what was established | where it went |
|---|---|---|
| **727** | A proved target-equivalence `(n+k)!² ∣ (2n)!` ⟺ a prime-valuation condition, plus an **infinite counterexample family** (`k=2`, `n=2m`, `m=1+2^a+2^b`; instances 14, 26, 38, 50, …) and a named barrier: fixed-multiplier short-interval mechanisms die to unbounded prime gaps | one verdict line to VAULT; the equivalence and enumeration nowhere |
| **251** | The filed derivation's engine refuted — `E_n = 2^n(S−S_n)` does **not** tend to 0, it grows like `2p_{n+1}` — then **repaired, both directions closed** | neither VAULT nor findings; filed `UNTESTED` |
| **329** | Translation-invariance obstruction killing an entire Sidon block-construction family: `{0,1,3}` and `{0,1,3,9}+T` collide for **any** `T`, because cross-sum collisions depend on within-block differences | neither |
| **855** | `π(x+y) ≤ π(x)+π(y)` fails **exactly** on `{(1, p−1) : p prime}`, excess exactly 1 — and a correction to the certificate it audits at `x=y=3` | bare `(1,1)` to VAULT; the characterisation nowhere |
| **400** | The `g₂` extremal table refuted by exact division | **see the correction below — this row is sharper than "neither"** |
| **859** | Claimed density table refuted by inclusion–exclusion: `d₃ = 2/3`, not the filed `1/3`; `d₅ = 2/5`, not `9/20` | neither |
| **1139** | Five consecutive `Ω ≥ 3` integers between the primes 241 and 247 — `242=2·11²`, `243=3⁵`, `244=2²·61`, `245=5·7²`, `246=2·3·41` | VAULT only |
| **535** | The frozen predicate refuted under **all three** readings, with a witness for each: `{1,4,5}` under 3-sum-free, `{2,3,5}` fails under sum-free, `{2,3,4}` fails under AP-free | neither |

## Correction, published within the hour: what survived was the verdict, not the proof

My first version of this page said the Erdős 400 refutation reached "neither VAULT nor findings."
**That was slightly wrong, and the accurate version is a worse indictment.**

A downstream DAG node *did* carry the verdict forward, as prose:

> *"RETRACTED by author boundary audit: … the universal lower bound (true, witness (n,1)) was
> conflated with exact maxima … the spike values and witnesses contain concrete arithmetic errors."*

**What did not survive is the arithmetic that did the refuting.** Searching the entire rescue tree
for `120960`, `2177280` or `55/3` returns nothing, and no VAULT row contains them. These three facts
exist only in the transcript, and each is checkable in seconds — I checked all three:

```
9!  / (7!·4!)  =  362880 / 120960   =  3 exactly
        so (7,4) is admissible at n=9 and g₂(9) ≥ 7+4−9 = 2, against the filed 1

11! / (9!·3!)  =  39916800 / 2177280  =  55/3  ∉ ℤ
        so the filed n=11 witness (9,3) is INADMISSIBLE, not merely suboptimal

2!·1! = 2  divides  2! = 2
        so g₂(2) = 1, against the filed 0
```

**The pipeline preserved "this was wrong" and discarded "here is why, exactly."**

A retraction without its counterexample cannot be re-checked, cannot be reused, and cannot stop the
same error recurring. It is the least useful half of a refutation to keep, and it is the half that
was kept.

Two further facts from the same check:

- That campaign produced **at least two distinct refutations** and the ledger kept one and lost the
  other. The VAULT holds a separate `REFUTED` row for `n=24` with witness `(13,13)`. **Flagging
  rather than asserting:** `24!/(13!·13!)` is not an integer either, so that surviving row's witness
  may have the same admissibility defect as the one it refutes. Worth checking before reuse.
- The audit's own "found in findings" hits for Erdős 943 and 890 were **false positives** — a
  generic phrase matched rows belonging to different problems. Tight-pattern re-checks confirm both
  are genuinely absent.

## One the audit itself got wrong

Erdős 890's L3 line claims `min S₃(n) = 1` for `n ≥ 2` with witness `n = 4`. That is false at its own
endpoint: 2, 3, 4 are three consecutive 3-smooth integers, so `S₃(2) = 0`. **No audit caught it.**
Recorded here so the next reader does not inherit it.

## What this changes

The fix is not to publish harder. It is that **a promotion pipeline keyed on verdict lines will
systematically lose the mathematics done in audit prose**, and in this estate that is where the
constructing happens. Every refutation in this release was recovered by reading transcripts directly
rather than by anything the machine promotes.

The estate convicts itself constantly and well. It just has no mechanism for *keeping* the
convictions.
