# Erdős #276 — common divisors of Fibonacci/Lucas-type recurrences

**Author:** Jared Wilder  
**Status:** recovered kernel-checked universal theorem from the estate.

Let `(a_n)` be an integer-valued recurrence satisfying

\[
a_{n+2}=a_{n+1}+a_n\qquad(n\ge0).
\]

## Theorem

For every integer `d`,

\[
\boxed{d\mid a_n\ \text{for every }n\ge0
\iff d\mid\gcd(a_0,a_1).}
\]

Equivalently, the common divisors of the entire recurrence are exactly the common divisors of its first two terms.

## Proof

The forward implication is immediate by taking `n=0,1`.

Conversely, if `d|a_0` and `d|a_1`, then induction using

\[
a_{n+2}=a_{n+1}+a_n
\]

shows `d|a_n` for every `n`.

## Authority

The recovered estate records label this result `KERNEL_CERTIFIED` / `KERNEL_CHECKED`, not merely computationally tested. The theorem is retained here because the formal authority and the exact universal scope were easy to lose inside the broader #276 campaign record.

## Scope

This is a structural theorem about the recurrence. It should not be read as a closure of any stronger parent claim associated with Erdős #276 beyond this common-divisor statement.
