# Erdős #197 — anchor-chain obstruction for 3-AP-free enumerations

**Status:** unconditional necessary-condition theorem; Erdős #197 remains OPEN.  
**Novelty:** no historical priority claim. The lemma was extracted from the Pass-3 campaign and independently re-derived; the literature contains a substantial theory of subsets admitting monotone-3-AP-free permutations, including recent density results.

Call an infinite set `S subset N` **3-permutable** if it admits a bijective enumeration with no monotone three-term arithmetic progression.

## Theorem — every anchor chain has infinitely many holes

Let `S subset N` be infinite and 3-permutable. Fix any

\[
v\in S
\]

and any odd positive integer `o`. Then `S` omits infinitely many members of the dyadic anchor chain

\[
\boxed{
C(v,o)=\{v+2^k o:k\ge0\}.
}
\]

Equivalently, `S` contains no tail of `C(v,o)`.

### Proof

Let `p:S->N` be the position map of a 3-AP-free enumeration of `S`, and fix `v in S`.

Only finitely many members of `S` occur before `v`; write

\[
Q=\{x\in S:p(x)<p(v)\}.
\]

Suppose for contradiction that `S` contains a tail of `C(v,o)`. Since `Q` is finite, choose `k_0` so large that

\[
y_k:=v+2^k o\in S\setminus Q
\qquad(k\ge k_0).
\]

Hence

\[
p(y_k)>p(v)
\qquad(k\ge k_0).
\]

But for every such `k`,

\[
v,\ y_k,\ y_{k+1}
\]

is an increasing three-term arithmetic progression, because

\[
y_{k+1}=2y_k-v.
\]

To avoid a monotone occurrence in the enumeration, the three positions cannot satisfy

\[
p(v)<p(y_k)<p(y_{k+1}).
\]

Both `y_k` and `y_{k+1}` occur after `v`, so necessarily

\[
p(y_{k+1})<p(y_k).
\]

Thus

\[
p(y_{k_0})>p(y_{k_0+1})>p(y_{k_0+2})>\cdots,
\]

an infinite strictly decreasing sequence of natural numbers. Contradiction.

Therefore no tail of the chain lies in `S`, which is equivalent to infinitely many omissions.

## 2-adic partition consequence

For fixed `v`, every integer `x>v` has a unique representation

\[
x-v=2^k o
\]

with `o` odd. Thus the chains `C(v,o)` over odd `o` partition the integers above `v`.

The theorem therefore says something stronger than ordinary sparseness: around **every one of its own anchor points**, a 3-permutable set must keep punching holes forever in every dyadic ray.

## Corollary — no full dyadic congruence-class tail

If `S` contains `v` and, for some `j`, contains every sufficiently large integer congruent to `v mod 2^j`, then `S` is not 3-permutable.

Indeed, for every odd `o`, all sufficiently large

\[
v+2^k o\qquad(k\ge j)
\]

belong to that residue class, so `S` contains a tail of an anchor chain.

In particular, a complete residue class modulo a power of two cannot itself be one of the two desired parts in Erdős #197.

## Recovery of the classical `N` obstruction

Taking `S=N`, `v=1`, and `o=1`, the theorem yields the chain

\[
2,3,5,9,17,\ldots
\]

and immediately proves that no permutation of all positive integers avoids monotone 3-term arithmetic progressions. That global fact is classical (Davis–Entringer–Graham–Simmons, 1977); the present interest is the anchored-subset necessary condition.

## Relation to Erdős #197

Problem #197 asks whether

\[
N=A\sqcup B
\]

can be partitioned so that both `A` and `B` are 3-permutable.

Any affirmative construction must therefore satisfy the anchor-chain obstruction **simultaneously in both colors**:

> for every `v in A` and every odd `o`, infinitely many points of `C(v,o)` lie in `B`; and symmetrically with `A,B` reversed.

This rules out a broad family of naive periodic, residue-class, or eventually periodic partitions. It does not decide whether a sufficiently irregular two-coloring exists.

## Literature boundary

The subject is active. Erdős #197 is currently still listed as open. Recent work of Jesse Geneson studies the density of subsets of `N` and `Z` admitting `omega`-permutations with no monotone 3-term AP and proves, among other things, an upper-density lower construction of at least `2/3` for `N`. The exact anchor-chain formulation above was not located in the targeted literature search, but no novelty claim is made without a comprehensive historical audit.

References:

- Erdős Problem #197: https://www.erdosproblems.com/197
- J. A. Davis, R. C. Entringer, R. L. Graham, G. J. Simmons, *On permutations containing no long arithmetic progression*, Acta Arith. 34 (1977), 81–90.
- J. Geneson, *Density bounds for permutations avoiding monotone arithmetic progressions*, arXiv:2608.12604 (2026).
