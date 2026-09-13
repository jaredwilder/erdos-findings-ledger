# Erdős #197 — complete finite analogue by parity descent

**Status:** unconditional finite theorem.  
**Parent Erdős #197:** OPEN.  
**Novelty:** no historical priority claim; this is an elementary structural theorem extracted from the campaign after earlier finite-search routes obscured the general proof.

## Theorem

Every finite set

\[
S\subset\mathbb N
\]

admits a linear ordering in which no nontrivial three-term arithmetic progression appears in increasing positional order.

Equivalently, for every finite `S` there is a bijection

\[
\pi:\{1,\ldots,|S|\}\to S
\]

such that there do not exist `i<j<k` with

\[
\pi(i),\pi(j),\pi(k)
\]

forming a nonconstant arithmetic progression in that value order.

Consequently, for **every finite partition**

\[
S=A\sqcup B,
\]

both parts independently admit such AP-avoiding orderings.

Thus the finite analogue of the partition requirement in Erdős #197 is completely trivialized: **every finite two-coloring works once each color class may choose its own recursive order.**

## Recursive construction

Define an ordering `B(S)` recursively.

If `|S|<=1`, use the unique order.

Otherwise split

\[
S=S_0\sqcup S_1,
\]

where `S_0` is the even part and `S_1` the odd part.

Normalize the two parity classes by

\[
T_0=\{x/2:x\in S_0\},
\qquad
T_1=\{(x-1)/2:x\in S_1\}.
\]

Recursively order `T_1` and `T_0`, lift them back to odd/even values, and concatenate the two blocks, for example

\[
B(S)=\bigl(2B(T_1)+1\bigr)\;\Vert\;\bigl(2B(T_0)\bigr).
\]

Either parity-first convention works as long as it is used consistently at each recursive node.

The recursion terminates because normalization divides the diameter/maximum scale by two until every branch is a singleton.

## Proof

Suppose, toward contradiction, that

\[
a,b,c
\]

form a nontrivial arithmetic progression,

\[
a+c=2b,
\qquad a<c,
\]

and appear in increasing order in `B(S)`.

Let the common difference be `d=b-a=c-b`.

### Case 1 — `d` is odd

Then the endpoint values `a,c` have the same parity, while the middle value `b` has the opposite parity.

Since the construction places the two parity classes in contiguous blocks, both endpoints lie in one block and the midpoint lies in the other.

Therefore the midpoint is either before **both** endpoints or after **both** endpoints. It cannot lie positionally between them.

So an increasing positional occurrence

\[
a\prec b\prec c
\]

is impossible.

### Case 2 — `d` is even

Then `a,b,c` all have the same parity. They therefore lie entirely inside one recursive parity block.

After applying the corresponding affine normalization

\[
x\mapsto x/2
\quad\text{or}\quad
x\mapsto(x-1)/2,
\]

they remain a nontrivial three-term arithmetic progression, and their relative order is unchanged.

Thus a forbidden progression in `B(S)` would induce a forbidden progression in the recursively ordered normalized set.

Descending repeatedly must eventually reach a singleton-scale branch, where no nontrivial 3-AP exists. Contradiction.

Hence `B(S)` is AP-avoiding.

## Finite partition corollary

If

\[
[N]=A\sqcup B
\]

is **any** two-coloring, apply the theorem separately to `A` and `B`.

Therefore every finite two-coloring of every `[N]` satisfies the finite analogue of the #197 requirement.

Earlier campaign computations exhaustively checked many small `N` instances and found explicit witnesses, but those searches are subsumed by the recursive theorem.

## Why this does not solve Erdős #197

The infinite problem asks for a partition of `N` into two infinite sets that each admit a **single bijective enumeration** with no monotone 3-AP.

The finite theorem supplies an ordering independently for every finite set. It does **not** give a coherent nested family of orderings, a compactness theorem preserving bijectivity/order avoidance, or an infinite recursive enumeration.

Indeed, infinite parity recursion has a basic well-ordering problem: placing one infinite parity class completely before another is not an enumeration of both blocks by `N` in the finite-concatenation sense.

So the finite theorem is exact and complete at finite scale, while the finite-to-infinite bridge remains load-bearing and open.

## Relation to the separate anchor-chain obstruction

The estate also contains a distinct necessary condition for any infinite 3-permutable set: from every anchor `v` and odd `o`, the set must omit infinitely many points of the dyadic chain

\[
v+2^k o.
\]

That obstruction is compatible with the present theorem: finite sets have no infinite-chain obligation at all.

Together the two results pinpoint the seam sharply:

- **finite AP-avoiding orderability:** universal, solved by parity descent;
- **infinite bijective orderability / two-color partition:** genuinely noncompact and still open.

## Provenance

Recovered from `erdos197-campaign-001`, where early routes performed exhaustive checks on small partitions before route R013 recorded the general parity-descent induction. The canonical estate audit correctly promoted this from “finite evidence” to a complete finite theorem.
