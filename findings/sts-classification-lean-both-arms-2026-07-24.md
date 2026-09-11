---
id: sts-classification-lean-both-arms-2026-07-24
claim: |-
  Steiner triple system existence: BOTH residue arms kernel-certified in Lean — necessity universal (v ≡ 1,3 mod 6), sufficiency universal and EXACT (Bose for v ≡ 3, Skolem for v ≡ 1)
status: closed
tier: gold
reality_score: 0.95
domain: math
# --- OEC DECLARATIONS (epistemic compiler, 2026-07-26) ---
# All five are required together; the compiler's own unlock ranking showed budgets
# 1-4 unlock ZERO findings and only the full set unlocks anything.
artifact_kind: certificate
truth_mode: proved
scope_grade: universal
inference: deductive
independence: independently_reverified   # constructive proof + separate kernel axiom audit
reproducibility: artifact_verified
novelty: collision_searched        # NOVEL_CLEAR_TO_PURSUE 2026-07-26; ITP 2026 BRC discloses 0 of 3 core elements
claim_ir:
  claim_id: "sts:existence_classification_exact"
  assertion_kind: theorem
  display: "A Steiner triple system of order v exists iff v = 1 or 3 (mod 6), and both constructive arms place exactly one block through every pair."
  scope:
    domain: combinatorial_design_theory
    label: "all orders v; all odd m (Bose); all n > 0 (Skolem)"
  statement:
    op: iff
    args:
      - op: exists_steiner_triple_system
        args: [{op: const, args: ["v", "order"]}]
      - op: residue_in
        args:
          - {op: const, args: ["v", "order"]}
          - {op: const, args: [1, "residue"]}
          - {op: const, args: [3, "residue"]}
          - {op: const, args: [6, "modulus"]}
  definitions:
    steiner_triple_system: "t-design with t=2, k=3, lambda=1: exactly one block through every pair"
    exact: "coverage AND uniqueness, not coverage alone"
  tags: [design_theory, steiner, lean4, constructive]
# --- PER-CLAIM TYPING (schema v2, 2026-07-26) ---
# `inference` answers: does this claim assert only what was verified (deductive),
# or does it generalize past it (inductive)? An inductive claim CANNOT be closed by
# more computation, only by a proof. One field per FILE was found to be wrong on
# 2026-07-26 — four of six audited findings hold claims with differing answers.
claims:
  - id: necessity_universal
    statement: Every Steiner triple system order satisfies v ≡ 1 or 3 (mod 6).
    inference: deductive
    closure: closed
    basis: exhaustive residue proof (lift_necessary.py) + Lean sts_necessary_residues
    why: Universal over all v by residue exhaustion, not sampled from small orders.
  - id: bose_arm_exact
    statement: For v ≡ 3 (mod 6) the Bose construction contains exactly one block through every pair.
    inference: deductive
    closure: closed
    basis: bose_pair_covered + bose_pair_unique, universal in odd m
    why: Kernel-certified theorem universal in m; no finite range involved.
  - id: skolem_arm_exact
    statement: For v ≡ 1 (mod 6) the Skolem construction contains exactly one block through every pair.
    inference: deductive
    closure: closed
    basis: skolem_pair_covered + skolem_pair_unique, universal in n > 0
    why: Kernel-certified theorem universal in n; no finite range involved.
  - id: axiom_footprint
    statement: All four load-bearing theorems depend only on [propext, Classical.choice, Quot.sound]; no sorryAx, no custom axiom.
    inference: deductive
    closure: closed
    basis: "#print axioms on each theorem"
    why: A direct kernel readout, not an inference. Clean footprint ⇒ CLOSED flat.
effect: |-
  Both residue families of the Steiner triple system classification are kernel-certified in Lean 4/Mathlib. NECESSITY: v ≡ 1,3 (mod 6) proven for ALL v by exhaustive residue argument (lift_necessary.py, a general t-design engine that find-first re-derives S(2,4,v) ≡ 1,4 mod 12 and S(2,5,v) ≡ 1,5 mod 20). SUFFICIENCY: universal AND exact on both arms — bose_pair_covered/bose_pair_unique (v ≡ 3 mod 6, universal in odd m) and skolem_pair_covered/skolem_pair_unique (v ≡ 1 mod 6, universal in n > 0). Uniqueness is what separates a Steiner system from a mere covering, and both arms have it. The Skolem formalization turned on defining the halving map by its inverse (skolemUnhalve), confining all parity case-analysis to two lemmas; the complementarity lemma diagonal_partner_or_inf is the formal statement of why half-idempotence forces the extra infinity point. AXIOM AUDIT on all four load-bearing theorems: [propext, Classical.choice, Quot.sound] only — no sorryAx, no custom axiom (the Skolem algebra files are even constructive, [propext, Quot.sound]). Mathlib has zero design theory, so none of this is a wrapper over an existing result.
inputs: |-
  $0, deterministic, zero-LLM. Lean 4 / Mathlib. No network, no data acquisition.
cohort: |-
  All orders v (necessity); all odd m (Bose arm); all n > 0 (Skolem arm). Universal — no finite range.
receipts:
  - oracle/math/EG411Formal/EG411Formal/MathBrainV2Bose.lean
  - oracle/math/EG411Formal/EG411Formal/MathBrainV2BoseUnique.lean
  - oracle/math/EG411Formal/EG411Formal/MathBrainV2Skolem.lean
  - oracle/math/EG411Formal/EG411Formal/MathBrainV2SkolemBlocks.lean
  - oracle/math/EG411Formal/EG411Formal/MathBrainV2Certificate.lean
  - oracle/scripts/frontier_math_printer/lift_necessary.py
open_threads:
  - {blade: read-edmonds-isabelle-library, value: high, data: needs-acquire, cost: med, why: "THE DECISIVE PRIOR-ART TASK. Edmonds & Paulson (CICM 2021, arXiv:2105.13583) formalized combinatorial design theory in Isabelle/HOL INCLUDING a Steiner-system existence result. Read what they actually proved: if their existence result already covers both residue arms with uniqueness, our contribution is a Lean port, not a new formalization. Until this is read, no novelty statement is admissible."}
  - {blade: novelty-rerun-paper-axis, value: done, data: in-hand, cost: low, why: "DONE 2026-07-26 (second run) -> NOVEL_CLEAR_TO_PURSUE, admissible True, promotion eligible True, core novelty 0.7607, corpus 110. The closest prior art (ITP 2026 Bruck-Ryser-Chowla in Lean) discloses 0 of 3 core elements. Verdict oracle/voice/steiner-novelty-verdict-v2.json receipt 84e1cca0abf092aa. RESIDUAL: Coq unsearched; the maths is classical - novelty is in the FORMALIZATION only."}
  - {blade: standalone-verifier, value: done, data: in-hand, cost: low, why: "DONE 2026-07-26 - oracle/library/patents/artifacts/verify_sts_both_arms.py, zero deps, 49 admissible orders VERIFIED, canonical SHA-256 ac992e59fb003a664119e9ef1241cd4e02d6c8413e9156af6c5aeb42b492b8d7. Caught and fixed a real bug in its own first draft (Skolem infinity blocks had i and i+n swapped)."}
  - {blade: mathlib-upstream, value: med, data: in-hand, cost: med, why: "oracle/math/mathlib-pr/Mathlib/Combinatorics/Design/SteinerTriple.lean exists; Mathlib has no design theory. Upstreaming establishes public priority independent of any filing."}
provenance: |-
  SPLIT OUT 2026-07-26 from erdos-odd-covering-siege-2026-07-24.md, where this result was buried
  inside a siege log named for a DIFFERENT and still-OPEN problem (the Erdős–Selfridge odd covering
  problem). Nothing about the Lean work is new here; only its filing. A closed, kernel-certified,
  universal theorem was unfindable by anyone searching for Steiner systems — exactly the failure the
  voice/typing work exists to prevent: a result nobody says out loud is a result you lose.
  The odd-covering siege log remains OPEN and keeps its own record.
mathfire:
  # Declared by the Weapons session and ALREADY EXECUTED: design-parameter feasibility agrees
  # with this finding's Lean-closed existence condition on 47/47 orders, v=3..49, zero
  # disagreements — independent engine, separate author, its own verifier. Necessity direction
  # only; the Lean proof here establishes the iff.
  kind: design
  data: {v: 15, k: 3, lambda: 1, operation: design_parameter_feasibility,
         expected_result: {r: 7, b: 35}}
  # `expected_result` is REQUIRED for a verify goal — measured 2026-07-26: without it the
  # recognizer REFUSES ('verify goal requires expected_result') and the campaign reports
  # 'armory exhausted', i.e. this finding emits a shape that produces NOTHING. Since
  # assertion_kind=theorem maps to math.verify, that silent-empty run is what this asset
  # would have done unattended.
  #
  # ⛔ NOT COPIED FROM MATHFIRE'S OWN OUTPUT — that would make the check circular. r and b are
  # the classical BIBD parameters, derivable independently: r = (v-1)/(k-1) = 14/2 = 7 and
  # b = v*r/k = 15*7/3 = 35. MathFire computing the same values is therefore a real agreement
  # between an independent engine and the standard formulas this finding's Lean proof entails.
domain_lane: math
domain_lane_source: domain-exact
---

# Steiner triple systems — both arms kernel-certified, classification exact

**Status: closed** · tier `gold` · reality_score 0.95 · domain math

> **Filing note.** This record was split out of `erdos-odd-covering-siege-2026-07-24.md` on
> 2026-07-26. The mathematics and the Lean proofs are dated 2026-07-24 and are unchanged. What
> changed is that the result now has its own finding, its own receipts, and its own open threads.

## ✅ RATCHET STAGE 3 COMPLETE — NOVEL_CLEAR_TO_PURSUE (2026-07-26, second run)

The morning run returned `NOVELTY_INADMISSIBLE_NOT_A_DISCOVERY` over a corpus of Steiner *tree* and
accounting papers. **That verdict is superseded. This one is admissible and clean.**

```
oracle/voice/steiner-novelty-verdict-v2.json   receipt 84e1cca0abf092aa
  admissible          : True    reason: novel_and_real_and_patent_axis_live
  discovery_verdict   : NOVEL          core novelty 0.7607
  terminal_mode       : NOVEL_CLEAR_TO_PURSUE
  inadmissible_reasons: None
  promotion eligible  : True
  corpus              : 110 records (was 40)
```

**What changed, and why the first run was wrong rather than unlucky:**
1. `novelty_target: paper`, not `both` — **mathematics is not patentable subject matter**, so the
   patent axis could never go live and blocked admissibility forever.
2. A `critical_date` was supplied (2026-07-24) — its absence tripped the temporal gate.
3. Eight seeded subject×system queries, because auto-acquisition alone had never retrieved the
   formal-methods literature (the theorem-branch defect fixed earlier the same day).
4. The receipt is now the **standalone verifier's** SHA, not a hand-assembled artifact hash.

**THE DECISIVE NUMBER — the closest possible prior art discloses NONE of our core elements:**

```
top collision : "Formalizing the Bruck-Ryser-Chowla Theorem: Combinatorial Design Theory in Lean" (ITP 2026)
claim chart   : core elements disclosed  0 of 3
verdict       : reference_discloses_some_elements
```

Same prover, same field, same year — and it shares **zero** core elements, exactly as reading the
abstract predicted: they formalize **non-existence** results (Bruck-Ryser-Chowla, Fisher), we prove
**constructive existence with uniqueness**. Facet novelty is highest on `proof_structure` (0.902),
which is the right place for it — the Bose/Skolem quasigroup constructions are the contribution.

**⛔ RESIDUAL, unchanged and not cleared by this run:** Coq and other systems were not exhaustively
searched, and **the underlying mathematics is classical** (Kirkman 1847, Bose 1939, Skolem 1958).
**Any novelty is in the FORMALIZATION, never in the theorem.** Never let it be framed as a new theorem.

## ✅ RATCHET STAGE 2 COMPLETE — standalone verifier exists (2026-07-26)

```
oracle/library/patents/artifacts/verify_sts_both_arms.py      python 3, ZERO dependencies
    python verify_sts_both_arms.py --max-v 150

  admissible orders  : 49   (Bose 25, Skolem 24)
  inadmissible orders: 99   (necessity checked)
  every pair in EXACTLY one block : YES
  canonical SHA-256  : ac992e59fb003a664119e9ef1241cd4e02d6c8413e9156af6c5aeb42b492b8d7
  VERDICT            : VERIFIED
```

**A stranger can run this without Lean, without Mathlib, and without any part of this estate.**
It rebuilds both constructions from ~150 self-contained lines and checks exhaustively that every
unordered pair lies in exactly one block, that block counts equal `v(v-1)/6`, that the replication
number is uniformly `(v-1)/2`, and that every inadmissible `v` genuinely fails the divisibility
conditions.

**⛔ SCOPE, STATED PRECISELY.** This re-derives the MATHEMATICS independently over a finite range.
It does **not** verify the Lean proof and it does **not** establish the universal claim — the Lean
files do that for all `v`. This is the independent corroboration a reviewer can execute; the Lean is
the universal argument. **Both are needed and they are different artifacts.**

**The verifier caught a real bug in its own first draft.** The initial reconstruction wrote the
Skolem infinity blocks as `{∞, (i,k), (i+n,k+1)}` instead of `{∞, (i+n,k), (i,k+1)}` — the two roles
swapped. That duplicated exactly `3n` pairs against the diagonal blocks and orphaned exactly `3n`
others, failing every Skolem order while Bose passed 17/17. **An independent re-derivation that
cannot fail is not a verifier.** This one failed, localised the defect to a specific block family,
and passed only after the construction was corrected.

## What is closed

| arm | theorem | scope | axioms |
|---|---|---|---|
| Necessity | `sts_necessary_residues` + `lift_necessary.py` | **all v** | exhaustive residue proof |
| Sufficiency, v ≡ 3 (mod 6) | `bose_pair_covered`, `bose_pair_unique` | **all odd m** | `[propext, Classical.choice, Quot.sound]` |
| Sufficiency, v ≡ 1 (mod 6) | `skolem_pair_covered`, `skolem_pair_unique` | **all n > 0** | `[propext, Classical.choice, Quot.sound]` |

No `sorryAx`. No custom axiom. The Skolem algebra files (`MathBrainV2Skolem.lean`) are constructive —
`[propext, Quot.sound]`, not even `Classical.choice`.

**Uniqueness is the point.** Coverage alone gives a covering design; "exactly one block through every
pair" is what makes it a Steiner system. Both arms have coverage *and* uniqueness.

## What is NOT established

- **PRIOR ART — EDMONDS' ISABELLE LIBRARY READ IN FULL 2026-07-26. IT DOES NOT ANTICIPATE THIS.**
  Edmonds & Paulson, *A Modular First Formalisation of Combinatorial Design Theory* (CICM 2021) +
  AFP entry `Design_Theory` + Edmonds' Cambridge thesis (156pp, read directly, not from abstracts).
  What their library actually contains about Steiner systems, quoted:

  > "a locale was declared for **Steiner systems** (t-designs where λt = 1). A simple lemma proves
  > all Steiner systems have a multiplicity of 1. Hence, the `steiner_system` locale is a sublocale
  > of the `simple_design` locale." (thesis p40)

  **That is the entire Steiner content: a DEFINITION and one trivial lemma.** No existence theorem,
  no construction, no classification.

  | term | occurrences in the 156-page thesis |
  |---|---|
  | Skolem | **0** |
  | quasigroup | **0** |
  | idempotent | **0** |
  | Bose | 12 — **all "Bose's INEQUALITY"** (b ≥ v+r−1 iff r ≥ k+λ), a BIBD counting bound |

  **TWO TRAPS THAT NEARLY PRODUCED A FALSE RETRACTION HERE:**
  1. **"Bose's inequality" is NOT "the Bose construction."** Same surname, unrelated results. A
     keyword-matching novelty check reads this as a collision. It is not one.
  2. The sentence search engines surface — *"the existence of Steiner systems, solving an early
     design theoretic problem, relies on hypergraph representations"* — is Edmonds **CITING
     KEEVASH'S PAPER PROOF as background motivation** (thesis p21). Keevash's theorem is **not
     formalized** in that library. The snippet describes related work, not a contribution.

  **Conclusion: the complete v ≡ 1,3 (mod 6) classification with both arms constructive and
  pair-uniqueness proved is NOT present in Isabelle/AFP.** Residual risk that keeps this UNKNOWN
  rather than CLEARED: Coq and other systems unchecked; Edmonds' later hypergraph/Lovász-Local-Lemma
  work unchecked; and **the underlying mathematics is classical** (Kirkman 1847, Bose 1939,
  Skolem 1958) — any novelty here is in the FORMALIZATION, never in the theorem.

- **⛔ PRIOR ART RESOLVED 2026-07-26 — DESIGN THEORY IN LEAN 4 ALREADY EXISTS.**
  Wang & Üsküplü, *"Formalizing the Bruck-Ryser-Chowla Theorem: Combinatorial Design Theory in
  Lean"*, **ITP 2026**, DOI `10.4230/lipics.itp.2026.19`. Same prover, same field, same year.
  Read in full. What they formalized:

  | they proved | kind |
  |---|---|
  | Bruck-Ryser-Chowla (necessary conditions for a symmetric BIBD) — first in ANY proof assistant | **non-existence** |
  | Fisher's inequality — first in Lean | **non-existence** |
  | Kramer-Mesner theorem — first in ANY proof assistant | counting |
  | Witt cancellation, matrix congruence, block matrices; extensions to Mathlib linear algebra | infrastructure |

  **Every headline result is a NECESSARY CONDITION — an obstruction saying when a design CANNOT
  exist. There is no existence result, no construction, no Bose, no Skolem, no quasigroup, no
  sufficiency anywhere in it.** Our work is the opposite direction: constructive existence, both
  arms, universal, with uniqueness. **NOT ANTICIPATED — the two are complementary, not overlapping.**

  **BUT TWO PREMISES OF THIS FINDING ARE NOW DEAD, AND MUST NOT BE REPEATED:**
  1. *"Mathlib contains no design theory"* — **RETIRED.** It does now, and it is at ITP 2026.
     Anyone who says otherwise is quoting a stale note.
  2. *"This is not a wrapper over an existing formalization"* — still true, but the burden has
     moved: a reviewer will ask how our block-design definitions relate to theirs. **Check for
     definitional collision with their BIBD infrastructure before upstreaming anything.**

  These authors are the natural upstream contact, the likeliest people to formalize STS existence
  next, and the first name any reviewer will raise. **Retrieved only after the query-generator fix
  — both earlier novelty runs missed it entirely.**

- **`noveltyforge` RAN 2026-07-26 AND REFUSED TO CERTIFY.**
  `terminal_mode: NOVELTY_INADMISSIBLE_NOT_A_DISCOVERY`. The band said `NOVEL` (core 0.7948) but the
  band is **not usable**: the auto-acquired corpus (n=40) retrieved Steiner *tree* papers (VLSI
  routing) and accounting/economics papers matching on "necessity and sufficiency" — and did not
  retrieve the Edmonds/Paulson formalization at all. A high novelty score over an irrelevant corpus
  measures retrieval failure, not novelty. Two blocking gates:
  `missing_critical_date_temporal_gate` and
  `patent_axis_not_live: zero_official_claim_grounded_patents`. The second is expected — pure
  mathematics is not patentable subject matter, so `novelty_target: both` was the wrong setting;
  this is a `paper` claim. Verdict: `oracle/voice/steiner-novelty-verdict.json`,
  receipt `b8f021d1e99eb90f454f99d57fe06f6be405f4f78e9bf3bdbf2529aeee7cc4e5`.
  **Prior art remains UNKNOWN, not cleared. Do not describe this as novel. Do not file.**
- No standalone verifier exists yet (stage 2 of the invention ratchet). Until a stranger can re-check
  this without the repo, it is not bankable.
- This says nothing about the Erdős–Selfridge odd covering problem, which remains **open**. See
  `erdos-odd-covering-siege-2026-07-24.md`.

## Why this was buried

The siege log it came from is titled for the odd covering problem. That problem is open; this result
is closed. Filing a closed theorem under an open problem's name makes it invisible to anyone searching
for it — including the machine. This is the concrete instance that motivated per-claim typing across
the ledger (2026-07-26).
