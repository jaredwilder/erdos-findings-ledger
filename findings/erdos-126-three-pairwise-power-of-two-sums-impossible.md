# Erdős #126 — three pairwise power-of-two sums are impossible

**Status:** unconditional elementary theorem.  
**Parent problem:** this is a local structural lemma, not a claim of frontier priority or a parent close.  
**Novelty:** unchecked; no priority claim.

## Theorem

There do not exist three distinct positive integers

\[
0<x<y<z
\]

such that all three pairwise sums

\[
x+y,\qquad x+z,\qquad y+z
\]

are powers of two.

## Proof

Because

\[
x+y<x+z<y+z,
\]

write

\[
x+y=2^p,\qquad x+z=2^q,\qquad y+z=2^r
\]

with

\[
p<q<r.
\]

Solving for `x`,

\[
2x=(x+y)+(x+z)-(y+z)
=2^p+2^q-2^r.
\]

But `r>=q+1`, so

\[
2^r\ge2^{q+1}=2\cdot2^q.
\]

Since `p<q`,

\[
2^p+2^q<2^q+2^q=2^{q+1}\le2^r.
\]

Hence

\[
2x<0,
\]

contradicting `x>0`.

Therefore no such triple exists.

## Estate disposition

This lemma appeared in the Pass-3 gold layer but was easy to lose because later external work on the broader Erdős problem changed the frontier. The lemma remains a valid independent structural fact and is retained here on its own scope.
