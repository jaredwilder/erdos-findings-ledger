---
id: erdos710-msl-campaign
title: Erdős #710 — theorems and measurements harvested from the MSL close campaigns
status: OPEN (target); the results below are the banked by-products
domain: number theory
provenance: oracle/evidence/msl-machine/gpt56-luna-*-erdos710-* (decodes + rounds),
            oracle/evidence/erdos710/ (matchers, reductions), 2026-09-02..03
updated: 2026-09-03
---

# Erdős #710 — the theorem bank

The target (obtain an asymptotic formula for f(n), the minimal L with n distinct
k-divisible integers in (n, n+L)) remains OPEN. Everything below is a RESULT collected
along the way and is banked so it is never lost. Each row carries its own honest status.
A close of the target does not gate any of these; they stand on their own receipts.

## PROVED (hand-verified derivations; no kernel backend used)

- **T1 — Endpoint monotonicity.** E(n) = n + f(n) is nondecreasing, hence f(n+1) ≥ f(n) − 1:
  the threshold never descends by more than one per step. Proof: a solution for n+1
  restricted to indices ≤ n solves n. Receipt: GPT-ANTICHAIN-REDUCTION-2026-09-02.md,
  hand-verified. Consequence: every descent of f has magnitude exactly 1 (empirically
  confirmed on [1,114]).
- **T2 — The primitive-antichain doubling reduction.** A Hall obstruction for the
  divisibility bipartite graph is equivalent to a primitive antichain A ⊆ [1,n] failing
  the doubling condition M_A(n+h) ≥ 2·M_A(n), where M_A(x) = #{m ≤ x : ∃a∈A, a|m}. So
  f(n) = min{h : M_A(n+h) ≥ 2M_A(n) for every primitive A}. Proof: divisibility upward
  closure preserves neighborhoods (k|j ⇒ N(j)⊆N(k)) while enlarging the index set;
  hand-verified. This is the arithmetic reformulation of the whole problem.
- **T3 — Critical doubling identity.** At the threshold there is a critical primitive
  antichain A with M_A(n + f(n) − 1) = 2·M_A(n) − 1 (deficiency exactly one just below
  threshold, from T1). Hand-verified.

## COMPUTATION_SUPPORTED (our own receipted matchers; finite ranges stated)

- **M1 — Verified exact thresholds** (inclusive convention t(n)): t(50)=76, t(100)=160,
  t(150)=246, t(200)=340, t(300)=510, t(500)=877, t(1000)=1816, t(2000)=3814. Two
  independent matchers (e710.py exhaustive; hall_tools.py augmenting-path, selftested);
  t(500) and t(1000) additionally cross-match the external GPT table. Receipt:
  oracle/evidence/msl-machine/gpt56-luna-CLOSE4-erdos710-2026-09-03/hall_tools.py.
- **M2 — Prime-descent law.** t(p) = t(p−1) − 1 for every prime p in [13, 113] (25/25,
  the last five out-of-sample from the conjecturing set); extended to p ≤ 1000 externally
  (unverified by us beyond 113). Small primes 2,3 ascend; 5,7,11 tie. Receipt:
  oracle/evidence/erdos710/DESCENT-LAW-TARGET-2026-09-02.md. Provable-looking; a genuine
  small unconditional result if closed.
- **M3 — Archetype refutation (the negative result).** NO named primitive-antichain
  family — tail intervals (n/q, n], Ω-level sets {Ω(m)=k}, prime-factor windows, or
  mixed tails — achieves the exact threshold for n ≥ 75. The Ω-level k=2/k=3 family is
  exactly extremal at n=50 (76=76) then undershoots by a widening margin (474 vs 510 at
  n=300, ratio ~0.93). The true extremal antichain lies OUTSIDE every named family.
  Receipt: gpt56-luna-CLOSE3 rounds 11,15 (W17, W24, CLAIM_STATUS REFUTED, receipted
  matcher). A negative theorem is a RESULT.
- **M4 — Critical-set structure (partial).** The minimal Hall violator's generating
  antichain at h=t(n)−1 is a mixed-Ω hybrid spanning roughly 0.24n to 0.98n (e.g. n=150:
  13 elements, Ω-distribution {1:2, 2:7, 3:4}, tail-fraction 0.23). Extracted via
  König/reachability from unmatched vertices. Receipt: hall_tools.invariants.

## OPEN sub-targets (the ladder that would close something)

- Classify the true critical antichains M4 into an explicit generator family A_fit(n);
  verify A_fit reproduces the exact thresholds M1 on a certified finite range. This is a
  CLOSABLE finite theorem and the standing successor target (campaign 4 reached rung 3
  clean but did not yet certify the family).
- The full asymptotic constant (the prize) — the ratio f(n)/(n·√(log n/log log n))
  rises through 1.0 near n≈5,000 toward the lower-bound constant 2/√e≈1.213; open.

## Prior art

Erdős–Pomerance 1980 (matching the naturals with distinct multiples in an interval) and
Erdős 1992; published bounds (2/√e+o(1))n(log n/log log n)^½ ≤ f(n) ≤ (1.7398+o(1))n(log n)^½.
See oracle/evidence/erdos710/ERPO80-SOURCE-NOTE.md (citation-level; paper text not on disk).

## THE FORMALIZER WORKS — I USED THE WRONG DOOR (correction, 2026-09-03)

Earlier text here said the Lean layer was "a calculator that can't prove the real math."
THAT WAS WRONG and it slandered a working tool. The estate's Frontier Formalizer proves
real theorems: EG411 alone has ~dozens of kernel-checked declarations (Balance Law,
Ladder, Defect Calculus, an IFF characterization), footprint exactly
[propext, Classical.choice, Quot.sound], kernel VERIFIED, external court review, byte-
bound FINAL.json receipts (oracle/frontier_formalizer/work/EG411-*/). See memory
eg411-balance-law-kernel-checked. The formalizer discovers new mathematics in MSL flow
and certifies it, discovery to receipt in one session.

What my #710 close-driver actually did: it called `run_obligation` (the raw kernel cable)
on hand-written `by decide` checks of numbers Python had already computed. That is the
bottom slice of the stack — a calculator use — and it BYPASSED the real formalizer
campaign entirely (deterministic reduce -> research arena -> authored Lean THEOREM
statement -> proof search -> semantic court -> kernel verify -> FINAL.json). The 2
"KERNEL_CHECKED" results (LO50, LO100) are genuine but tiny: each confirms one Python-
chosen index set is Hall-deficient. They prove no theorem about f, and did not use the
formalizer's actual power.

THE REAL PATH to certified #710 mathematics (not a plumbing IOU, real work): author the
theorem — the doubling reduction (T2), or the prime-descent law (M2) as a general
statement over the relevant range, or a Hall-deficiency lemma — and run the ACTUAL
frontier-formalizer campaign the way EG411 was run, landing a clean-axiom FINAL.json with
court review. The close driver should hand the formalizer a THEOREM, not per-n arithmetic.
