# Erdős #1107 — exact finite obstruction at 87

**Status:** exact finite exhaustive result.  
**Scope:** one integer, `n=87`; no asymptotic conclusion is claimed.  
**Novelty:** unchecked.

Recall that a positive integer is **powerful** if every prime dividing it occurs to exponent at least two.

## Theorem

The positive powerful integers at most `87` are exactly

\[
\boxed{
1,4,8,9,16,25,27,32,36,49,64,72,81.
}
\]

No sum of one, two, or three members of this set (repetition allowed) equals `87`.

Therefore

\[
\boxed{87\text{ is not a sum of at most three positive powerful numbers}.}
\]

## Exhaustive check

The powerful-number list follows directly from prime factorization: every prime exponent in the factorization must be either zero or at least two.

Once the list is fixed, the representation claim is finite. Exhaust all unordered multisets of sizes `1`, `2`, and `3` drawn from the 13 values above. None has sum `87`.

The 2026-09-13 publication sweep independently regenerated the powerful-number list and replayed the complete combinations-with-repetition check; the result matched the Pass-3 estate record with zero representations.

## Scope boundary

This is a finite obstruction/regression point extracted from the Erdős #1107 campaign. It does not by itself settle any stronger eventual, density, or universal representation question associated with the parent problem.
