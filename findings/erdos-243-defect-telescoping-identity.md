# Erdős #243 — exact defect telescoping identity and false `+1` counterexample

**Status:** unconditional algebraic identity; canonical Erdős #243 remains OPEN.  
**Source:** Pass-3 campaign ore, routes R008/R009, independently re-derived here.

Let

\[
2\le a_1<a_2<\cdots
\]

be any strictly increasing integer sequence, and define its deviation from the Sylvester successor by

\[
d_n:=a_{n+1}-(a_n^2-a_n+1).
\]

No asymptotic hypothesis is needed for the finite identity below.

## 1. Exact one-step defect identity

For every `n`,

\[
\boxed{
\frac1{a_n}
=
\frac1{a_n-1}
-
\frac1{a_{n+1}-1}
-
\frac{d_n}{a_n(a_n-1)(a_{n+1}-1)}.
}
\]

### Proof

By definition,

\[
a_{n+1}-1=a_n(a_n-1)+d_n.
\]

Hence

\[
\frac1{a_n-1}-\frac1{a_{n+1}-1}
=
\frac{a_{n+1}-a_n}{(a_n-1)(a_{n+1}-1)}.
\]

Using

\[
a_{n+1}-a_n=(a_n-1)^2+d_n,
\]

the right-hand side is

\[
\frac1{a_n}
+
\frac{d_n}{a_n(a_n-1)(a_{n+1}-1)},
\]

which rearranges to the displayed identity.

## 2. Finite telescoping form

Summing from `n=1` to `N` gives the exact identity

\[
\boxed{
\sum_{n=1}^{N}\frac1{a_n}
=
\frac1{a_1-1}
-
\frac1{a_{N+1}-1}
-
\sum_{n=1}^{N}
\frac{d_n}{a_n(a_n-1)(a_{n+1}-1)}.
}
\]

If `a_n -> infinity` and the reciprocal series converges, then the limiting form is

\[
\boxed{
\sum_{n\ge1}\frac1{a_n}
=
\frac1{a_1-1}
-
\sum_{n\ge1}
\frac{d_n}{a_n(a_n-1)(a_{n+1}-1)}.
}
\]

The residual series converges automatically whenever the left side does, because the finite identity defines its partial sums.

## 3. Sylvester recurrence = zero defect

The target recurrence in Erdős #243 is

\[
a_{n+1}=a_n^2-a_n+1.
\]

This is exactly `d_n=0`. In that case the residual term vanishes and the classical telescoping formula is recovered:

\[
\sum_{n\ge1}\frac1{a_n}=\frac1{a_1-1}.
\]

For the usual Sylvester sequence beginning `2,3,7,43,...`, this gives reciprocal sum `1`.

## 4. The mined `+1` counterexample is not a counterexample

One historical route proposed

\[
a_1=2,
\qquad
 a_{n+1}=a_n^2-a_n+2.
\]

Its first terms are

\[
2,4,14,184,33674,\ldots
\]

and it was at one point described as having reciprocal sum exactly `1`, which would have contradicted Erdős #243 because its deviation is constantly `+1`.

That claim is false.

Here `d_n=1` for every `n`, so the exact defect identity gives

\[
\sum_{n\ge1}\frac1{a_n}
=
1-
\sum_{n\ge1}
\frac1{a_n(a_n-1)(a_{n+1}-1)}
<1.
\]

Thus the proposed sum-`1` counterexample dies immediately, without numerical tail estimation.

The rationality of this `+1`-defect reciprocal sum is a separate question; the internal campaign found no proof that it is rational. Therefore this family is not a verified counterexample to #243.

## 5. Correction to the earlier false pointwise identity

An earlier route used

\[
\frac1{a_n}
\stackrel{?}{=}
\frac1{a_{n-1}}-rac1{a_{n+1}-1}.
\]

This is false outside the zero-defect recurrence and is circular as a route to proving that recurrence.

For example, on the `+1` family the triple `(2,4,14)` gives

\[
\frac14\ne\frac12-\frac1{13}.
\]

The boxed defect identity above is the correct ambient replacement: it records exactly how far a general sequence is from telescoping.

## 6. Structural reformulation of the open core

Suppose now that the canonical hypotheses of #243 hold:

\[
\frac{a_{n+1}}{a_n^2}\to1,
\qquad
\sum_n\frac1{a_n}\in\mathbb Q.
\]

Then the identity converts rationality of the reciprocal sum into rationality of the signed defect series

\[
\sum_{n\ge1}
\frac{d_n}{a_n(a_n-1)(a_{n+1}-1)}.
\]

The conjecture asks, in this language, whether those hypotheses force

\[
d_n=0
\]

for all sufficiently large `n`.

The identity itself does **not** prove that implication: cancellations among nonzero signed defects remain the load-bearing difficulty.

## Public status / literature boundary

Erdős #243 is still listed as open. Erdős–Straus proved a structural `limsup` obstruction for any non-Sylvester candidate, and Duverney proved the conjecture under a stronger convergence hypothesis. Recent independent work also studies centred remainder/error dynamics for this problem.

References:

- https://www.erdosproblems.com/243
- Google DeepMind Formal Conjectures, `ErdosProblems/243.lean`

This note claims the elementary defect identity and the correction of the internal false counterexample only; it does not claim a solution of #243 or historical priority for related remainder formulations.
