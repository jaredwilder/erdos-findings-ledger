# Erdős #893 — Zsigmondy pointwise lower bound

**Status:** unconditional classical corollary; not a solution of Erdős #893.  
**Novelty:** none claimed. The content is an explicit extraction of a useful uniform inequality from Bang–Zsigmondy.

Let `omega(m)` be the number of distinct prime factors and `tau(m)` the divisor-counting function.

## Theorem

For every integer `k>=1`,

\[
\omega(2^k-1)\ge \tau(k)-2.
\]

Consequently,

\[
\tau(2^k-1)\ge 2^{\tau(k)-2}.
\]

(The second inequality is harmlessly weak for `tau(k)<2`; equivalently one may write `tau(2^k-1)>=2^{max(tau(k)-2,0)}`.)

## Proof

For every divisor `d|k` with `d>=2` and `d!=6`, the Bang–Zsigmondy theorem supplies a primitive prime divisor `p_d` of

\[
2^d-1.
\]

Primitive means that `p_d` divides no `2^e-1` with `1<=e<d`. Equivalently,

\[
\operatorname{ord}_{p_d}(2)=d.
\]

Therefore the primes `p_d` attached to different `d` are distinct. Since `d|k`, the elementary divisibility

\[
2^d-1\mid 2^k-1
\]

shows that every such `p_d` divides `2^k-1`.

There are `tau(k)` divisors of `k`. At worst we lose `d=1` and, when it occurs, `d=6`. Hence

\[
\omega(2^k-1)\ge \tau(k)-2.
\]

Finally, an integer with `r` distinct prime factors has at least `2^r` divisors, so

\[
\tau(2^k-1)\ge 2^{\omega(2^k-1)}\ge2^{\tau(k)-2}.
\]

## Sharp scope / relation to #893

Erdős #893 defines

\[
f(n)=\sum_{1\le k\le n}\tau(2^k-1)
\]

and asks about the limit of `f(2n)/f(n)`.

The theorem above supplies strong pointwise spikes whenever `k` has many divisors, but **does not by itself control the denominator `f(n)` strongly enough to prove a limit statement**. In particular, the historical campaign's attempts to combine this lower bound with an unproved `f(n)<=n^{1+o(1)}`-type upper bound are not part of this theorem.

The current public status of #893 remains open. Kovač and Luca proved that no finite limit exists by showing

\[
\limsup_{n\to\infty}\frac{f(2n)}{f(n)}=\infty,
\]

and give evidence for divergence to infinity; this note does not strengthen that published asymptotic result.

## Provenance

Recovered from Pass-3 route material for `erdos893-campaign-001`. The source route correctly isolated the Zsigmondy counting lemma after several failed multiplicative-growth routes. This file strengthens the recorded `omega` inequality by immediately translating it to the divisor-count lower bound above.

## Reference

- Erdős Problem #893: https://www.erdosproblems.com/893
- Bang–Zsigmondy theorem (classical primitive-divisor theorem).
