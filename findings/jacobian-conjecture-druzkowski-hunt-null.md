---
id: jacobian-conjecture-druzkowski-hunt-null
claim: |-
  Jacobian Conjecture: bounded Druzkowski hunt finds 0 counterexamples; 1117 constant-Jacobian maps all verified invertible
status: open
tier: bronze
reality_score: 0.3
domain: algebra
effect: |-
  Deterministic 0-dollar zero-LLM counterexample-hunt over the Druzkowski normal form F=X+(AX)^o3 (equivalent to full JC by Bass-Connell-Wright + Druzkowski), exact over Q (char 0 -- statement firewall: JC is FALSE in char p). Coverage, no silent caps: n=2 full (entries -2..2, 625 maps); n=3 full (entries -1..1, 19683 maps); n=4 strict-upper-triangular family complete (729); n=5 strict-upper-triangular partial (58/59049, time-capped). Result: 1117 maps had a constant nonzero Jacobian (genuine JC instances) and ALL 1117 were verified invertible by A17 Groebner elimination with the explicit inverse constructed for each; 0 counterexamples. This CONFIRMS JC on the swept slice (find-first, re-deriving known low-dimension truth) and is consistent with JC being true. It is NOT a proof and NOT a disproof -- JC remains OPEN. Any counterexample a future run reports is a SUSPECTED BUG to independently re-kill, never announced.
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/kbk/engine/jacobian_conjecture_hunt.py
  - oracle/evidence/jacobian-conjecture-hunt-receipt.json
blades: |-
  T-ENGINE-jacobian-conjecture-hunt, T-ENGINE-A17-groebner
open_threads:
  - {blade: T-ENGINE-jacobian-conjecture-hunt, value: low, data: in-hand, cost: med, why: "extend coverage to higher n via structured nilpotent Druzkowski families as a regression harness only -- JC believed true, null-yield by design"}
provenance: |-
  Oracle KBK engine, 0-dollar deterministic zero-LLM; blade self-tested (jacobian_conjecture_hunt.py --selftest green: inverts a known automorphism, rejects a known non-invertible map). Run 2026-07-24.
domain_lane: math
domain_lane_source: domain-exact
---

# Jacobian Conjecture: bounded Druzkowski hunt finds 0 counterexamples; 1117 constant-Jacobian maps all verified invertible

**Status: open** · tier `bronze` · reality_score 0.3 · domain algebra

**Effect / numbers.**

Deterministic 0-dollar zero-LLM counterexample-hunt over the Druzkowski normal form F=X+(AX)^o3 (equivalent to full JC by Bass-Connell-Wright + Druzkowski), exact over Q (char 0 -- statement firewall: JC is FALSE in char p). Coverage, no silent caps: n=2 full (entries -2..2, 625 maps); n=3 full (entries -1..1, 19683 maps); n=4 strict-upper-triangular family complete (729); n=5 strict-upper-triangular partial (58/59049, time-capped). Result: 1117 maps had a constant nonzero Jacobian (genuine JC instances) and ALL 1117 were verified invertible by A17 Groebner elimination with the explicit inverse constructed for each; 0 counterexamples. This CONFIRMS JC on the swept slice (find-first, re-deriving known low-dimension truth) and is consistent with JC being true. It is NOT a proof and NOT a disproof -- JC remains OPEN. Any counterexample a future run reports is a SUSPECTED BUG to independently re-kill, never announced.

**Receipts.**

- `oracle/kbk/engine/jacobian_conjecture_hunt.py`
- `oracle/evidence/jacobian-conjecture-hunt-receipt.json`

**Blades.**

T-ENGINE-jacobian-conjecture-hunt, T-ENGINE-A17-groebner

**Open threads (next blades).**

- **T-ENGINE-jacobian-conjecture-hunt** (value low · data in-hand · cost med) — extend coverage to higher n via structured nilpotent Druzkowski families as a regression harness only -- JC believed true, null-yield by design

**Provenance.**

Oracle KBK engine, 0-dollar deterministic zero-LLM; blade self-tested (jacobian_conjecture_hunt.py --selftest green: inverts a known automorphism, rejects a known non-invertible map). Run 2026-07-24.


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
