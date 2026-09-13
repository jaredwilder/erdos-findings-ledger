# Erdős #1056 — repeated-singleton “solution” is semantic domain drift

**Status:** historical close INVALID; Erdős #1056 remains OPEN.  
**Source:** Pass-3 internal campaign, route R001/T1.

## Canonical problem

For every `k>=2`, does there exist a prime `p` and `k` **consecutive intervals**

`I_1,...,I_k`

such that

\[
\prod_{n\in I_i}n\equiv1\pmod p
\]

for every `i`?

The intended intervals are successive adjacent blocks, as in the historical examples.

## The mined false close

A historical transference packet argued that the literal statement allowed

\[
p=2,\qquad I_1=\cdots=I_k=\{1\}.
\]

Each singleton has product `1`, so the packet filed:

`LEMMA_VERDICT ... status=PROVED`

and said this supplied the affirmative close for every `k`.

That is not an instance of the canonical object.

## Exact semantic failure

“Consecutive intervals” does not mean merely that every `I_i` is itself an interval of consecutive integers. The intervals are **successive adjacent intervals** cut out by increasing endpoints.

The current Formal Conjectures encoding makes this explicit. It quantifies a boundary map

`boundaries : Fin (k+1) -> Nat`

with

`StrictMono boundaries`

and defines interval `i` as

`Ico (boundaries i) (boundaries (i+1))`.

Under that semantics, equal repeated singleton intervals are impossible: strict monotonicity forces successive boundaries, hence ordered non-overlapping blocks.

The historical examples agree:

- `k=2`, `p=11`: blocks `{3,4}` and `{5,6,7}`;
- `k=3`, `p=17`: blocks `{2,3,4,5}`, `{6,...,11}`, `{12,13,14,15}`.

Thus the repeated-singleton witness changes the domain rather than solving the stated problem.

## Additional degenerate check

Even if one required only **disjoint** nonempty intervals rather than the full adjacent-boundary semantics, the proposed `p=2` construction still collapses: the only positive singleton with odd product beginning at 1 is `{1}`, so one cannot take two disjoint copies of it.

Allowing empty intervals would create a different trivialized problem because the empty product is `1`; that is another semantic variant and not the intended canonical question.

## Correct disposition

- arithmetic fact `product({1}) = 1 mod 2`: TRUE;
- repeated-singleton tuple as a canonical #1056 witness: FALSE / OUTSIDE DOMAIN;
- R001/T1 “all k” close: **RETRACTED**;
- Erdős #1056: **OPEN**.

The current public problem page records finite constructions for small `k` and newer partial progress, but not a solution for arbitrary `k`.

## References

- Erdős Problem #1056: https://www.erdosproblems.com/1056
- Formal Conjectures, `ErdosProblems/1056.lean`, whose `StrictMono boundaries` condition freezes the adjacent-interval semantics.
