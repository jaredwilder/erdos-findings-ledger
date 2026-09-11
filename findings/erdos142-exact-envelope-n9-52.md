---
id: erdos142-exact-envelope-n9-52
claim: |-
  SUPERSEDED: headline understated the receipt (44/n<=52 vs receipt 46/n<=54)
status: superseded
tier: bronze
reality_score: 0.6
effect: |-
  Superseded by erdos142-exact-envelope-n9-54. The claim line asserted 44 exact values to n=52 while its own pinned receipt scan-9-60.json records proven_count=46 and envelope_max_n=54. The n=52 figure came from a single contended-CPU trial; three subsequent runs gave 54. Banking must match the receipt it cites
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/evidence/erdos142-exact-envelope/scan-9-60.json
open_threads: []
provenance: |-
  (not provided)
---

# SUPERSEDED: headline understated the receipt (44/n<=52 vs receipt 46/n<=54)

**Status: superseded** · tier `bronze` · reality_score 0.6

**Effect / numbers.**

Superseded by erdos142-exact-envelope-n9-54. The claim line asserted 44 exact values to n=52 while its own pinned receipt scan-9-60.json records proven_count=46 and envelope_max_n=54. The n=52 figure came from a single contended-CPU trial; three subsequent runs gave 54. Banking must match the receipt it cites

**Receipts.**

- `oracle/evidence/erdos142-exact-envelope/scan-9-60.json`


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
