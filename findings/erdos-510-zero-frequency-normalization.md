# Erdős #510 — zero-frequency normalization and false trivial close

**Status:** statement-normalization correction; Chowla's cosine problem remains OPEN.  
**Source:** Pass-3 internal campaign `erdos510-campaign-001` plus current public statement surfaces.

## The issue

One public prose form of Erdős #510 says:

> If `A subset Z` is a finite set of size `N`, is there an absolute `c>0` and `theta` such that
> \[
> \sum_{n\in A}\cos(n\theta)<-cN^{1/2}?
> \]

Taken literally for every finite subset of `Z`, this has immediate degenerate obstructions because the frequency `0` contributes the constant term `1`.

For example,

\[
A=\{0\}
\]

gives

\[
\sum_{n\in A}\cos(n\theta)=1
\]

for every `theta`, so no negative bound is possible.

Likewise

\[
A=\{0,1\}
\]

gives

\[
1+\cos\theta\ge0
\]

for every `theta`.

A historical internal route therefore filed a trivial negative close on the frozen `A subset Z` wording.

## Why this is not a solution of the intended problem

The current Formal Conjectures encoding freezes a nondegenerate asymptotic version:

- `A` is a finite set of natural-number frequencies;
- `0 notin A`;
- the universal claim is only required **eventually in `N`**.

Schematically it asserts the existence of `c>0` such that for all sufficiently large `N`, every `N`-element `A` with `0 notin A` has some `theta` satisfying

\[
\sum_{n\in A}\cos(n\theta)<-c\sqrt N.
\]

The known Bedert and Ruzsa variants on the same formalization use the same `0 notin A` / eventual-`N` normalization.

Therefore the `{0}` and `{0,1}` examples diagnose a **statement-freeze mismatch**, not the mathematical content of Chowla's intended open problem.

## Permanent estate rule for #510

Any future theorem/certificate/reconstruction for #510 must state its normalization explicitly.

### Canonical working form

Use the nonzero-frequency, sufficiently-large-`N` form unless the historical source being studied explicitly requires another normalization.

### Invalid close

Do **not** promote

`A={0}` or `A={0,1}`

as a disproof of the intended Chowla cosine problem.

They only refute the unqualified literal variant that permits zero frequency and demands the estimate at every small cardinality.

## Why the distinction matters

Adding frequency zero shifts the cosine polynomial by the constant `1`:

\[
\sum_{n\in A\cup\{0\}}\cos(n\theta)
=1+\sum_{n\in A}\cos(n\theta).
\]

For asymptotic polynomial-size negative bounds this additive constant is harmless once the statement is formulated for sufficiently large `N`, but at tiny `N` it completely changes truth values. Thus both qualifiers—nonzero frequencies and eventual `N`—are semantic rather than cosmetic.

## Current public status

The intended problem is still open. Current public notes record the best known polynomial exponent `1/7` (Bedert), while the conjectured `N^{1/2}` scale is optimal in order because of Sidon-difference-set examples.

References:

- Erdős Problem #510: https://www.erdosproblems.com/510
- Google DeepMind Formal Conjectures, `ErdosProblems/510.lean`

This file is a normalization/correction record, not a new bound.
