---
id: oracle-algebraic-existence-engine
claim: |-
  KILLER INFRA: self-validating multi-engine algebraic-existence engine + exact-certificate bridge + cross-engine agreement
status: validated-observational
tier: silver
reality_score: 0.7
domain: math-infra
effect: |-
  2026-07-24 harden+bank+strengthen phase, COMPLETE for the safe pieces. oracle/kbk/engine/existence_engine.py: a general, reusable algebraic-existence decider -- 'does this parametrized polynomial family contain a member with property P?' -- underlying JC counterexample hunts, SRG existence, design existence. FULL SELFTEST GREEN across five capabilities: (1) sympy builds the constraint ideal; (2) Singular (WSL, GF p) fast Krull-dim + nonzero-scalar seed, SELF-VALIDATED (a fixed ideal's dim must match); (3) HomotopyContinuation.jl (WSL) numerical irreducible decomposition of incidence varieties Groebner can't compute, SELF-VALIDATED (nid(xy)=2); (4) EXACT-CERTIFICATE BRIDGE: HC.jl numerical solve -> rational (continued-fraction) + algebraic (nsimplify) reconstruction -> EXACT re-verification in sympy (validated recovering 1/2,1/3 and sqrt(2)); a float is never a proof -- numerics propose, exact certifies. (5) CROSS-ENGINE AGREEMENT: Singular and HC.jl must independently CONCUR on nonempty/empty; verdict WITHHELD on any disagreement or untrusted engine (two-checker anti-facade). Every verdict carries a trusted flag from a self-check, so a silent tool failure returning 'empty' can never masquerade as a proof of nonexistence -- the program's core facade risk, now structural. HARDENING: oracle/kbk/engine/setup_engines.sh reproducibly stands up Singular + Julia 1.10.5 + HomotopyContinuation.jl, version-pinned. REMAINING (deferred, not lost): dispatch-wiring into the KBK autonomous loop + technique-registry registration -- both DEFERRED because the registry/KBK tree is under concurrent mutation by another process (98->125 techniques mid-session); wiring into a moving tree corrupts it. Do these once it settles.
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/kbk/engine/existence_engine.py
  - oracle/kbk/engine/setup_engines.sh
  - oracle/kbk/engine/mold_triage.py
  - oracle/kbk/engine/jacobian_deformation_hunter.py
blades: |-
  T-ENGINE-jacobian-deformation-hunter, T-ENGINE-mold-triage-singular
open_threads: []
provenance: |-
  Cash session 2026-07-24: built + self-validated exact-certificate bridge and cross-engine agreement; full engine selftest green.
domain_lane: math
domain_lane_source: domain-exact
---

# KILLER INFRA: self-validating multi-engine algebraic-existence engine + exact-certificate bridge + cross-engine agreement

**Status: validated-observational** · tier `silver` · reality_score 0.7 · domain math-infra

**Effect / numbers.**

2026-07-24 harden+bank+strengthen phase, COMPLETE for the safe pieces. oracle/kbk/engine/existence_engine.py: a general, reusable algebraic-existence decider -- 'does this parametrized polynomial family contain a member with property P?' -- underlying JC counterexample hunts, SRG existence, design existence. FULL SELFTEST GREEN across five capabilities: (1) sympy builds the constraint ideal; (2) Singular (WSL, GF p) fast Krull-dim + nonzero-scalar seed, SELF-VALIDATED (a fixed ideal's dim must match); (3) HomotopyContinuation.jl (WSL) numerical irreducible decomposition of incidence varieties Groebner can't compute, SELF-VALIDATED (nid(xy)=2); (4) EXACT-CERTIFICATE BRIDGE: HC.jl numerical solve -> rational (continued-fraction) + algebraic (nsimplify) reconstruction -> EXACT re-verification in sympy (validated recovering 1/2,1/3 and sqrt(2)); a float is never a proof -- numerics propose, exact certifies. (5) CROSS-ENGINE AGREEMENT: Singular and HC.jl must independently CONCUR on nonempty/empty; verdict WITHHELD on any disagreement or untrusted engine (two-checker anti-facade). Every verdict carries a trusted flag from a self-check, so a silent tool failure returning 'empty' can never masquerade as a proof of nonexistence -- the program's core facade risk, now structural. HARDENING: oracle/kbk/engine/setup_engines.sh reproducibly stands up Singular + Julia 1.10.5 + HomotopyContinuation.jl, version-pinned. REMAINING (deferred, not lost): dispatch-wiring into the KBK autonomous loop + technique-registry registration -- both DEFERRED because the registry/KBK tree is under concurrent mutation by another process (98->125 techniques mid-session); wiring into a moving tree corrupts it. Do these once it settles.

**Receipts.**

- `oracle/kbk/engine/existence_engine.py`
- `oracle/kbk/engine/setup_engines.sh`
- `oracle/kbk/engine/mold_triage.py`
- `oracle/kbk/engine/jacobian_deformation_hunter.py`

**Blades.**

T-ENGINE-jacobian-deformation-hunter, T-ENGINE-mold-triage-singular

**Provenance.**

Cash session 2026-07-24: built + self-validated exact-certificate bridge and cross-engine agreement; full engine selftest green.


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
