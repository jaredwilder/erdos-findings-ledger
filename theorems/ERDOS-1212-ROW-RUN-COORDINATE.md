# Erdős #1212 — exact fixed-row run coordinate

**Author:** Jared Wilder  
**Status:** exact local theorem recovered from the campaign; the parent infinite-path problem remains open.

The relevant graph has coprime lattice vertices and unit coordinate steps. Fix a row `x>=2`.

Define `g(n)` using the campaign's **dual Jacobsthal convention**:

> `g(n)` is the least integer `m` such that every block of `m` consecutive integers contains at least one integer that is **not** coprime to `n`.

Equivalently, `g(n)-1` is the maximum possible length of a consecutive block all of whose entries are coprime to `n`.

## Theorem

For every `x>=2`, the maximum length of a consecutive vertical run on row `x` is exactly

\[
\boxed{g(\operatorname{rad}(x))-1}.
\]

Moreover, if `x` is even, the row has no vertical edge at all.

## Proof

A vertical run on row `x` is exactly a block of consecutive integers `y` satisfying

\[
\gcd(x,y)=1.
\]

But

\[
\gcd(x,y)=1\iff \gcd(\operatorname{rad}(x),y)=1.
\]

By the definition of the dual run function `g`, the longest consecutive block all coprime to `rad(x)` has length exactly `g(rad(x))-1`.

For the even-row statement, if `x` is even and `(x,y)` is a vertex then `y` is odd. Hence `y-1` and `y+1` are even, so

\[
\gcd(x,y\pm1)\ge2.
\]

Thus neither vertical neighbor is a vertex.

## Exact checks retained from the source

The campaign's integer-only verifier checked the finite box used for regression testing and recorded, among other examples:

- row `25`: the run `y=6,7,8,9` has length `4`, attaining the bound;
- even rows: zero vertical degree.

The finite checks are regression evidence; the theorem itself is analytic and all-row.

## Convention warning

This identity is **not** a statement about every convention called the Jacobsthal function. The source explicitly warned that the complementary standard convention reverses the interpretation. The definition above is therefore part of the theorem statement.

## Scope

This theorem forces any infinite admissible path to change rows repeatedly, but it does not construct such a path and does not close Erdős #1212. The global multi-row/CRT seam remains open.
