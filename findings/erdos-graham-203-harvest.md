---
id: erdos-graham-203-harvest
claim: |-
  Erdos-Graham #203 harvest: numerical theorem tau(m)<=5 (m<=1e6), 2nd-moment orthogonality lemma, Claude Lemma 15
status: open
tier: raw
reality_score: 0.1
domain: math
# --- DEMOTED 2026-07-26 -----------------------------------------------------
# reality_score 0.3 -> 0.1. NOT because the content is wrong, but because the
# BASIS is an LLM-written referee document with no machine verification and no
# proof-checker receipt. Its own notes say so: "NOT machine-verified in-repo",
# "NEEDS HUMAN VERIFICATION", parent EG#203 resolution WITHDRAWN.
# This record must NOT be consumed as evidence by any downstream reasoner until
# at least one claim is re-derived under a real checker. An unverified deductive
# claim is not a weak result — it is an UNCHECKED one, which is a different thing
# and a more dangerous one, because its form looks like a theorem.
evidence_status: unverified_llm_authored
consumable_as_evidence: false
# --- OEC DECLARATIONS (2026-07-26) ---
# DIAGNOSTIC, NOT EVIDENCE. An LLM-authored referee document with no proof-checker
# receipt. 'diagnostic' + 'observed' is the floor and it is deliberate: this record
# must never be able to satisfy an obligation.
artifact_kind: diagnostic
truth_mode: observed
scope_grade: bounded_family
inference: inductive
independence: single_path
reproducibility: undocumented
novelty: unchecked
claim_ir:
  claim_id: "eg203_harvest:candidate_leads"
  assertion_kind: conjecture
  display: "Three candidate results surfaced by an emulated-referee pass; none machine-verified."
  scope:
    domain: number_theory
    label: "EG203 research corpus, 211 files"
  statement:
    op: unverified_candidate_set
    args:
      - {op: const, args: ["erdos_graham_203", "target"]}
  definitions:
    status: "NOT machine-verified in-repo; parent EG203 resolution WITHDRAWN"
  tags: [erdos, harvest, unverified, do_not_cite]
# --- PER-CLAIM TYPING (schema v2, 2026-07-26) ---
claims:
  - id: tau_numerical
    statement: "For all m <= 10^6 coprime to 6 there exist (k,l), k+l <= 45, with 2^k·3^l·m + 1 prime, and tau(m) = min(k+l) <= 5 uniformly."
    inference: deductive
    closure: open
    basis: numerical search to 10^6 (no certified-arithmetic checker, no in-repo receipt)
    why: >-
      Properly SCOPED to m <= 10^6, so the form is deductive — but the search was never
      re-run under a checker in this repo. Deductive-in-form, UNVERIFIED-in-fact.
      Closure route is mechanical: re-run to 10^7 under certified arithmetic.
  - id: second_moment_lemma
    statement: "E_m|Delta_m(q)|² = 1/|Gamma_q| − 1/(q−1), with CRT cross-moments vanishing."
    inference: deductive
    closure: open
    basis: analytic derivation, relative error <= 1e-16 numerically
    why: A derivation, but unverified in-repo. Same status as above.
  - id: claude_lemma_15
    statement: "Unconditional n=2 BVK-Kummer-Chebotarev on the degree-8 Q(sqrt2, sqrt3) tower."
    inference: deductive
    closure: open
    basis: asserted by an LLM referee pass; NO proof-checker receipt
    why: >-
      DO NOT CITE. An LLM asserting a proof is not evidence of a proof — this estate
      runs on tool output, never on a model's say-so. Needs a human number theorist
      or a formalization. Flagged "NEEDS HUMAN VERIFICATION" by its own author.
effect: |-
  Emulated-referee harvest of the Erdos-Graham #203 corpus surfaces 3 candidate results. (1.1) NUMERICAL THEOREM: for all m<=1e6 coprime to 6 there exist (k,l) with k+l<=45 such that 2^k*3^l*m+1 is prime, and tau(m)=min(k+l)<=5 uniformly (unconditional, numerical; incl. the 1D Sierpinski number 78557 has tau_2D=3). (1.3) 2nd-moment orthogonality lemma: E_m|Delta_m(q)|^2 = 1/|Gamma_q| - 1/(q-1) with CRT cross-moment vanishing (unconditional, rel err <=1e-16). (2.2) Claude Lemma 15: unconditional n=2 BVK-Kummer-Chebotarev on the degree-8 Q(sqrt2,sqrt3) tower (NEEDS HUMAN VERIFICATION). HONEST: this is an EMULATED-referee document, NOT machine-verified in-repo; L15 and L8 are explicitly conditional; the parent EG#203 resolution was WITHDRAWN (memory eg203_wilder2026_withdrawn). Candidate leads for human refereeing, not established theorems.
inputs: |-
  $0. Emulated-Erdos referee pass over the #203 research corpus (211 files). Candidate-extraction, not machine verification. No live proof-checker receipts attached.
cohort: |-
  Erdos-Graham #203 research corpus (numerical search to 1e6; empirical verifications R573/R599/R600/R682/R691).
receipts:
  - oracle/research/findings/harvest-swarm/erdos-emulated-harvest.md
blades: |-
  emulated-referee 7-pass harvest (triage of non-believed claims + Pass 1 CLEAR / Pass 2 HIDDEN). NOT a machine proof-checker; several items flagged conditional or needing human verification.
open_threads:
  - {blade: human-verify-L15, value: high, data: needs-acquire, cost: high, why: "have a number theorist verify Claude Lemma 15 (unconditional n=2 Chebotarev) - the strongest single fruit"}
  - {blade: machine-verify-numerical, value: high, data: in-hand, cost: med, why: "re-run tau(m)<=5 to 1e7 under a certified-arithmetic checker to bank the numerical theorem"}
  - {blade: deposit-priority, value: med, data: in-hand, cost: low, why: "Zenodo DOI deposit of the corpus to establish priority"}
provenance: |-
  harvest-swarm emulated-Erdos referee (claude-opus-4.7), $0. Candidate results only; parent #203 WITHDRAWN; L15/L8 conditional.
domain_lane: math
domain_lane_source: domain-exact
---

# Erdos-Graham #203 harvest: numerical theorem tau(m)<=5 (m<=1e6), 2nd-moment orthogonality lemma, Claude Lemma 15

**Status: open** · tier `raw` · reality_score 0.3 · domain math

**Effect / numbers.**

Emulated-referee harvest of the Erdos-Graham #203 corpus surfaces 3 candidate results. (1.1) NUMERICAL THEOREM: for all m<=1e6 coprime to 6 there exist (k,l) with k+l<=45 such that 2^k*3^l*m+1 is prime, and tau(m)=min(k+l)<=5 uniformly (unconditional, numerical; incl. the 1D Sierpinski number 78557 has tau_2D=3). (1.3) 2nd-moment orthogonality lemma: E_m|Delta_m(q)|^2 = 1/|Gamma_q| - 1/(q-1) with CRT cross-moment vanishing (unconditional, rel err <=1e-16). (2.2) Claude Lemma 15: unconditional n=2 BVK-Kummer-Chebotarev on the degree-8 Q(sqrt2,sqrt3) tower (NEEDS HUMAN VERIFICATION). HONEST: this is an EMULATED-referee document, NOT machine-verified in-repo; L15 and L8 are explicitly conditional; the parent EG#203 resolution was WITHDRAWN (memory eg203_wilder2026_withdrawn). Candidate leads for human refereeing, not established theorems.

**Inputs.**

$0. Emulated-Erdos referee pass over the #203 research corpus (211 files). Candidate-extraction, not machine verification. No live proof-checker receipts attached.

**Cohort.**

Erdos-Graham #203 research corpus (numerical search to 1e6; empirical verifications R573/R599/R600/R682/R691).

**Receipts.**

- `oracle/research/findings/harvest-swarm/erdos-emulated-harvest.md`

**Blades.**

emulated-referee 7-pass harvest (triage of non-believed claims + Pass 1 CLEAR / Pass 2 HIDDEN). NOT a machine proof-checker; several items flagged conditional or needing human verification.

**Open threads (next blades).**

- **human-verify-L15** (value high · data needs-acquire · cost high) — have a number theorist verify Claude Lemma 15 (unconditional n=2 Chebotarev) - the strongest single fruit
- **machine-verify-numerical** (value high · data in-hand · cost med) — re-run tau(m)<=5 to 1e7 under a certified-arithmetic checker to bank the numerical theorem
- **deposit-priority** (value med · data in-hand · cost low) — Zenodo DOI deposit of the corpus to establish priority

**Provenance.**

harvest-swarm emulated-Erdos referee (claude-opus-4.7), $0. Candidate results only; parent #203 WITHDRAWN; L15/L8 conditional.


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
