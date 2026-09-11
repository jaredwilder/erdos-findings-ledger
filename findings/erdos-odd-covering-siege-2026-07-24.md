---
id: erdos-odd-covering-siege-2026-07-24
claim: |-
  Erdos-Selfridge odd covering problem: per-set refutations of the smallest density-clearing distinct-odd modulus sets; density >= 1 necessary but NOT sufficient (certified per-set impossibility). Problem itself OPEN.
status: open
tier: gold
reality_score: 0.8
domain: math
# --- OEC DECLARATIONS (2026-07-26) ---
# SCOPE IS 'instance': these are PER-SET decisions over a finite space. They do not
# touch the infinite problem, which stays open.
artifact_kind: enumeration
truth_mode: certified
scope_grade: instance
inference: deductive
independence: independently_reverified   # CP-SAT and PySAT agree; witnesses re-checked separately
reproducibility: artifact_verified
novelty: unchecked
claim_ir:
  claim_id: "erdos_odd_covering:density_not_sufficient"
  assertion_kind: refutation
  display: "Density >= 1 is necessary but NOT sufficient: {3,5,7,9,11,13,15} clears the density wall and still admits no covering."
  scope:
    domain: number_theory
    label: "distinct odd modulus multisets, L <= 45045"
  statement:
    op: necessary_but_not_sufficient
    args:
      - {op: const, args: ["density_at_least_one", "condition"]}
      - {op: const, args: ["distinct_odd_covering_system", "target"]}
  definitions:
    proof_level: "independently_cross_checked, not certificate-level; DRAT is the promotion path"
  tags: [erdos, covering_systems, sat, open]
# --- PER-CLAIM TYPING (schema v2, 2026-07-26) ---
claims:
  - id: density_necessary
    statement: A covering system requires sum 1/n_i >= 1.
    inference: deductive
    closure: closed
    basis: re-derived by obstruction_discovery.discover() over verified data; a known necessary condition
    why: A proof, not a sample. Machine re-derived a published result.
  - id: dense_set_unsat
    statement: "{3,5,7,9,11,13,15} (density 1.022) admits no covering residue assignment."
    inference: deductive
    closure: closed
    basis: two independent complete solvers (CP-SAT + PySAT) agree UNSAT; L = 45045
    why: >-
      Exhaustive over the FINITE space L=45045 for THIS modulus set. Deductive but
      scoped: it settles one set, not the infinite problem. Proof level is
      independently_cross_checked, not certificate-level; DRAT logging is the promotion path.
  - id: density_not_sufficient
    statement: Density >= 1 is necessary but not sufficient for a distinct-odd covering.
    inference: deductive
    closure: closed
    basis: dense_set_unsat is a density-clearing set that still fails
    why: A single verified counterexample settles a sufficiency claim outright.
  - id: even_modulus_separator
    statement: A covering system must contain an even modulus (equivalently, smallest modulus = 2).
    inference: inductive
    closure: open
    basis: obstruction mining over positives (all even) and negatives
    why: >-
      LEAD, NOT A RESULT. Explicitly partly circular — every positive is even only
      because no odd cover is known. This IS the Erdos-Selfridge conjecture restated
      from data. No amount of further mining can close it; it needs a proof.
  - id: mus_signature
    statement: The minimal unsatisfiable core concentrates at extreme classes of primes dividing few moduli.
    inference: inductive
    closure: open
    basis: minimal 37-residue and 36-residue MUS on two modulus sets
    why: >-
      Corroborated on two sets. Two data points is a signature, not a theorem. The
      related rule "every prime divides >= 2 moduli" was REFUTED by a real cover
      ({2,3,4,5,6,8,12,24}) — which is why this one stays inductive.
effect: |-
  Per-set refutations of distinct-odd covering candidates by two independent complete solvers (CP-SAT + PySAT), with every SAT witness re-checked by a separate array-marking verifier. Ground-truth gate green on the known cover {2,3,4,6,12}. The smallest natural distinct-odd set clearing the density wall, {3,5,7,9,11,13,15} (density 1.022, L=45045), is UNSAT — so density >= 1 is necessary but NOT sufficient. Unsat-core mining extracts minimal 37- and 36-residue MUSes; the non-circular structural signature is concentration at extreme classes (0, p-1) of primes dividing few moduli. The "must contain an even modulus" separator is a data-driven restatement of the open conjecture and is explicitly NOT a proof. Per-set UNSATs are finite-computational and do not resolve the infinite problem.
inputs: |-
  $0, deterministic, zero-LLM. OR-tools CP-SAT + PySAT (Cadical/Glucose). No network, no data acquisition.
cohort: |-
  Distinct odd modulus multisets > 1; L up to 45045. Finite per-set decisions only.
receipts:
  - oracle/scripts/frontier_math_printer/covering_system_attack.py
  - oracle/runtime/state/frontier-math-covering-odd-siege.json
  - oracle/runtime/state/frontier-math-covering-campaign.json
  - oracle/scripts/frontier_math_printer/campaign_director.py
open_threads:
  - {blade: drat-proof-logging, value: high, data: in-hand, cost: med, why: "Promote per-set UNSATs from independently_cross_checked to certificate-level with a DRAT proof log."}
  - {blade: family-level-obstruction, value: high, data: in-hand, cost: high, why: "Lift per-set UNSAT to a family-level obstruction. The strategic move after a non-binding-density UNSAT is obstruction-lifting, NOT a bigger set at CP-SAT (L explodes 45045 -> 765765 -> 14.5M)."}
  - {blade: noncircular-separator, value: high, data: in-hand, cost: high, why: "Mine prime-local/LP invariants from unsat-cores for a separator sharper than density that does not presuppose the conjecture."}
provenance: |-
  Campaign-Director siege, opened 2026-07-24. The Steiner triple system results produced by the same
  campaign_brain.py engine were SPLIT OUT on 2026-07-26 to
  sts-classification-lean-both-arms-2026-07-24.md — they are closed, this problem is not.
domain_lane: math
domain_lane_source: domain-exact
---

# Erdős odd covering problem — siege log (opened 2026-07-24)

**Problem (Erdős–Selfridge; Guy, *Unsolved Problems in Number Theory* B21; OPEN):**
Does a covering system of ℤ exist whose moduli are all **distinct, odd, and > 1**?
A covering system is a finite set of congruences x ≡ aᵢ (mod nᵢ) such that every integer satisfies at
least one. Classic covers exist (e.g. moduli {2,3,4,6,12}) but use even moduli; whether an all-odd one
exists is unknown. Conjectured answer: no such system exists.

This is the first target of the **Campaign-Director siege** — the strategic layer being forged, by hand,
one round at a time, against a real open problem (not designed top-down).

## Organ

`oracle/scripts/frontier_math_printer/covering_system_attack.py` — for a FIXED odd modulus multiset,
decide whether some residue assignment covers ℤ/Lℤ (L = lcm):
- **CONSTRUCT/REFUTE**, two independent complete solvers: OR-tools **CP-SAT** (lazy clause generation) +
  **PySAT** (CDCL, Cadical/Glucose). An UNSAT is trusted only when both agree. Every SAT witness is
  re-checked by a separate array-marking verifier (different code path).
- **Obstruction mining** reuses the real `obstruction_discovery.discover()` (the organ that re-derived
  Bruck-Ryser) with a covering-system invariant library over modulus multisets.
- Receipt: `oracle/runtime/state/frontier-math-covering-odd-siege.json`. RSI: `ratchet-cross-run-ledger.json`.

## Round 1–2 receipts

Ground-truth gate GREEN: known cover {2,3,4,6,12} → SAT + witness verified; density-starved {2,3}, {2,4,8} → UNSAT.

| modulus set | density | L | verdict | proof level |
|---|---|---|---|---|
| {3,5,7,9,11,13} | 0.955 | 45045 | UNSAT | N-wall (density < 1) |
| **{3,5,7,9,11,13,15}** | **1.022** | 45045 | **UNSAT** | **two independent complete solvers (CP-SAT + PySAT)** |

**Result:** the smallest natural distinct-odd set that *clears* the density wall still provably fails.
Density ≥ 1 is necessary but **not sufficient** — a certified per-set impossibility.

## Obstruction mining (`discover()` over verified data)

- Positives = machine-verified covers (all EVEN, since no odd cover is known).
- Negatives = machine-verified non-covers (density-starved + the dense-but-failing {3,5,7,9,11,13,15}).
- **Re-derived, PROVEN:** *density Σ1/nᵢ ≥ 1* — the machine surfaces the known necessary condition from data.
- **Reconstructed, NOVEL-from-data (a lead, unproven):** *a covering must contain an even modulus* /
  *smallest modulus = 2* — this **is the Erdős–Selfridge conjecture**, and it is the only separator that
  kills the dense-failing {3,5,7,9,11,13,15}. Locating it says: the missing wall is this (conjectural) law.

## Honest boundary

- Per-set UNSATs are **finite-computational**, not a resolution of the infinite problem.
- The "contains an even modulus" separator is **partly circular** (positives are all even because no odd
  cover is known) — a data-driven restatement of the open conjecture, not a proof. `discover()`'s own
  doctrine: small negative-sets admit many separators; a NOVEL-from-data label is a lead.
- Proof level of the UNSATs is `independently_cross_checked` (two complete solvers agree), **not**
  certificate-level — a DRAT proof-log is the promotion path.

## Unsat-core mining — obstruction localized (round 3, 2026-07-24)

`unsat_core()` (PySAT selector-guarded coverage clauses + `get_core` + deletion-MUS) extracts the MINIMAL
set of residues no assignment can jointly cover:
- {3,5,7,9,11,13,15} → minimal **37-residue** MUS; {3,5,7,9,11,13,21} → minimal 36-residue MUS (both verified minimal, out of L=45045).
- **Non-circular structural signature:** the MUS concentrates at the extreme classes (0, p−1) of primes that
  divide FEW moduli. Corroborated on both sets — a prime in 1 modulus carries a sharp bimodal concentration
  that DISSOLVES when it divides ≥2 (7: class-0 count 11→5 as it went 1→2 moduli; 5: →18 as it went 2→1).
- **Tempting rule REFUTED, honestly:** "every prime divides ≥2 moduli" is FALSE — {2,3,4,5,6,8,12,24} is a
  verified cover with prime 5 in one modulus; `discover()` correctly rejected the candidate (it excludes a real cover).
- **Conclusion:** the sharper obstruction is the INTERACTION of density-minimality (no coverage slack) ×
  prime under-representation — not a standalone prime-count rule. That interaction is the next testable-predicate target.

## Campaign Director — the strategic loop, forged (2026-07-24)

`oracle/scripts/frontier_math_printer/campaign_director.py` runs the siege as a multi-round campaign that
rebuilds its attack map from receipts, and REPRODUCES this session's by-hand loop automatically:
firewall → attack (both dense odd sets REFUTED) → **stall-detect** (density non-binding → pivot, don't
escalate compute) → mine (MUS + prime-representation fingerprint) → hypothesize (representation family) →
**test-refute** (`discover()` killed `every prime ≥2/≥3 moduli`; density survived) → maturity
EMPIRICALLY-CONSTRAINED + RSI (`campaign-director` family). Receipt:
`oracle/runtime/state/frontier-math-covering-campaign.json`. One instantiation (covering); the stage
sequence is the general Director template — generalized when a second siege forces the target interface.

## Math Brain — false green caught & fixed (2026-07-24, /goal BUILD IT ALL)

`oracle/scripts/frontier_math_printer/campaign_brain.py` — the full loop: **angle-generator** (diverse angles,
sharpened by receipts) + **RSI-ordered multi-round loop** (angles ordered by info-gain) + **two-wall
convergence** + **8-dim state vector**. Proven on two problem shapes: **covering** (single-existence → converges
"loop dry", honest OPEN gap) and **Steiner S(2,3,v)** (classification). **A pasted critique caught a FALSE
GREEN:** the Steiner "walls MET / rediscovered Kirkman" was finite-frontier (v=3..19) FITTING — not a theorem.
**Fixed:** a finite separator can never set `wallsMeet`; built `lift_necessary.py`, which PROVES the necessary
condition **v ≡ 1,3 mod 6 for all v** (exhaustive residue proof) — a general t-design engine that find-first
re-derives S(2,4,v)≡1,4 mod12 and S(2,5,v)≡1,5 mod20 too. Steiner is now honestly **NECESSARY-PROVEN (all v) +
SUFFICIENCY-PARTIAL: infinite families constructively PROVEN (verified doubling template, order≤127) — NOT a full classification**. Registered `T-BRAIN-existence-campaign`, lane
`STEINER-2-3-V-EXISTENCE`; validator + cockpit sync green. **V2 roadmap (staged, external-tool-gated):**
certificate→lemma (Craig interpolation), ProblemIR + e-graph (egglog), theory-populations + disagreement
experiments, cvc5 CEGIS, the sufficient construction-synthesis arm, blind-recovery R0–R6; current rung ≈ R2–R3.

## ⛔ MOVED 2026-07-26 — the Steiner triple system result now has its own finding

The STS classification work formerly recorded below (Bose exactness, the Skolem arm, and the
final both-arms axiom audit) was **split out to
`oracle/ledger/findings/sts-classification-lean-both-arms-2026-07-24.md`**.

Reason: it is **closed** — both residue arms kernel-certified in Lean, universal, clean axiom
footprint, no `sorryAx` — and it was filed inside a siege log named for a **different and still-open
problem**. A closed theorem under an open problem's name is unfindable by anyone searching for it.
The mathematics is unchanged and still dated 2026-07-24; only its filing moved.

**The odd covering problem below remains OPEN.** Nothing in the STS result bears on it.

The sections that follow are retained only as the campaign narrative that produced the STS work
(`campaign_brain.py` was proven on two problem shapes: covering and Steiner). **Cite the STS finding,
not this log, for any Steiner claim.**

---

## ★ BOSE EXACTNESS PROVEN IN LEAN (2026-07-24) — the v≡3 (mod 6) arm is closed
<!-- CANONICAL RECORD: sts-classification-lean-both-arms-2026-07-24.md — narrative retained here -->


`oracle/math/EG411Formal/EG411Formal/MathBrainV2BoseUnique.lean` — **`bose_pair_unique`**: for every odd
`m` and every pair of distinct points of `ZMod m × Fin 3`, the Bose construction contains **exactly one**
block through that pair. Existence was already proven (`bose_pair_covered`); this adds **uniqueness**, which
is the "exactly once" property that separates a **Steiner system** from a mere covering.

Supporting theorems, all universal in odd `m`: `mem_verticalBlock`, `verticalBlock_ne_diagonalBlock`,
`diagonal_same_layer`, `bose_unique_vertical`, `bose_unique_diagonal`. The mixed case (different first
coordinate **and** different layer) is discharged by a normal-form lemma using `boseOp_eq_iff` to pin the
remaining base point uniquely.

**Kernel audit (the certificate that matters):**
```
#print axioms MathBrainV2.bose_pair_unique
  -> depends on axioms: [propext, Classical.choice, Quot.sound]
```
The three standard Lean axioms only — **no `sorryAx`**, no custom axiom. A `sorry` anywhere in the
dependency chain would surface as `sorryAx` in that list; it does not appear.

**What this does and does NOT establish.** It closes the sufficiency arm for **v ≡ 3 (mod 6)** exactly and
universally. It does **NOT** prove the classification: the **Skolem arm (v ≡ 1 mod 6) is not formalized**, so
`sts-classification` remains OPEN in the proof frontier and the machine still reports
`NECESSARY-PROVEN + SUFFICIENCY-PARTIAL`. Wired into `external_tools.lean_certificate_smoke` (5 certs) and
the `v2_acceptance` proof frontier as node `bose-pair-uniqueness` (proven) alongside `skolem-pair-coverage`
(NOT proven). One real bug fixed in passing: the Lean smoke decoded subprocess output as cp1252 on Windows,
so any Unicode in a proof file (`≠`, `≡`, `ℤ`) crashed the reader thread and silently returned `stdout=None`
— now decoded as UTF-8.

## ★ SKOLEM ARM (v ≡ 1 mod 6) — algebra + complementarity PROVEN (2026-07-24)

Two new Lean files, both **constructive** (`axioms = [propext, Quot.sound]` — not even `Classical.choice`),
no `sorry`, no custom axiom:

**`MathBrainV2Skolem.lean`** — the half-idempotent commutative quasigroup on `Z_{2n}`, universal in `n>0`.
Formalization trick that made it tractable: define the halving map by its **inverse** (`skolemUnhalve`:
`g u = 2u` for `u<n`, `2(u-n)+1` for `u≥n`), whose branches are exactly the evens and odds of `[0,2n)`.
Both maps explicit and computable, proved mutually inverse — so all parity case-analysis is confined to two
lemmas and never leaks upward. Theorems: `skolemHalve_unhalve`, `skolemUnhalve_halve`, `skolemOp_eq_iff`,
`skolemOp_comm`, `skolemOp_solve`, `skolemOp_left_cancel`, `skolemOp_right_cancel`,
`skolemOp_half_idem_lt` (`q i i = i` for `i<n`), `skolemOp_half_idem_ge` (`q i i = i-n` for `i≥n`).

**`MathBrainV2SkolemBlocks.lean`** — the block design (`vertical` / `infinity` / `diagonal`, counts match
`n + 3n + 3·C(2n,2) = n(6n+1) = v(v-1)/6`) plus the structural lemmas, culminating in
**`diagonal_partner_or_inf`**: for distinct `x,y`, either the diagonal partner `w = g y - x` is legitimate
(`w ≠ x`), **or** `y.val < n ∧ x = y + n` — which is exactly the pair an infinity block covers. That is the
formal statement of **why half-idempotence forces the extra ∞ point**: the two block families are exactly
complementary, so coverage can never have a hole. Supporting: `add_self_eq_zero_iff` (doubling kills only
`0` and `n`), `val_add_self_even`, `skolemUnhalve_ne_add_self`, `skolemUnhalve_eq_add_self`.

**`skolem_pair_covered` — PROVEN (same session).** The full case assembly landed: ∞-pairs (via
`inf_pair_covered`, splitting on which half `y` sits in) · same-point/different-layer (vertical block below
the half-way point; a diagonal block whose apex is the point itself above it, legitimate precisely because
`g x ≠ x + x` there) · same-layer (direct diagonal) · **mixed** (the complementarity lemma decides diagonal
vs. infinity block). Axioms `[propext, Classical.choice, Quot.sound]`, no `sorryAx`.

**Both arms now have universal coverage**: `bose_pair_covered` (v ≡ 3) + `skolem_pair_covered` (v ≡ 1).

**`skolem_pair_unique` — PROVEN (same session). BOTH ARMS NOW EXACT.** The "exactly one block"
upgrade, by cases on the pair type, each showing any generated block containing the pair equals a
canonical one: **∞-pairs** (`skolem_inf_pair_unique` — only infinity blocks contain ∞; the val-constraint
`i.val < n` kills the wrong branch) · **same point / different layers** (`skolem_samepoint_unique` —
vertical below the halfway mark; above it the diagonal is forced and its partner `g x - x` is unique, with
the layer pinned by a decidable `Fin 3` lemma `layer_pair_det`) · **same layer** (`skolem_samelayer_unique`)
· **mixed** (`skolem_mixed_unique_aux` — the complementarity lemma proves the infinity route and the
diagonal route are *mutually exclusive*, so exactly one block covers). Assembled in `skolem_pair_unique`.

**Final audit — all four load-bearing theorems, universal, no `sorryAx`:**

| theorem | axioms |
|---|---|
| `bose_pair_covered` / `bose_pair_unique` | `[propext, Classical.choice, Quot.sound]` |
| `skolem_pair_covered` / `skolem_pair_unique` | `[propext, Classical.choice, Quot.sound]` |

Both residue families of the STS classification are kernel-certified: necessity universal
(`lift_necessary` + Lean `sts_necessary_residues`), sufficiency universal and **exact** (Bose for
v ≡ 3, Skolem for v ≡ 1). Lean smoke: **7 certificates**. Proof frontier: every `skolem-*` and `bose-*`
node now `proven=True`.

## Maturity state & next

State: EMPIRICALLY CONSTRAINED (real EXISTS/REFUTED data); full problem FRONTIER, side diagnosed =
**missing obstruction**. The stall that defines the Director: after a per-set UNSAT with non-binding
density, the strategic move is *obstruction-lifting*, not throwing a bigger set at CP-SAT (L explodes:
45045 → 765765 → 14.5M). Next: (1) enrich prime-local/LP invariants mined from CP-SAT unsat-cores for a
non-circular separator sharper than density; (2) lift per-set UNSAT to a family-level obstruction;
(3) DRAT proof-logging for certificate-level promotion.

Registry: lane `ERDOS-ODD-COVERING`, techniques `T-ODDCOV-construct-or-refute`,
`T-ODDCOV-obstruction-discovery` (`oracle/ledger/technique-registry.json`). **Wired into the canonical
loop (2026-07-24):** `covering_system_bridge.py` → `target_dispatch` (`oddcover:/covering-system:<moduli>`,
flagship routes REFUTED+trusted); method-technique-map A05; cockpit MATH room, sync-check green.
