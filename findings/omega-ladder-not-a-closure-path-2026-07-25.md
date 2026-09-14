---
id: omega-ladder-not-a-closure-path-2026-07-25
claim: |-
  EG411 omega-ladder is provably NOT a closure path (cap grows ~2.47k)
status: validated-observational
tier: gold
reality_score: 0.8
domain: number-theory
effect: |-
  NEGATIVE STRUCTURAL RESULT. For squarefree N=p1..pk, 3phi(N)=2N+2 is equivalent to prod(1-1/p_i)=2/3+2/(3N). If all primes >= c then a solution needs (1-1/c)^k <= 2/3, giving the closed-form cap p1 < 1/(1-(2/3)^(1/k)) ~ k/ln(3/2) ~ 2.47k. VALIDATED against the generated kill-trees exactly: k=6 -> p1<15.3 -> {5,7,11,13}; k=7 -> p1<17.8 -> {5,7,11,13,17}, both matching the generated roots. CONSEQUENCE: the cap GROWS LINEARLY in k, so the search tree strictly inflates as you climb (observed ~130x per rung; k=11 -> 110480 nodes, k=12 -> >14.38M and unfinished). There is no k at which the tree collapses for a structural reason. The omega-ladder is therefore a BOUNDING program with no terminal rung - an infinite regress by construction - and cannot close EG411 r=2 no matter how far it is climbed. Rungs are not wedges. This retires an entire attack direction.
inputs: |-
  0 dollars, deterministic, no network, no LLM
cohort: |-
  (see effect)
receipts:
  - oracle/math/EG411Formal/EG411Formal/OmegaTreeSupport.lean
  - oracle/math/EG411Formal/EG411Formal/MultiplicativeBalance.lean
blades: |-
  cap_kill_balance
open_threads:
  - {blade: "prove the uniform wedge: doubly-exponential prime growth in 3phi(N)=2N+2 forces N+1 to be {2,3}-smooth. One statement uniform in k", value: med, data: in-hand, cost: med, why: ""}
  - {blade: both neighbours already proven (cascade characterisation + cascade lemma), so it would close EG411 r=2., value: med, data: in-hand, cost: med, why: ""}
provenance: |-
  session 2026-07-25, 0 dollar deterministic zero-LLM
domain_lane: math
domain_lane_source: domain-exact
---

# EG411 omega-ladder is provably NOT a closure path (cap grows ~2.47k)

**Status: validated-observational** · tier `gold` · reality_score 0.8 · domain number-theory

**Effect / numbers.**

NEGATIVE STRUCTURAL RESULT. For squarefree N=p1..pk, 3phi(N)=2N+2 is equivalent to prod(1-1/p_i)=2/3+2/(3N). If all primes >= c then a solution needs (1-1/c)^k <= 2/3, giving the closed-form cap p1 < 1/(1-(2/3)^(1/k)) ~ k/ln(3/2) ~ 2.47k. VALIDATED against the generated kill-trees exactly: k=6 -> p1<15.3 -> {5,7,11,13}; k=7 -> p1<17.8 -> {5,7,11,13,17}, both matching the generated roots. CONSEQUENCE: the cap GROWS LINEARLY in k, so the search tree strictly inflates as you climb (observed ~130x per rung; k=11 -> 110480 nodes, k=12 -> >14.38M and unfinished). There is no k at which the tree collapses for a structural reason. The omega-ladder is therefore a BOUNDING program with no terminal rung - an infinite regress by construction - and cannot close EG411 r=2 no matter how far it is climbed. Rungs are not wedges. This retires an entire attack direction.

**Inputs.**

0 dollars, deterministic, no network, no LLM

**Receipts.**

- `oracle/math/EG411Formal/EG411Formal/OmegaTreeSupport.lean`
- `oracle/math/EG411Formal/EG411Formal/MultiplicativeBalance.lean`

**Blades.**

cap_kill_balance

**Open threads (next blades).**

- **prove the uniform wedge: doubly-exponential prime growth in 3phi(N)=2N+2 forces N+1 to be {2,3}-smooth. One statement uniform in k** (value med · data in-hand · cost med) — 
- **both neighbours already proven (cascade characterisation + cascade lemma), so it would close EG411 r=2.** (value med · data in-hand · cost med) — 

**Provenance.**

session 2026-07-25, 0 dollar deterministic zero-LLM


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
