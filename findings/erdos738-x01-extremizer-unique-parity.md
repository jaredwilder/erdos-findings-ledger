---
id: erdos738-x01-extremizer-unique-parity
claim: |-
  X01 executed: T06 bound tight for all n<=10 and the extremizer is UNIQUE at every n, equal to the parity-defect host
status: validated-observational
tier: silver
reality_score: 0.8
effect: |-
  CP-SAT enumeration under the bank's verbatim constraints (T01 diagonal zero, T02/T03 parent exclusion). Max |supp(A_c)| = floor(n^2/2) at every n=1..10, matching T06 exactly. Full solution enumeration returns exactly ONE extremizer per n, and at every n it is the opposite-parity pattern a+b odd -- i.e. precisely the T08 parity-defect host. X01 asked to classify all extremizers; the classification is: the extremizer exists, is unique, and is the parity host
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/evidence/erdos738-import/X01-extremizer-classification.json
  - oracle/evidence/erdos738-import/frozen-statements.json
open_threads: []
provenance: |-
  (not provided)
---

# X01 executed: T06 bound tight for all n<=10 and the extremizer is UNIQUE at every n, equal to the parity-defect host

**Status: validated-observational** · tier `silver` · reality_score 0.8

**Effect / numbers.**

CP-SAT enumeration under the bank's verbatim constraints (T01 diagonal zero, T02/T03 parent exclusion). Max |supp(A_c)| = floor(n^2/2) at every n=1..10, matching T06 exactly. Full solution enumeration returns exactly ONE extremizer per n, and at every n it is the opposite-parity pattern a+b odd -- i.e. precisely the T08 parity-defect host. X01 asked to classify all extremizers; the classification is: the extremizer exists, is unique, and is the parity host

**Receipts.**

- `oracle/evidence/erdos738-import/X01-extremizer-classification.json`
- `oracle/evidence/erdos738-import/frozen-statements.json`


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
