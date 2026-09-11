# Six times the machine convicted its own work

Every entry below is a claim this project made and then killed, with the object or argument that
killed it. They are published because a project that only ships its successes gives a reader no way
to calibrate the successes.

Each was re-read against its source file on 2026-09-11 before being listed here. The quotes are
verbatim.

---

## 1. A verification gate that was not independent

**The claim.** `theorem_transports.py` banked a kernel-certified theorem as a decision procedure and
documented its ground-truth gate as reproducing results *"established by an INDEPENDENT route"* --
the root caps from `omega_tree_enumerator.py`.

**What killed it.** That file's line 9 prunes on `A*(x-1)^j > B*x^j + 2`, which is the subject's own
`cap_fires` condition **rearranged character for character**. In the source's words:

> Agreeing with it proves only that the same inequality was implemented twice: it catches
> transcription bugs and nothing else.

**The repair, and why it is not a softening.** The consistency gate was demoted to exactly that, and
a genuinely independent gate added: unpruned exhaustive brute force with zero shared logic, which
must **first recover the known solutions 5, 35, 1295** before it is allowed to report any stratum
empty -- because a searcher that finds nothing everywhere would confirm any claim. It then ran 233
million combinations across the omega = 5..8 strata, all empty, zero contradictions with the four
known solutions. The hardened gate demonstrably bites: tampering the certificate file collapses the
reported ratio from 0.425 to 0.179 and restores on repair, and it rejected an over-claim by handing
back the actual counterexample `(5,7,37)`.

**The general lesson, as written at the time:** *"a gate quietly sharing its subject's assumptions is
worse than no gate, because absence of a gate is visible and a circular one reads as proof.
Verification independence must be checked at the level of shared FORMULAE, not shared authorship or
shared file."*

Source: `oracle/ledger/findings/circular-verification-gate-caught-2026-07-25.md`

---

## 2. A data-integrity test that everything passes

**The claim.** A transfer passed all five contract gates asserting that matrices with curation
defects violate the factorial-moment identity
`Sum_{j-sets S} C(|comN S|, m) = Sum_{m-sets A} C(c(A), j)`.

**What killed it.** The identity is a pure double count of the pairs (S,A) with S x A entirely arcs.
It uses **neither completeness nor antisymmetry**, so it holds for every binary relation. Four of
four arbitrary non-tournament digraphs satisfied it in all nine (j,m) arms.

> A test that everything passes tests nothing.

**The repair, with its own failure printed.** The replacement carries `IsTournament` as a
load-bearing hypothesis and does discriminate -- but the published table shows it still misses one
case, "one unscored pair: **0 / 4 -- NOT DETECTED**", and says why: deleting arcs only lowers the
left side, so the cap is blind to unscored pairs. The source calls this *"a real limitation, not a
caveat."*

**The general lesson:** the contract checks that a correspondence is declared and well formed. It
cannot check that the declared law is true.

Source: `oracle/evidence/erdos902-adjudication/REFUTED-identity-qc.md`

---

## 3. Density at least 1 is not sufficient for an odd covering system

**The claim (an implicit working rule).** Sets clearing the density wall are candidates for covering
systems.

**What killed it.** `{3,5,7,9,11,13,15}`, density **1.022**, L = 45045, is **UNSAT** -- proved by two
independent complete solvers, CP-SAT and PySAT, agreeing. It is the smallest natural distinct-odd
set that clears the density wall, and it still provably fails.

The ground-truth gate was run first: the known cover `{2,3,4,6,12}` returns SAT with a verified
witness, and the density-starved `{2,3}` and `{2,4,8}` return UNSAT. A solver that called everything
UNSAT would have been caught there.

**Result:** density >= 1 is necessary but **not sufficient**, as a certified per-set impossibility.

Source: `oracle/ledger/findings/erdos-odd-covering-siege-2026-07-24.md`

---

## 4. A predicted plateau that could not exist

**The claim.** The dominant long-plateau value of C_k drops by exactly 1 as k rises by 1
(C_3 -> 9, C_4 -> 8, C_5 -> 7), therefore C_6's long plateau sits at value 6.

**What killed it.** `C_6(9) = 8`, proven optimal. By monotonicity `C_6(N) >= 8` for every `N >= 9`,
so a long plateau at value 6 above n = 9 is **impossible, not merely unobserved**. The value-6 run is
only `n` in [6,7], length 2.

The refutation is deductive: monotonicity plus one proven value.

Source: `oracle/evidence/rapid-fire/C6-REFUTED-PREDICTION.json`

---

## 5. A constraint called non-binding that binds

**The claim.** C3 is non-binding at the optimum for Sidon sets: `max|Sidon| == max|Sidon & C3|` for
all n.

**What killed it.** An explicit breakpoint at n = 39..41. At n = 39 and 40, `|Sidon| = 8` but
`|Sidon & C3| = 7`. At n = 41 the constraint stops binding again.

The correct description is not "non-binding" but **delayed**: the joint system reaches each size
later than the marginal one, and the delays widen with size.

A child claim, "Sidon and C2-free implies C3-free", is also false, with witnesses at n = 12, 16, 20,
24 -- for example `{3,7,10,12}`.

Source: `oracle/evidence/rapid-fire/SIDON-C3-NONBINDING-REFUTED.json`

---

## 6. A failure count stated globally from a partial scan

**The claim.** For Erdos 1005, property P3 fails at exactly n = 63 and n = 91 below 92.

**What killed it.** The project's own blade, rescanned from n = 4, found **fifteen** exceptions:
7, 9, 11, 15, 19, 23, 25, 27, 31, 35, 39, 49, 51, 63, 91. These match van Doorn's published list
exactly.

The scan had started at n = 60 and the result was stated globally. The data was right and the
reporting was wrong, which is the more dangerous of the two failures because nothing in the output
looks broken.

Source: `oracle/ledger/findings/erdos-1005-farey-similarly-ordered-2026-07-25.md`

---

## What these have in common

Four of the six were caught by attacking the project's own work rather than defending it, and two of
those were caught only because a gate was required to recover a known answer before it was allowed
to report a new one. That single discipline -- **make the checker prove it can find something before
you believe it found nothing** -- accounts for more of the corrections here than any other technique.

Entry 2 is the one worth reading twice. Its repair is published alongside a table showing the repair
still misses a case, labelled as a real limitation. A repair that hides its remaining hole is how a
refuted claim comes back.
