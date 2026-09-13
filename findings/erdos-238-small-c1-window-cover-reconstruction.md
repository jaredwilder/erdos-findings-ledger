# Erdős #238 — small-`c₁` window-cover reconstruction

**Status:** classical restricted result reconstructed from the internal campaign; sharpened finite bridge recorded here.  
**Main Erdős #238 status:** OPEN.  
**Novelty claim:** none for the small-`c₁` theorem. Erdős Problems attributes that result to Erdős (1949).

## Canonical problem

For `c₁,c₂>0`, ask whether for every sufficiently large `x` there are more than `c₁ log x` consecutive primes `<=x` whose pairwise differences are all `>c₂`.

The unrestricted universal-`c₁` question remains open.

## Recovered restricted theorem

For every fixed `c₂>0`, there exists `epsilon(c₂)>0` such that for every

`0 < c₁ < epsilon(c₂)`, 

the desired block exists for all sufficiently large `x`.

This is the classical small-`c₁` sibling, not a solution of the full problem.

## Exact finite bridge: bad-gap window covering

Let

`p₁ < p₂ < ... < p_n <= x`

be the primes up to `x`. Call the gap at index `i` **bad** when

`p_{i+1}-p_i <= c₂`.

Let `B` be the number of bad gaps. Consider all windows of `k` consecutive primes. There are

`n-k+1`

such windows.

### Lemma

If every `k`-prime window contains a bad gap, then

`B (k-1) >= n-k+1`.

Equivalently, if

`B < (n-k+1)/(k-1)`,

then some `k` consecutive primes have **all** adjacent gaps `>c₂`.

### Proof

A bad gap between `p_i` and `p_{i+1}` can lie in at most `k-1` windows of `k` consecutive primes: those windows whose starting index places this gap among their `k-1` internal gaps.

If every one of the `n-k+1` windows contains at least one bad gap, counting window–bad-gap incidences gives

`n-k+1 <= B(k-1)`.

The contrapositive proves the claim.

The recovered Pass-3 route used the weaker but still valid denominator `k`; the `k-1` form above is the sharp incidence count for this argument.

## Sieve input and the logarithmic block

For fixed `c₂`, standard Brun/Selberg upper-bound sieve estimates give

`B_{c₂}(x) = O_{c₂}(x/log²x)`.

Indeed, a bad adjacent prime gap is in particular a prime pair `(p,p+d)` with integer `1 <= d <= c₂`; there are only finitely many such `d`, and each fixed-shift prime-pair counting function has a Selberg-sieve upper bound of order `x/log²x`.

Meanwhile the prime number theorem gives

`n = pi(x) ~ x/log x`.

Take

`k = floor(c₁ log x)+1`.

Then

`(n-k+1)/(k-1) ~ x/(c₁ log²x)`.

Thus if a fixed sieve constant `C(c₂)` satisfies eventually

`B_{c₂}(x) <= C(c₂) x/log²x`,

any fixed `c₁` with a strict margin

`c₁ C(c₂) < 1`

forces the window-cover inequality for all sufficiently large `x`, hence yields the desired `k`-prime block.

Because every adjacent gap in that block exceeds `c₂`, every non-adjacent difference does as well.

## Why this does not solve #238

The argument supplies only some positive threshold `epsilon(c₂)`. It does **not** handle arbitrary `c₁>0`.

The internal campaign correctly refused closure at exactly this point. Pure first-moment counting from an upper bound

`B_{c₂}(x) <= C(c₂)x/log²x`

cannot make the admissible `c₁` arbitrarily large. A full solution needs a mechanism beyond this fixed-constant covering argument.

## Provenance

Recovered from the 2026-09-02 Pass-3 mathematical paragraph mine for `erdos238-campaign-001`, especially the R003 route records that:

- certified the small-`c₁` sibling;
- isolated the finite window-cover bridge;
- explicitly refused to promote it to the universal-`c₁` close.

The source mine's weaker incidence statement used `B < (n-k+1)/k`; the present note independently tightens that finite combinatorial step to `k-1` without changing the asymptotic scope.

## Literature collision / historical status

Erdős Problems #238 states that Erdős proved the small-`c₁` case in:

P. Erdős, *On some applications of Brun's method*, Acta Univ. Szeged. Sect. Sci. Math. (1949), 57–63.

The January 2026 discussion on the problem page also describes the standard sieve+pigeonhole proof shape. Accordingly this file is a **reconstruction and mechanism record**, not a priority claim.

## Public references

- https://www.erdosproblems.com/238
- https://www.erdosproblems.com/forum/thread/238
- https://github.com/google-deepmind/formal-conjectures/blob/main/FormalConjectures/ErdosProblems/238.lean
