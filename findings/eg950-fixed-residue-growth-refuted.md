---
id: eg950-fixed-residue-growth-refuted
claim: |-
  EG#950: fixed-residue k-rough sieve admissible for all k, growth mechanism refuted
status: open
tier: bronze
reality_score: 0.35
domain: number-theory
effect: |-
  EG#950 reciprocal-sum clusters: the fixed-residue k-rough sieve is admissible-by-construction for all k (cross-checked to k=300), but its growth mechanism is REFUTED: S(k) oscillates ~[0.58,1.36], slope ~0 vs ln k (R^2=0.0003/0.0754) to k=7000. A real validated negative result; true extremal S(k) boundedness remains OPEN.
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/math/attacks/erdos950-fn-reciprocal-cluster-2026-07-15/
blades: |-
  T-950-fixed-residue-k-rough-sieve, T-950-fft-convolution-sieve-fn
open_threads: []
provenance: |-
  KBK math program, 0-dollar deterministic zero-LLM. Author: Jared Wilder.
domain_lane: math
domain_lane_source: domain-exact
---

# EG#950: fixed-residue k-rough sieve admissible for all k, growth mechanism refuted

**Status: open** · tier `bronze` · reality_score 0.35 · domain number-theory

**Effect / numbers.**

EG#950 reciprocal-sum clusters: the fixed-residue k-rough sieve is admissible-by-construction for all k (cross-checked to k=300), but its growth mechanism is REFUTED: S(k) oscillates ~[0.58,1.36], slope ~0 vs ln k (R^2=0.0003/0.0754) to k=7000. A real validated negative result; true extremal S(k) boundedness remains OPEN.

**Receipts.**

- `oracle/math/attacks/erdos950-fn-reciprocal-cluster-2026-07-15/`

**Blades.**

T-950-fixed-residue-k-rough-sieve, T-950-fft-convolution-sieve-fn

**Provenance.**

KBK math program, 0-dollar deterministic zero-LLM. Author: Jared Wilder.


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
