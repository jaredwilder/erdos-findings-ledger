---
id: erdos142-lower-arm-k3-closed-by-citation
claim: |-
  Erdos 142 lower arm: k=2 and k=3 CLOSED, k>=4 is the exact residue
status: validated-observational
tier: silver
reality_score: 0.8
effect: |-
  erdos_142.variants.lower states r_k(N)=o(N/log N) for 1<k -- the only arm of the four whose Lean statement is a proposition rather than an answer(sorry) hole. k=2: every pair is a non-trivial 2-AP so r_2(N)<=1=o(N/log N), closed trivially. k=3: Bloom & Sisask 2020 (10.48550/arxiv.2007.03528, OpenAlex W3038544589, verbatim abstract sha256 229cf96cd69ae261) prove |A| << N/(log N)^{1+c} for absolute c>0, and (log N)^{-c}->0 gives r_3(N)=o(N/log N) -- CLOSED at row 3 by citation. The same abstract states this is 'the first non-trivial case', which certifies the boundary: k>=4 is untouched and is the exact residue of this arm
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/evidence/erdos142-k3-citation/bloom-sisask-record.json
  - oracle/evidence/erdos142-k3-citation/corpus.json
  - oracle/evidence/targets/lean-attackability-audit.json
open_threads: []
provenance: |-
  (not provided)
---

# Erdos 142 lower arm: k=2 and k=3 CLOSED, k>=4 is the exact residue

**Status: validated-observational** · tier `silver` · reality_score 0.8

**Effect / numbers.**

erdos_142.variants.lower states r_k(N)=o(N/log N) for 1<k -- the only arm of the four whose Lean statement is a proposition rather than an answer(sorry) hole. k=2: every pair is a non-trivial 2-AP so r_2(N)<=1=o(N/log N), closed trivially. k=3: Bloom & Sisask 2020 (10.48550/arxiv.2007.03528, OpenAlex W3038544589, verbatim abstract sha256 229cf96cd69ae261) prove |A| << N/(log N)^{1+c} for absolute c>0, and (log N)^{-c}->0 gives r_3(N)=o(N/log N) -- CLOSED at row 3 by citation. The same abstract states this is 'the first non-trivial case', which certifies the boundary: k>=4 is untouched and is the exact residue of this arm

**Receipts.**

- `oracle/evidence/erdos142-k3-citation/bloom-sisask-record.json`
- `oracle/evidence/erdos142-k3-citation/corpus.json`
- `oracle/evidence/targets/lean-attackability-audit.json`


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
