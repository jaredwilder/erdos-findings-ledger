---
id: graham-alspach-z29-z31-fully-closed
claim: |-
  Graham-Alspach sequenceability: Z_29 and Z_31 fully closed (all subset sizes)
status: validated-observational
tier: silver
reality_score: 0.65
domain: combinatorics
effect: |-
  Graham-Alspach sequenceability: Z_29 and Z_31 FULLY CLOSED (every subset size) -- every k-subset admits an ordering with all partial sums distinct and nonzero mod p. 1.64M witnesses, 2 independent checkers (Go+Python) + EPCE third, 0 disagreements. Z_37/41/43/47/59/61 partial (top band only). Primitive-root geometric sequencing is a general full-set theorem lead (valid on 11/11 tested primes).
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/ledger/armory/formal.md
blades: |-
  T-GRAHAM-multiplicative-orbit-reduction, T-GRAHAM-primitive-root-geometric-sequencing, T-GRAHAM-independent-multi-checker-crosscheck
open_threads: []
provenance: |-
  KBK math program, 0-dollar deterministic zero-LLM; dual-checker + EPCE verified. Author: Jared Wilder.
domain_lane: math
domain_lane_source: domain-exact
---

# Graham-Alspach sequenceability: Z_29 and Z_31 fully closed (all subset sizes)

**Status: validated-observational** · tier `silver` · reality_score 0.65 · domain combinatorics

**Effect / numbers.**

Graham-Alspach sequenceability: Z_29 and Z_31 FULLY CLOSED (every subset size) -- every k-subset admits an ordering with all partial sums distinct and nonzero mod p. 1.64M witnesses, 2 independent checkers (Go+Python) + EPCE third, 0 disagreements. Z_37/41/43/47/59/61 partial (top band only). Primitive-root geometric sequencing is a general full-set theorem lead (valid on 11/11 tested primes).

**Receipts.**

- `oracle/ledger/armory/formal.md`

**Blades.**

T-GRAHAM-multiplicative-orbit-reduction, T-GRAHAM-primitive-root-geometric-sequencing, T-GRAHAM-independent-multi-checker-crosscheck

**Provenance.**

KBK math program, 0-dollar deterministic zero-LLM; dual-checker + EPCE verified. Author: Jared Wilder.


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
