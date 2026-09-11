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

Two campaigns carry a **refuted claim at a higher tier than its own correction**:

- **Erdős 943** — fifteen VAULT rows still stand at `PROVED_BY_SPEAKER` or
  `COMPUTATION_SUPPORTED` asserting a bound that a later row refutes.
- **Erdős 9** — the incorrect characterisation sits at `COMPUTATION_SUPPORTED`, its correction sits
  *below* it at `UNTESTED`.

**Anything reading the VAULT by rank picks the wrong row.**

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
| **400** | The `g₂` extremal table refuted by exact division: `g₂(2)=1` not 0, `g₂(9)≥2` not 1, and the filed `n=11` witness `(9,3)` gives `11!/(9!·3!) = 55/3 ∉ ℤ` | neither — the cleanest total drop of an exact computation |
| **859** | Claimed density table refuted by inclusion–exclusion: `d₃ = 2/3`, not the filed `1/3`; `d₅ = 2/5`, not `9/20` | neither |
| **1139** | Five consecutive `Ω ≥ 3` integers between the primes 241 and 247 — `242=2·11²`, `243=3⁵`, `244=2²·61`, `245=5·7²`, `246=2·3·41` | VAULT only |
| **535** | The frozen predicate refuted under **all three** readings, with a witness for each: `{1,4,5}` under 3-sum-free, `{2,3,5}` fails under sum-free, `{2,3,4}` fails under AP-free | neither |

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
