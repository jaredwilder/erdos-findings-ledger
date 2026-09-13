# Erdős #1210 — false `C=1` proof route killed

**Status:** proof route FALSE; Erdős #1210 remains open.  
**Source:** Pass-3 internal campaign ore, `erdos1210-campaign-001`, route R007/L1.

## Canonical target

For a pairwise-coprime set `A subset [1,n)`, Erdős #1210 asks whether

\[
\sum_{a\in A}\frac1{n-a}
\le
\sum_{p<n}\frac1p+O(1)
\]

with an absolute uniform constant.

The public problem is still listed as open.

## The mined false close

One historical route was filed as

`status=PROVED`

with the claim that the main proposition holds with uniform `C=1`. Its key step was:

> if `a_1,a_2` are coprime, then `n-a_1,n-a_2` are coprime because
> `gcd(n-a_1,n-a_2) | gcd(a_1,a_2)`.

That divisibility statement is false.

## Exact counterexample to the proof step

Take

\[
n=10,\qquad a_1=1,\qquad a_2=7.
\]

Then

\[
\gcd(1,7)=1,
\]

so `{1,7}` satisfies the pairwise-coprime hypothesis. But

\[
n-a_1=9,\qquad n-a_2=3,
\]

and

\[
\gcd(9,3)=3.
\]

Thus

\[
\gcd(n-a_1,n-a_2)=3\nmid1=\gcd(a_1,a_2).
\]

So the transformed set `B={n-a:a in A}` need not be pairwise coprime, and the subsequent injective-smallest-prime assignment does not follow.

## What this does and does not show

This kills the **R007/L1 proof**, not the Erdős proposition itself and not the possibility that `C=1` might happen to be true for some other reason.

Indeed, the same campaign contains exact finite evidence compatible with `D(n)<=1` for small `n`, but repeatedly records the absence of any finite-to-uniform theorem. That evidence cannot repair the broken universal proof.

The only safe disposition is therefore:

- R007/L1 full proof: **FALSE / RETRACTED AS A PROOF**;
- small exact computations: finite evidence only;
- Erdős #1210: **OPEN**.

## Why this record matters

The Pass-3 mine contains local `PROVED` labels that are workflow provenance rather than mathematical authority. This example is a concrete semantic-audit failure mode: an elementary-looking transformation silently destroys pairwise coprimality.

Future routes should blacklist the inference

`pairwise-coprime A => pairwise-coprime (n-A)`.

## Public reference

- Erdős Problem #1210: https://www.erdosproblems.com/1210
