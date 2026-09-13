# Erdős #885 — factor-difference / square duality

**Status:** exact structural theorem; **Lean-verified in the recovered campaign receipt**.  
**Parent problem:** OPEN.  
**Novelty:** likely elementary / priority unresolved; no historical novelty claim is made here.

For an integer `N>=1`, define

\[
D(N)=\{|a-b|:a,b\in\mathbb N,\ ab=N\}.
\]

## Theorem

For `N>=1` and `d>=0`,

\[
\boxed{
d\in D(N)
\iff
\exists s\in\mathbb N:\ s^2=d^2+4N.
}
\]

Equivalently, factor differences of `N` are exactly those nonnegative `d` for which `d^2+4N` is a perfect square.

## Elementary proof

### Forward direction

Suppose

\[
N=ab,
\qquad
 d=|a-b|.
\]

Then

\[
(a+b)^2=(a-b)^2+4ab=d^2+4N.
\]

So `s=a+b` is the required square witness.

### Reverse direction

Suppose

\[
s^2=d^2+4N.
\]

Then

\[
(s-d)(s+d)=4N.
\]

Because `s^2` and `d^2` have the same parity, `s` and `d` have the same parity. Since `N>0`, we also have `s>d`. Thus

\[
a=\frac{s+d}{2},
\qquad
b=\frac{s-d}{2}
\]

are positive integers, and

\[
ab=\frac{s^2-d^2}{4}=N,
\qquad
|a-b|=d.
\]

Hence `d in D(N)`.

## Formal authority recovered from the estate

The Pass-2 kernel audit records the source file

`campaigns/erdos885-campaign-001/kernel/Erdos885Duality.lean`

with the theorem declaration

```lean
theorem erdos885_factor_difference_square
    (N d : ℕ) (hN : 1 ≤ N) :
    (∃ a b : ℕ, a * b = N ∧ b ≤ a ∧ a - b = d) ↔
    ∃ s : ℕ, s * s = d * d + 4 * N
```

The recovered verification receipt reports:

- backend: WSL / Mathlib project;
- status: `VERIFIED`;
- exit code: `0`;
- verification time: `4.6s`;
- declaration clean: `true`;
- axiom footprint: `propext`, `Classical.choice`, `Quot.sound`.

The exact `.lean` source bytes are still a provenance-recovery target; the compiler/axiom receipt is already preserved in the estate tables.

## Why this matters for #885

The original problem asks whether for every `k>=1` there are

\[
N_1<\cdots<N_k
\]

such that

\[
\left|\bigcap_i D(N_i)\right|\ge k.
\]

The square duality changes the coordinates completely. To find `k` common factor differences `d_1,...,d_k`, one seeks integers `N_i` such that

\[
\boxed{d_j^2+4N_i\text{ is a square for every }i,j.}
\]

So the common-difference problem becomes a simultaneous integral-point / simultaneous-square problem. This points naturally toward difference-of-squares parametrizations, Pell-type structures, conics, and higher simultaneous Diophantine intersections rather than the failed LCM constructions in the historical campaign.

## Pair-commonality is finite for fixed distinct differences

The same coordinate system gives an immediate finite reduction for two prescribed differences. If both `d<e` belong to `D(N)`, write

\[
x^2=d^2+4N,
\qquad
y^2=e^2+4N.
\]

Then

\[
y^2-x^2=e^2-d^2,
\]

so

\[
(y-x)(y+x)=e^2-d^2.
\]

Thus for fixed `d,e`, the possible `N` lie in a finite divisor enumeration of `e^2-d^2`. This explains why a successful all-`k` construction cannot simply freeze a finite difference set and scale `N` arbitrarily; the differences must co-vary with the witnesses.

## Exact campaign witnesses / boundary

The recovered campaign records exact small-`k` witnesses and finite pair intersections, but no all-`k` construction. In particular, the theorem is a **structural reduction**, not a close of #885.

A historical LCM-style route was killed because it incorrectly forced `0 in D(N_i)` for nonsquares. The square criterion makes the defect immediate:

\[
0\in D(N)\iff N\text{ is a square}.
\]

That failed route should remain dead.

## Publication boundary

What is public here:

- the exact square-duality theorem;
- an elementary proof;
- the recovered Lean compiler/axiom authority;
- the finite fixed-pair reduction;
- the simultaneous-square reformulation of the parent search.

What is **not** claimed:

- a solution of Erdős #885;
- a `k=5` witness;
- novelty of the elementary identity;
- public recovery of the exact historical `.lean` source bytes yet.
