# Erdős #513 — lacunary `sum z^(2^k)` route is outside the entire-function domain

**Status:** historical route INVALID by domain failure; Erdős #513 remains OPEN.  
**Source:** Pass-3 internal campaign `erdos513-campaign-001`, especially R001/L1.

## Canonical object

Erdős #513 asks for the supremum, over **transcendental entire** functions

\[
f(z)=\sum_{n=0}^{\infty}a_nz^n,
\]

of

\[
\liminf_{r\to\infty}
\frac{\max_n |a_n|r^n}
{\max_{|z|=r}|f(z)|}.
\]

The transcendental-entire hypothesis is load-bearing. Polynomial and finite-radius analytic functions are outside the domain.

## The mined family

A historical route proposed the Hadamard-lacunary series

\[
F(z)=\sum_{k\ge0}z^{2^k}
\]

and then performed exact arithmetic on expressions such as

\[
\frac{e^u}{\sum_{k\ge0}e^{2^ku}}
\]

in an attempt to obtain a canonical lower/extremal comparison.

The finite arithmetic itself is not the problem.

The function `F` is **not entire**.

## Exact radius-of-convergence calculation

Write

\[
F(z)=\sum_{n\ge0}a_nz^n,
\]

where

\[
a_n=\begin{cases}
1,&n=2^k\text{ for some }k,\\
0,&\text{otherwise}.
\end{cases}
\]

By Cauchy–Hadamard,

\[
R^{-1}=\limsup_{n\to\infty}|a_n|^{1/n}.
\]

Along the subsequence `n=2^k`,

\[
|a_n|^{1/n}=1,
\]

while all coefficients have magnitude at most one. Therefore

\[
\limsup |a_n|^{1/n}=1,
\qquad
\boxed{R=1}.
\]

Equivalently, for every real `r>1`, the individual terms

\[
r^{2^k}
\]

do not even tend to zero, so the series diverges.

Thus `F` is analytic only in the open unit disk, not an entire function and certainly not a transcendental entire admissible object for #513.

## Consequence for the campaign certificate

The raw route contains an exact-integer certificate evaluating a ratio for this family and labels a lacunary-family lemma `PROVED`.

That certificate can at most certify arithmetic about the finite-radius/lacunary series inside its domain of convergence. It cannot certify any statement of the form

> “this admissible entire-function family has canonical #513 ratio ...”

because the premise is false.

Permanent disposition:

- exact arithmetic performed on the displayed lacunary sums: may be correct as arithmetic;
- `F(z)=sum z^(2^k)` is transcendental entire: **FALSE**;
- use of `F` as an admissible #513 witness/extremizer/counterexample: **INVALID / DOMAIN DRIFT**;
- any descendant conclusion about the canonical supremum that requires this admissibility: **RETRACTED**.

## Correct comparison: `e^z`

The same campaign also examines

\[
f(z)=e^z=\sum_{n\ge0}\frac{z^n}{n!},
\]

which **is** transcendental entire. Standard Stirling estimates give

\[
\max_n\frac{r^n}{n!}
\sim \frac{e^r}{\sqrt{2\pi r}},
\qquad
\max_{|z|=r}|e^z|=e^r,
\]

so this particular admissible function has ratio tending to zero.

That fact only shows that no positive lower bound holds **pointwise for every entire function**. It does not conflict with the canonical quantity, which is a **supremum over functions** and is known to exceed `1/2`.

## Current public boundary

Erdős Problems currently records #513 as open. The known bounds include a strict lower bound above `0.585` and a universal upper bound strictly below `2/pi`; the exact supremum remains unknown.

References:

- https://www.erdosproblems.com/513
- Google DeepMind Formal Conjectures, `ErdosProblems/513.lean`

This note is an internal authority correction, not a new bound for #513.
