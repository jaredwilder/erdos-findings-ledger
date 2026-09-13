# Erdős #891 — `Omega` / `omega` variant substitution kills the claimed close

**Status:** historical close INVALID; canonical Erdős #891 remains OPEN.  
**Source:** Pass-3 campaign ore for `erdos891-campaign-001`.

## Canonical problem

For `2=p_1<p_2<...` and fixed `k>=2`, Erdős #891 asks whether every sufficiently large interval

\[
[n,n+p_1p_2\cdots p_k)
\]

contains an integer having **more than `k` distinct prime factors**.

Write `omega(m)` for the number of distinct prime divisors and `Omega(m)` for the number counted with multiplicity. The canonical problem is an `omega` statement.

## The mined false close

A sequence of historical routes observes that any interval of length at least `2^k` contains a multiple

\[
m=2^k q.
\]

For `q>=2`, it then obtains

\[
\Omega(m)=k+\Omega(q)\ge k+1.
\]

Since the primorial `p_1...p_k >= 2^k`, this indeed gives an elementary theorem for the **multiplicity-counting `Omega` variant**.

One mined row then says this “closes branch A.” That is not a close of Erdős #891.

## Exact failure of the transfer

For distinct prime factors,

\[
\omega(2^k q)
\]

need not be large at all. If `q` is itself a power of two then

\[
\omega(2^k q)=1.
\]

For example, at `k=2` and `n=29`, the forced multiple of `2^k=4` in the six-term window `[29,35)` is

\[
32=2^5,
\]

so

\[
\Omega(32)=5>2,
\qquad
\omega(32)=1.
\]

Thus the exact witness mechanism used by the claimed close proves nothing of the required distinct-prime-factor inequality.

The smaller window `[5,11)={5,6,7,8,9,10}` is an even starker finite illustration: its forced `2^2` multiple is `8`, with `Omega(8)=3` but `omega(8)=1`. (This is not a counterexample to the canonical asymptotic statement; it demonstrates the variant mismatch.)

## Correct surviving theorem

The following multiplicity variant is valid:

> For every `k>=2` and every `n>=2^k+1`, any interval of length at least `2^k` contains an integer `m` with `Omega(m)>k`.

Proof: take the first multiple `m=2^k q >= n`; then `q>=2` and `Omega(m)=k+Omega(q)>=k+1`.

This theorem is elementary but it is **not Erdős #891**.

## Estate chronology

The same raw campaign contains earlier audit rows explicitly warning about the `OMEGA/OMEGA-CAPITAL` trap and later rows correctly saying that the `omega` reading does not transfer. The invalid close arose because those warnings were not propagated consistently into the branch-level status.

Permanent disposition:

- `Omega`-with-multiplicity variant: **PROVED, elementary**;
- transfer from that result to distinct-prime `omega`: **FALSE**;
- claimed canonical branch-A close: **RETRACTED**;
- Erdős #891: **OPEN**.

## Public source state

Erdős Problems currently states that the problem requires more than `k` **distinct** prime factors and says it is unknown even for `k=2`.

Reference: https://www.erdosproblems.com/891
