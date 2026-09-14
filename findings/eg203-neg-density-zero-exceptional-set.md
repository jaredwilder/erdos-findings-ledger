---
id: eg203-neg-density-zero-exceptional-set
claim: |-
  EG#203: exceptional set has density zero (unconditional, Gamma-fiber companion)
status: validated-observational
tier: gold
reality_score: 0.85
domain: number-theory
effect: |-
  Unconditional density-zero of the EG#203 exceptional set (m coprime to 6 with m*2^k*3^l+1 composite for all k,l). Companion Gamma-fiber paper: exact fiber |B_q(c)|=gcd(a_q,b_q)*1_{Gamma_q}(c); Delta_m(q) closed form + Pappalardi eta=1/12 (no GRH) giving |Delta_m(q)|<q^-0.5 on density-one primes; CRT cross-moment vanishing => O(1) variance of sum_q lambda_q Delta_m(q) => Markov => #{m<=M exceptional} << M(log M)^-c, c in (0,0.1]. Empirically anchored: 259/259 (q,m) pairs, moment laws 0 error to 1e-16.
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/math/papers/companion_gamma_fiber_local_density.tex
blades: |-
  T-EG203-gamma-fiber-local-density, T-EG203-moment-laws, T-EG203-density-zero-kummer-obstruction-schema
open_threads: []
provenance: |-
  18-paper Kummer corpus (companion note), 0-dollar deterministic zero-LLM; verified by hand + empirical R682/R691-VERIFY. Author: Jared Wilder.
domain_lane: math
domain_lane_source: domain-exact
---

# EG#203: exceptional set has density zero (unconditional, Gamma-fiber companion)

**Status: validated-observational** · tier `gold` · reality_score 0.85 · domain number-theory

**Effect / numbers.**

Unconditional density-zero of the EG#203 exceptional set (m coprime to 6 with m*2^k*3^l+1 composite for all k,l). Companion Gamma-fiber paper: exact fiber |B_q(c)|=gcd(a_q,b_q)*1_{Gamma_q}(c); Delta_m(q) closed form + Pappalardi eta=1/12 (no GRH) giving |Delta_m(q)|<q^-0.5 on density-one primes; CRT cross-moment vanishing => O(1) variance of sum_q lambda_q Delta_m(q) => Markov => #{m<=M exceptional} << M(log M)^-c, c in (0,0.1]. Empirically anchored: 259/259 (q,m) pairs, moment laws 0 error to 1e-16.

**Receipts.**

- `oracle/math/papers/companion_gamma_fiber_local_density.tex`

**Blades.**

T-EG203-gamma-fiber-local-density, T-EG203-moment-laws, T-EG203-density-zero-kummer-obstruction-schema

**Provenance.**

18-paper Kummer corpus (companion note), 0-dollar deterministic zero-LLM; verified by hand + empirical R682/R691-VERIFY. Author: Jared Wilder.


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
