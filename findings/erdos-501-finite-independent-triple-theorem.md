# Erdős #501 — finite row-family independent-triple theorem

**Status:** exact finite theorem extracted from the campaign; **no continuum transfer is claimed**.  
**Parent Erdős #501:** OPEN.  
**Novelty:** not assessed here.

## Finite model

Let

\[
V=[N],\qquad N\ge3,
\]

and for every `x in V` let

\[
A_x\subseteq V,
\qquad
|A_x|\le m.
\]

Call an unordered pair `{x,y}` **bad** when at least one of the directed incidences

\[
y\in A_x
\quad\text{or}\quad
x\in A_y
\]

holds.

A triple `{u,v,w}` is **independent** if none of its three pairs is bad.

Equivalently, form the symmetric conflict graph whose edge `xy` is present iff `y in A_x` or `x in A_y`; an independent triple is an independent set of size three in this graph.

## Theorem

If

\[
\boxed{6m<N-1,}
\]

then an independent triple exists.

## Proof

Count directed incidences

\[
(x,y),\qquad y\in A_x,\quad y\ne x.
\]

There are at most

\[
\sum_x |A_x|\le mN
\]

such incidences. Therefore the number of unordered bad pairs is at most `mN` as well.

Each bad pair belongs to exactly

\[
N-2
\]

triples.

Hence the number of triples that contain at least one bad pair is at most

\[
mN(N-2).
\]

On the other hand,

\[
\binom N3
=
\frac{N(N-1)(N-2)}6.
\]

The hypothesis

\[
6m<N-1
\]

is exactly

\[
mN(N-2)<\binom N3.
\]

So the bad pairs cannot touch every triple. At least one triple contains no bad pair, hence is independent.

QED.

## Boundary check

The strict inequality matters. At the formal boundary `6m=N-1`, the counting argument gives only

\[
\text{bad triples}\le\binom N3,
\]

which does not force a survivor.

Degenerate cases behave correctly:

- `m=0`: the conflict graph has no edges and every triple is independent;
- `N=3,m=0`: the unique triple survives;
- families with huge rows such as `A_x=V\setminus\{x\}` lie far outside the theorem's hypothesis.

## Relation to the historical campaign repair

Several earlier finite models in the #501 campaign were rejected because they did not faithfully preserve both directions of the symmetric independence condition or because a proposed finite-to-continuum transfer was unsupported.

Route R019 isolated the correct finite object and the simple bad-pair double count above. The source certifier records the full finite domain

\[
N\ge3,\qquad m\ge0,\qquad6m<N-1
\]

and explicitly excludes any automatic continuum transfer.

Some internal notes experimented with stronger pair-count normalizations; the conservative theorem published here uses only the indisputable estimate

\[
\#\{\text{bad unordered pairs}\}\le mN,
\]

so the stated `6m<N-1` hypothesis is fully justified without additional symmetry assumptions.

## Scope boundary

The original #501 problem is not a finite graph problem. This theorem is a **finite independent-triple lemma** inspired by the campaign's discretization.

Nothing here proves that the continuous / outer-measure hypotheses of Erdős #501 admit a discretization satisfying the required finite row bound at all scales, nor that a sequence of finite independent triples has a valid limiting transfer.

Therefore:

> **finite theorem: PROVED; continuum transfer: OPEN; parent Erdős #501: OPEN.**
