# Erdős #289 — all-prime p-adic obstruction for finite reciprocal sums

**Status:** unconditional elementary theorem packet.  
**Parent Erdős #289:** OPEN.  
**Historical priority / novelty:** not adjudicated here. The `p=2` slice contains the classical Kürschák mechanism; the all-prime packaging is published as an estate asset pending literature court.

## Main theorem

Let

\[
S\subset\{2,3,4,\ldots\}
\]

be finite and suppose

\[
R(S):=\sum_{n\in S}\frac1n\in\mathbb Z.
\]

Fix any prime `p` and define

\[
\boxed{
U_p(S)=
\sum_{\substack{n\in S\\p\mid n}}
\frac1{n/p}.
}
\]

Then

\[
\boxed{v_p(U_p(S))\ge1.}
\]

Equivalently,

\[
\frac{U_p(S)}p
\]

is `p`-adically integral.

---

# Proof

Split the reciprocal sum according to divisibility by `p`:

\[
R(S)
=
\sum_{\substack{n\in S\\p\nmid n}}\frac1n
+
\sum_{\substack{n\in S\\p\mid n}}\frac1n.
\]

The second term is

\[
\frac1p
\sum_{\substack{n\in S\\p\mid n}}
\frac1{n/p}
=
\frac{U_p(S)}p.
\]

Every denominator in the first sum is a `p`-adic unit, so

\[
\sum_{p\nmid n}\frac1n\in\mathbb Z_{(p)}
\]

(and therefore has nonnegative `p`-adic valuation).

The total `R(S)` is an integer, hence also `p`-adically integral. Therefore their difference

\[
\frac{U_p(S)}p
=
R(S)-
\sum_{p\nmid n}\frac1n
\]

is `p`-adically integral. Thus

\[
v_p(U_p(S))-1\ge0,
\]

which is exactly

\[
\boxed{v_p(U_p(S))\ge1.}
\]

QED.

---

# Maximum-denominator-layer corollary

There is a complementary integer formulation that makes the local obstruction especially transparent.

Let

\[
L=\operatorname{lcm}(S)
\]

and fix a prime `p`. Put

\[
e=\max_{n\in S}v_p(n)=v_p(L),
\]

and let

\[
M_p=\{n\in S:v_p(n)=e\}
\]

be the maximal `p`-denominator layer.

Since `R(S)` is integral,

\[
\sum_{n\in S}\frac Ln
=
L R(S)
\]

is divisible by `L`, hence in particular by `p`.

For every `n` with `v_p(n)<e`, the quotient `L/n` is divisible by `p`. Reducing modulo `p` therefore leaves only the maximal layer:

\[
\boxed{
\sum_{n\in M_p}\frac Ln\equiv0\pmod p.
}
\]

Each `L/n` in that sum is a `p`-adic unit. Consequently:

> **The maximal `p`-adic denominator layer can never consist of exactly one term.**

This statement holds for **every prime** `p`.

For `p=2`, the familiar unique-maximal-power-of-two denominator contradiction is precisely this corollary.

---

# Why the all-prime form is stronger operationally

A reciprocal-sum search can carry not just one parity state but a simultaneous vector of local conditions, one for every relevant prime:

\[
\bigl(v_p(U_p(S))\bigr)_p.
\]

Any candidate finite set whose reciprocal sum is intended to be an integer must satisfy all of them simultaneously.

This makes the theorem useful as a local-global pruning rule for Egyptian-fraction / interval-block searches.

---

# Relation to Erdős #289

The canonical problem asks whether, for all sufficiently large `k`, one can choose `k` pairwise-distinct finite intervals of consecutive positive integers,

- each of length at least two;
- pairwise nonoverlapping;
- pairwise nonadjacent;

whose combined reciprocal sum is exactly `1`.

If the union of the chosen intervals is `S`, then `R(S)=1`, so **every prime simultaneously imposes the theorem above**.

This does not settle existence for large `k`, but it is a necessary condition on every candidate solution.

---

# Companion estate assets

The same #289 campaign contains additional, separately scoped results:

1. **Kürschák interval obstruction.** A single nontrivial interval of consecutive integers has nonintegral reciprocal sum; the `p=2` maximal-denominator mechanism is the classical core.

2. **Forced `[2,3]` head in a decomposition of `1`.** The recovered campaign records that if a valid interval decomposition contains the integer `2`, the interval containing it is forced to be `[2,3]`, contributing `5/6` and leaving residual reciprocal mass `1/6` starting at least at `5`.

3. **Finite tail certificate.** The source records an exact finite check that no single interval `[a,b]`, `5<=a<b<=60`, has reciprocal sum `1/6`.

Those assets can be composed with the all-prime obstruction, but the finite no-run range is evidence only beyond its declared cutoff.

---

# Formalization boundary

The recovered estate lists `all_prime_padic_obstruction` as a **fresh formalization target** with proof plan:

> split `p|n` / `p∤n`; use p-adic integrality; conclude `U_p/p` integral.

That status means the theorem was queued for kernel formalization; it does **not** by itself certify that a Lean source compiled. This file therefore claims an elementary mathematical proof, not kernel authority, unless/until the exact formal source and compiler receipt are recovered.

## Provenance

Recovered during Pass 2 from the #289 campaign and independently re-audited during the 2026-09-13 publication sweep. The source's exhaustive sanity check enumerated all subsets of `{2,...,20}` with integral reciprocal sum and reported 168 prime/subset conditions with zero violations; that computation is corroboration, not the proof.
