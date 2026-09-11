---
id: circulant-ramsey-family-elimination
claim: |-
  No circulant graph on 40 vertices witnesses R(3,10) > 40, and no circulant graph on 36 vertices
  witnesses R(4,6) > 36. Both circulant families were enumerated exhaustively and completely --
  1,048,575 and 262,143 connection sets respectively, 1,310,718 in total, zero survivors. Produced
  unattended by the autonomous frontier loop and re-verified by a standalone checker that shares no
  code with the search.
status: closed
tier: silver
reality_score: 0.9
domain: math
origin: this_estate
artifact_kind: family_elimination
truth_mode: certified
scope_grade: one_construction_family_at_one_order
inference: deductive
independence: independently_reverified
reproducibility: artifact_verified
novelty: not_cleared
claim_ir:
  claim_id: "extremal_graph_theory:circulant_ramsey_family_elimination"
  assertion_kind: exhaustive_negative
  display: "No circulant witness for R(3,10)>40 or R(4,6)>36; both families exhausted."
  scope:
    domain: extremal_graph_theory
    label: "circulant graphs on Z_40 and Z_36 only"
  definitions:
    circulant: "graph on Z_n with i~j iff (i-j) mod n lies in a connection set S satisfying S = -S, 0 not in S"
    witness: "a graph with no K_k and no independent set of size l; such a graph proves R(k,l) > n"
  tags: [ramsey, circulant, exhaustive_search, family_elimination, autonomous]
claims:
  - id: r3_10_n40_no_circulant_witness
    inference: deductive
    truth_mode: certified
    status: closed
  - id: r4_6_n36_no_circulant_witness
    inference: deductive
    truth_mode: certified
    status: closed
---

# No circulant witness at R(3,10) n=40 or R(4,6) n=36

## RESULT

| case | connection sets tested | family size | complete | witnesses |
|---|---|---|---|---|
| R(3,10), n=40 | **1,048,575** | 1,048,575 | ✅ | **0** |
| R(4,6), n=36 | **262,143** | 262,143 | ✅ | **0** |

A circulant graph on `Z_n` is given by a connection set `S` with `S = -S` and `0 ∉ S`; vertices
`i,j` are adjacent iff `(i−j) mod n ∈ S`. Every such graph at these two orders contains either a
`K_k` or an independent set of size `l`.

## ⛔ SCOPE — READ BEFORE CITING

This eliminates **one construction family at one order**. It is **not** a determination of
`R(3,10)` or `R(4,6)`, and it is **not** evidence that no non-circulant witness exists. A failed
search over one family is not a bound in either direction. The published state of both numbers is
unchanged by this result.

## THE FAMILY SIZE IS THE WHOLE CORRECTNESS QUESTION — AND THE FIRST RUN GOT IT WRONG

For **odd** `n`, every shift `s` pairs with a distinct partner `n−s`, so `S` is determined by a
subset of `{1..(n−1)/2}`.

For **even** `n`, the shift `n/2` is **its own inverse** and is an independent, legitimate element.
The family is therefore `2^(n/2)`, not `2^(n/2 − 1)`.

**The first run missed this and claimed completeness on half the family.** At `n = 40` it searched
`2¹⁹ − 1 = 524,287` and reported `exhausted: True`; the true family is `2²⁰ − 1 = 1,048,575`.

The tell was arithmetic, not a crash: `tried` landed *exactly* on a power of two minus one, which
is what an enumeration bound looks like when it is off by one generator. The claim was retracted
and both cases re-run. The standalone verifier now **recomputes the family size from the
definition** so the count is checkable rather than asserted.

## INDEPENDENT RE-VERIFICATION

Verifier: `oracle/library/patents/artifacts/verify_circulant_ramsey_exhaustion.py` — stdlib only,
no estate imports, no shared code with the search.

- Adjacency is rebuilt from the definition (`i~j iff (i−j) mod n ∈ S`), not from the search's
  representation
- Cliques and independent sets are decided **exactly** by branch and bound, not sampled
- Independent sets are decided as cliques in the complement

**The negative control is load-bearing.** An exhaustion checker that can only ever report "no
witness" has proved nothing — it may simply be broken. Since `R(3,3) = 6`, a circulant witness
**must** exist on 5 vertices and **must not** on 6. The verifier finds **2 on 5** and **0 on 6**.
It demonstrably accepts and rejects, so its zeros carry information.

Receipt: `oracle/ledger/receipts/circulant-ramsey-family-elimination.json`
Evidence: `oracle/evidence/circulant-ramsey-exhaustion.json`

## HOW IT WAS PRODUCED — THE POINT OF THIS ENTRY

Generated **unattended** by `oracle/tools/frontier_jobs.py` driving the autonomy supervisor:
the loop selected the targets from the 9,926-row ingested frontier by priority, attacked each
through `frontier_bridge`, recorded honest `INCONCLUSIVE` verdicts, escalated the budget rung, and
continued to the next target with no human in the loop.

It also **found a defect in its own instrument**: at the first budget the naive verifier could not
finish a single check — `C(47,11) = 17,417,133,617` subsets for one candidate graph — so a
60-second budget overran to 370s and the declared budget was decorative. Replacing subset
enumeration with branch and bound raised throughput roughly 800× and made the budget exact, which
is what made complete exhaustion reachable at all.

## Falsifier

A connection set `S ⊆ Z_40` (or `Z_36`) with `S = −S`, `0 ∉ S`, whose circulant graph has no `K_3`
and no independent set of size 10 (resp. no `K_4` and no independent 6-set). The verifier accepts a
witness and will report it.

## Novelty — THE GATE SAID NOVEL AND I DO NOT BELIEVE IT

`noveltyforge` returned **`NOVEL` / `NOVEL_CLEAR_TO_PURSUE`**, admissible
(`novel_and_real_and_patent_axis_live`), corpus 82, top collision `US11461581` at **0.0900**,
`anticipates: false`.

**That verdict is recorded and NOT acted on.** Look at what it collided with: two US patents and a
1991 *Journal of Chemical Physics* paper. The auto-acquired corpus never reached the extremal
combinatorics literature at all. Small-Ramsey circulant searches are a heavily trodden space —
Radziszowski's dynamic survey *Small Ramsey Numbers* (DS1) catalogues exactly this kind of
computation, and this estate ingested that very PDF for its bounds — so a clean novelty result
here is far more likely a **corpus gap than whitespace**.

    A NOVELTY GREEN FROM A CORPUS THAT CANNOT SEE THE FIELD IS NOT EVIDENCE OF NOVELTY.

Verdict: `oracle/evidence/novelty/circulant-ramsey-elimination-verdict.json`.
Status held at **`novelty: not_cleared`** in the frontmatter. Clearing it requires a prior-art pass
against DS1 and the circulant-Ramsey literature specifically, which has not been done.
