# Erdős #1192 — exact energy floor and density ceiling

**Status:** unconditional supporting lemmas; Erdős #1192 remains OPEN for general `r>=3`.  
**Novelty:** none claimed. These are elementary Cauchy–Schwarz consequences extracted from the internal campaign because they identify the exact scale at which the open problem lives.

For `A subset N`, let

\[
f_r(n)=\#\{(a_1,\ldots,a_r)\in A^r:a_1+\cdots+a_r=n\},
\]

with ordered tuples and repetition allowed, and put

\[
E_r(x)=\sum_{0\le n\le x} f_r(n)^2.
\]

## 1. Every asymptotic basis has linear energy from below

Suppose `A` is an asymptotic basis of order `r`, and let `N` be any threshold such that

\[
f_r(n)\ge1\qquad(n\ge N).
\]

Then for every integer `x>=N`,

\[
\boxed{
E_r(x)\ge \frac{(x-N+1)^2}{x+1}.
}
\]

### Proof

The basis property gives

\[
\sum_{0\le n\le x}f_r(n)\ge x-N+1.
\]

Cauchy–Schwarz over the `x+1` terms yields

\[
\left(\sum_{0\le n\le x}f_r(n)\right)^2
\le (x+1)E_r(x).
\]

Combine the two inequalities.

In particular,

\[
E_r(x)\ge x-O_A(1),
\]

so `E_r(x)=o(x)` is impossible for every asymptotic basis. The `O(x)` target in #1192 therefore sits at the smallest possible order of growth.

## 2. An `O(x)` energy bound forces the `x^(1/r)` density scale

Fix `y>=1`. Every ordered `r`-tuple from

\[
A\cap[1,y]
\]

has sum at most `ry`. Hence, writing

\[
M(y)=|A\cap[1,y]|,
\]

we have the exact counting inequality

\[
\sum_{0\le n\le ry} f_r(n)\ge M(y)^r.
\]

A second Cauchy–Schwarz application gives

\[
\boxed{
E_r(ry)\ge \frac{M(y)^{2r}}{ry+1}.
}
\]

Consequently, if for some constant `C`

\[
E_r(x)\le Cx
\]

throughout the relevant range (in particular at `x=ry`), then

\[
\boxed{
M(y)^{2r}\le C\,ry(ry+1)
}
\]

and therefore

\[
\boxed{
|A\cap[1,y]|
\le \bigl(C\,ry(ry+1)\bigr)^{1/(2r)}.
}
\]

As `y->infinity`, this is

\[
|A\cap[1,y]|\le (C^{1/(2r)}r^{1/r}+o(1))y^{1/r}.
\]

So any #1192 witness with linear representation energy is automatically as sparse, up to constants, as an order-`r` basis can reasonably be.

## 3. Matching lower density forced by the basis property

The basis property itself also forces the opposite scale. For large `x`, all integers in `[N,x]` require representations, so the number of available ordered `r`-tuples from `A cap [1,x]` must satisfy

\[
|A\cap[1,x]|^r\ge x-N+1.
\]

Thus

\[
|A\cap[1,x]|\ge (x-N+1)^{1/r}.
\]

Combining this with the previous section shows that any successful #1192 witness must live on the sharply constrained scale

\[
|A\cap[1,x]|\asymp x^{1/r}
\]

(up to constants, with the upper estimate evaluated at the harmless rescaling above).

## 4. What this says about the open problem

These inequalities do **not** construct the required basis for `r>=3` and do not refute its existence. They locate the difficulty:

- linear `E_r(x)` is the exact order-theoretic floor allowed by Cauchy–Schwarz;
- attaining it forces near-minimal basis density;
- a dense or naive basis pays superlinear energy automatically.

So the open problem is not merely to find a basis and separately control representations. It asks for a basis whose representation vector remains essentially as flat as Cauchy–Schwarz permits while operating at the minimal density scale.

## 5. Correction preserved from the raw campaign

One historical route wrote the false cutoff inequality

\[
E_r(2^k)\ge \frac{|A\cap[1,2^k]|^{2r}}{2^k}.
\]

That is wrong: `r`-fold sums of elements at most `2^k` can be as large as `r2^k`, outside the summation window.

The correct exact form is

\[
E_r(r2^k)\ge
\frac{|A\cap[1,2^k]|^{2r}}{r2^k+1},
\]

which is precisely the second theorem above.

This correction matters because the raw Pass-3 history later caught and retracted the bad cutoff; the public theorem record should contain the repaired statement rather than the earlier local `PROVED` residue.

## Public status / literature boundary

Erdős Problem #1192 is currently open in general. The problem page records that Erdős and Rényi constructed sets with the desired linear energy and `|A cap [1,x]| >> x^(1/r)`, without the required basis conclusion, and that Ruzsa proved the full answer for `r=2`.

Reference:

- https://www.erdosproblems.com/1192
- I. Z. Ruzsa, *A just basis*, Monatsh. Math. (1990), 145–151.

The inequalities in this note are supporting infrastructure only; no historical priority claim is made.
