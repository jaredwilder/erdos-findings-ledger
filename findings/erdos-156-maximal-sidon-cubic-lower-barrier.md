# Erdős #156 — universal cubic lower barrier for maximal Sidon sets

**Status:** unconditional elementary theorem; repaired from a campaign route that initially mishandled blockers.  
**Parent problem:** OPEN.  
**Novelty:** not assessed here.

Let `A subset [N]` be an inclusion-maximal Sidon set, using the standard convention that all unordered pair sums `a+b` with `a<=b` are distinct. Put

\[
k=|A|.
\]

## Theorem

Every such maximal Sidon set satisfies

\[
\boxed{
N\le
k+\frac{k(k+1)}2+k^3.
}
\]

Consequently

\[
\boxed{|A|=\Omega(N^{1/3}).}
\]

For example, for `k>=2`, the displayed bound implies the simple explicit estimate

\[
N\le 2k^3,
\qquad
k\ge (N/2)^{1/3}.
\]

This is a universal **lower barrier** on the size of every inclusion-maximal Sidon set. It does not construct a maximal Sidon set of order `O(N^(1/3))`, which is the difficult direction relevant to the parent problem.

## Proof — corrected blocker dichotomy

Fix `x in [N]\A`. Since `A` is maximal, adjoining `x` destroys the Sidon property. Because `A` itself is Sidon, a new repeated sum must involve `x`.

There are only two genuine possibilities.

### Type I — diagonal blocker

The new pair `(x,x)` collides with an old pair `(a,b)`:

\[
2x=a+b
\]

for some `a,b in A`.

Thus `x` belongs to the half-sum blocker set

\[
H(A)=\{x\in[N]:2x\in A+A\}.
\]

Because a Sidon set has exactly `k(k+1)/2` unordered pair sums with repetition,

\[
|H(A)|\le\frac{k(k+1)}2.
\]

### Type II — mixed blocker

A new pair `(x,a)` collides with an old pair `(b,c)`:

\[
x+a=b+c,
\]

so

\[
x=b+c-a\in (A+A)-A.
\]

The number of possible ordered triples `(a,b,c)` is at most `k^3`, hence

\[
|((A+A)-A)\cap[N]|\le k^3.
\]

### No third case

If two distinct colliding pairs both contain exactly one copy of `x`, say `x+a=x+b`, then `a=b`, so the pairs are not distinct. If `(x,x)` collides with `(x,a)`, then `x=a in A`, contrary to `x notin A`.

Therefore every point of `[N]` lies in

\[
A\cup H(A)\cup((A+A)-A).
\]

Counting gives

\[
N
\le
k+\frac{k(k+1)}2+k^3.
\]

This proves the theorem.

## Why this is a repair, not the original raw claim

An earlier campaign shorthand asserted the stronger inclusion

\[
[N]\subseteq A\cup((A+A)-A).
\]

That is not generally justified: a missing point can be blocked solely because `2x=a+b`. The elementary example `A={1,3}`, `x=2` demonstrates the missing blocker mechanism: `2x=1+3`, while `2` need not lie in `(A+A)-A`.

The later source audit explicitly restored the half-sum blocker and retained the safe count

\[
N\le k+\frac{k(k+1)}2+k^3.
\]

That repaired inequality is the theorem published here.

## Scope relative to Erdős #156

The theorem proves that **no** inclusion-maximal Sidon set can be asymptotically smaller than cubic-root scale.

The interesting opposite direction—constructing sufficiently thin maximal Sidon sets uniformly in `N`—is not supplied by this argument. In fact the campaign also records large maximal extensions arising from Singer-type Sidon sets, so a universal *upper* bound on every maximal Sidon set of order `N^(1/3)` is false.

Thus the correct asset is a universal lower barrier, not a parent close.
