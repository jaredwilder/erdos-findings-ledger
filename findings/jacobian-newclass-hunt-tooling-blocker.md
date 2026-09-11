---
id: jacobian-newclass-hunt-tooling-blocker
claim: |-
  JC new-class hunt: full 3-tier engine built (sympy->Singular->HomotopyContinuation.jl); first mold (1,-1,-3) DECIDED empty
status: open
tier: gold
reality_score: 0.7
domain: algebra
effect: |-
  2026-07-24: the seed-search + incidence tooling is fully stood up and validated end-to-end. THREE-TIER ENGINE: (1) sympy builds the constant-Jacobian constraint ideal (det of Jacobian + coefficient extraction) [oracle/kbk/engine/mold_triage.py]; (2) Singular 4.2.1 (WSL) does fast finite-field Groebner/dim/saturation triage -- decides 80-constraint systems in seconds that hung sympy on Q and GF(p); (3) HomotopyContinuation.jl (Julia 1.10.5, WSL) does the GENERAL collision-incidence variety via numerical irreducible decomposition (nid) -- the object Singular's symbolic Groebner/saturation could NOT compute (killed at 40min). RESULT: the (1,-1,-3) weight-system mold is DECIDED EMPTY (no constant-nonzero-Jacobian map with a genuine a!=b collision => no counterexample class in it). Evidence, all self-validated: charts 1,2 empty (Singular); chart 3 empty (HC.jl, which Singular could not finish); general incidence empty under TWO independent lambda(a-b)=1 normalizations (HC.jl nid), with a nid self-check (ncomponents(xy)=2) proving the tool detects nonempty varieties so the 0 is real. CAVEATS: lambda-generic (two normalizations, not a formal all-directions proof); nid is numerical (self-check bounds but doesn't eliminate risk). NEW CLASS: still not found -- this mold is empty; the class, if it exists in this framework, is in a DIFFERENT mold. NEXT (protocol phase 2): ranked sweep of rank-two-invariant molds (u,v independent), each now decidable by this engine. TODO: bake mold_triage.py + the HC.jl incidence pipeline as permanent registered blades (currently mold_triage.py on disk; HC scripts in scratchpad).
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/kbk/engine/mold_triage.py
blades: |-
  T-ENGINE-mold-triage-singular, T-ENGINE-jacobian-deformation-hunter
open_threads: []
provenance: |-
  Cash session 2026-07-24: Singular + Julia/HomotopyContinuation.jl stood up in WSL, full incidence pipeline validated (nid self-check), (1,-1,-3) decided empty across charts + general incidence x2 lambda.
domain_lane: math
domain_lane_source: domain-exact
---

# JC new-class hunt: full 3-tier engine built (sympy->Singular->HomotopyContinuation.jl); first mold (1,-1,-3) DECIDED empty

**Status: open** · tier `gold` · reality_score 0.7 · domain algebra

**Effect / numbers.**

2026-07-24: the seed-search + incidence tooling is fully stood up and validated end-to-end. THREE-TIER ENGINE: (1) sympy builds the constant-Jacobian constraint ideal (det of Jacobian + coefficient extraction) [oracle/kbk/engine/mold_triage.py]; (2) Singular 4.2.1 (WSL) does fast finite-field Groebner/dim/saturation triage -- decides 80-constraint systems in seconds that hung sympy on Q and GF(p); (3) HomotopyContinuation.jl (Julia 1.10.5, WSL) does the GENERAL collision-incidence variety via numerical irreducible decomposition (nid) -- the object Singular's symbolic Groebner/saturation could NOT compute (killed at 40min). RESULT: the (1,-1,-3) weight-system mold is DECIDED EMPTY (no constant-nonzero-Jacobian map with a genuine a!=b collision => no counterexample class in it). Evidence, all self-validated: charts 1,2 empty (Singular); chart 3 empty (HC.jl, which Singular could not finish); general incidence empty under TWO independent lambda(a-b)=1 normalizations (HC.jl nid), with a nid self-check (ncomponents(xy)=2) proving the tool detects nonempty varieties so the 0 is real. CAVEATS: lambda-generic (two normalizations, not a formal all-directions proof); nid is numerical (self-check bounds but doesn't eliminate risk). NEW CLASS: still not found -- this mold is empty; the class, if it exists in this framework, is in a DIFFERENT mold. NEXT (protocol phase 2): ranked sweep of rank-two-invariant molds (u,v independent), each now decidable by this engine. TODO: bake mold_triage.py + the HC.jl incidence pipeline as permanent registered blades (currently mold_triage.py on disk; HC scripts in scratchpad).

**Receipts.**

- `oracle/kbk/engine/mold_triage.py`

**Blades.**

T-ENGINE-mold-triage-singular, T-ENGINE-jacobian-deformation-hunter

**Provenance.**

Cash session 2026-07-24: Singular + Julia/HomotopyContinuation.jl stood up in WSL, full incidence pipeline validated (nid self-check), (1,-1,-3) decided empty across charts + general incidence x2 lambda.


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
