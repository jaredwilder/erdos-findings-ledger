# A claimed complete proof of Erdős 1210 is false at its first lemma

**Date: 2026-09-11. Found while mining this estate's own dossiers, and published the same hour.**

## The problem

> Let `A ⊆ [1,n)` be a set of integers such that `(a,b) = 1` for all distinct `a, b ∈ A`. Is it true
> that `Σ_{a∈A} 1/(n−a) ≤ Σ_{p<n} 1/p + O(1)`?

## What was claimed

A dossier in this estate files a route marked **PROVED** asserting the main proposition holds with
an explicit uniform constant **C = 1**, via two lemmas. An independent mining pass over the corpus
rated it *"the strongest thing in the range"* and *"answers the posed question outright."*

The first lemma, verbatim:

> **Lemma L1 (reduction).** If a₁,a₂ ∈ A are distinct and d = gcd(n−a₁, n−a₂), then aᵢ ≡ n (mod d),
> so d | gcd(a₁,a₂) = 1. Hence **B = {n−a : a ∈ A} is pairwise coprime**.

## Why it is false

From `d | n−a₁` and `d | n−a₂` it follows that `a₁ ≡ a₂ ≡ n (mod d)`, and therefore that
`d | a₁ − a₂`. **That is all that follows.** Concluding `d | gcd(a₁,a₂)` additionally requires
`d | n`, which is not given and is not true in general.

### The smallest counterexample

```
n = 5,  A = {1, 3}          A ⊆ [1,5),  gcd(1,3) = 1     hypothesis satisfied
B = {n−a} = {4, 2}          gcd(4, 2) = 2 ≠ 1            B is NOT pairwise coprime
```

L1 fails at n = 5.

### It is not an edge case

An exhaustive check over all n < 40 and all coprime pairs finds **1,625 counterexamples**. The first
several:

| n | A | B = {n−a} | gcd(B) |
|---|---|---|---|
| 5 | {1,3} | {4,2} | 2 |
| 7 | {1,3} | {6,4} | 2 |
| 7 | {1,4} | {6,3} | 3 |
| 7 | {1,5} | {6,2} | 2 |
| 7 | {3,5} | {4,2} | 2 |
| 8 | {2,5} | {6,3} | 3 |

Since L2 takes the pairwise-coprimality of B as its hypothesis, the chain collapses and **the claimed
proof establishes nothing**.

## What this does and does not mean

It does **not** refute the problem. The inequality holds comfortably at every counterexample above;
at n = 5, A = {1,3} the left side is 3/4 while `Σ_{p<5} 1/p = 1/2 + 1/3 = 5/6`. **Erdős 1210 remains
open.**

What is refuted is one route inside this estate that was filed as PROVED and then endorsed by a
downstream mining pass as the best result in its range. Nothing in the dossier retracts it.

## Why this is published

Because the failure mode is the dangerous one. The lemma is short, reads fluently, and its
conclusion is plausible. It survived being filed, being mined, and being ranked first out of a
110-problem range by a careful reader. It did not survive someone writing down `n = 5, A = {1,3}`.

A corpus of this size will contain more of these. The only defence is that claims marked PROVED are
treated as leads until a counterexample search has been run against them, which is exactly what
happened here, one hour before this file was written.
