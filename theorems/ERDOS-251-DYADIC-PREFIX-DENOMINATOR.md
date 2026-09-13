# Erdős #251 — exact denominator of every finite prime/dyadic prefix

**Author:** Jared Wilder  
**Status:** exact all-`N` finite-prefix theorem recovered from the estate.  
**Parent problem:** remains open; this theorem does **not** imply irrationality of the infinite series.

Let `p_n` denote the `n`th prime with `p_1=2`, and define

\[
S_N=\sum_{n=1}^N \frac{p_n}{2^n}.
\]

## Theorem

The denominator of `S_N` in lowest terms is

\[
\boxed{1\quad(N=1),\qquad 2^N\quad(N\ge 2).}
\]

Equivalently, for every `N>=2`, the numerator after putting the sum over the common denominator `2^N` is odd.

## Proof

Write

\[
S_N=\frac{A_N}{2^N},\qquad
A_N=\sum_{n=1}^N p_n 2^{N-n}.
\]

For `n<N`, the factor `2^{N-n}` is even. The final summand is `p_N`, and `p_N` is odd for every `N>=2`. Hence

\[
A_N\equiv p_N\equiv1\pmod2.
\]

Therefore no factor of 2 cancels and the reduced denominator is exactly `2^N`. At `N=1`, `S_1=2/2=1`.

## Indexing note

Some estate records use an origin-0 normalization. Under that convention the same parity argument shifts the exponent by one. This file uses the standard one-based prime indexing above.

## Authority boundary

The estate's exact-Fraction replay checked the small prefixes and spot values including `19/8`, `45/16`, and `3727/1024`. The universal statement above comes from the parity proof, not from finite extrapolation.

Nothing here proves that

\[
\sum_{n\ge1}\frac{p_n}{2^n}
\]

is irrational. The missing finite-to-infinite analytic bridge was explicitly left open in the source campaign.
