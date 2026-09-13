# Erdős #477 — complete quadratic obstruction by symmetric differences

**Status:** unconditional theorem for every quadratic integer polynomial; **degree-2 case closed negatively**.  
**Canonical parent problem:** the campaign's degree >=3/full question was not closed by this estate theorem.  
**Proof status:** independently repaired on 2026-09-13 during publication court.  
**Novelty / priority:** not adjudicated here; do not retroactively attribute later full degree>=3 work to this estate.

## Canonical setting

Let

\[
f:\mathbb Z\to\mathbb Z,
\qquad
f(k)=ak^2+bk+c,
\qquad a\ne0,
\]

and let

\[
B=f(\mathbb Z).
\]

Erdős #477 asks whether there can be a set `A subset Z` such that every integer `n` has **exactly one** representation

\[
n=\alpha+\beta,
\qquad
\alpha\in A,
\quad
\beta\in B.
\]

Equivalently, one asks for a unique direct sum

\[
\mathbb Z=A\oplus B.
\]

## Theorem — no quadratic works

For every quadratic integer polynomial

\[
f(k)=ak^2+bk+c,\qquad a\ne0,
\]

there is **no** set `A subset Z` with

\[
\boxed{\mathbb Z=A\oplus f(\mathbb Z).}
\]

Thus the degree-2 branch of the problem is completely obstructed.

---

# Proof

## 1. Uniqueness forces disjoint difference sets

If

\[
\mathbb Z=A\oplus B
\]

uniquely, then

\[
\boxed{(A-A)\cap(B-B)=\{0\}.}
\]

Indeed, if

\[
a_1-a_2=b_2-b_1\ne0
\]

with `a_1,a_2 in A` and `b_1,b_2 in B`, then

\[
a_1+b_1=a_2+b_2
\]

gives two distinct representations of the same integer.

## 2. Every quadratic difference set contains a full nonzero subgroup

Choose an integer `q` such that

\[
2aq+b\ne0.
\]

Such a `q` always exists because `a ne 0`. Define

\[
L:=2(2aq+b)\ne0.
\]

For every integer `t`, compute symmetrically around `q`:

\[
\begin{aligned}
f(q+t)-f(q-t)
&=a\bigl((q+t)^2-(q-t)^2\bigr)
 +b\bigl((q+t)-(q-t)\bigr)\\
&=4aqt+2bt\\
&=2(2aq+b)t\\
&=Lt.
\end{aligned}
\]

Therefore

\[
\boxed{L\mathbb Z\subseteq B-B.}
\]

This is the load-bearing quadratic identity.

## 3. Therefore `A` is finite

By uniqueness,

\[
(A-A)\cap L\mathbb Z=\{0\}.
\]

Hence two distinct elements of `A` cannot be congruent modulo `|L|`. Otherwise their nonzero difference would lie in `L Z`.

Thus `A` contains at most one representative of each residue class modulo `|L|`, and so

\[
\boxed{|A|\le |L|<\infty.}
\]

## 4. A finite number of quadratic translates cannot cover all integers

If `a>0`, the quadratic value set `B=f(Z)` is bounded below. Since `A` is finite,

\[
A+B=\bigcup_{\alpha\in A}(\alpha+B)
\]

is also bounded below.

It therefore cannot equal `Z`.

If `a<0`, the same argument works with “bounded above.”

This contradicts the required coverage

\[
A+B=\mathbb Z.
\]

Therefore no such `A` exists.

QED.

---

# Why this file is a proof repair

The recovered campaign registry contained the stronger-looking sentence that for every quadratic the difference set `f(Z)-f(Z)` “covers all integers outside one residue class modulo `4|a|`,” followed by `|A|<=2`.

That intermediate claim is false as written.

For example, with

\[
f(k)=2k^2,
\]

every value difference is even, so the difference set certainly does not contain all integers outside one residue class modulo 8. Moreover `A={0,1,4}` has nonzero differences `1,3,4`, none of which is a difference of two values `2x^2-2y^2`; thus the raw universal `|A|<=2` intermediate claim also fails in this example.

The later Pass-3 source correctly re-established only the special square case `f(k)=k^2` by the classical difference-of-squares identity and explicitly warned that its universal analytic reduction was missing.

The theorem above salvages the **all-quadratic conclusion** with a different proof. The correct invariant is not “almost every residue is a quadratic value difference,” but the much simpler fact that the quadratic difference set contains **one entire nonzero additive subgroup `L Z`**.

That subgroup alone forces any uniqueness set `A` to be finite, after which one-sided boundedness of a quadratic finishes the argument.

## Special square case recovered automatically

For `f(k)=k^2`, take for instance `q=1`, giving `L=4`. The general proof already forces `A` to contain at most one element from each class modulo 4, hence to be finite.

The stronger classical square-specific calculation says

\[
\{x^2-y^2:x,y\in\mathbb Z\}
=
\mathbb Z\setminus\{d:d\equiv2\pmod4\},
\]

which further sharpens the uniqueness bound to `|A|<=2`. That refinement is unnecessary for the general quadratic obstruction.

---

# Scope / chronology boundary

This theorem proves:

> **every quadratic integer polynomial fails the direct-complement requirement.**

It does **not**, by itself, say anything comparable for degree `>=3`: the symmetric difference

\[
f(q+t)-f(q-t)
\]

is no longer linear in `t`, so the subgroup argument is genuinely degree-2.

The estate's earlier records explicitly left degree `>=3` unresolved. Later external 2026 work going beyond the quadratic slice must be cited as external and must not be retroactively attributed to this campaign.
