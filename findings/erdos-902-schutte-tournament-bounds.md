---
id: erdos-902-schutte-tournament-bounds
claim: |-
  Erdos #902 (Schutte): f(1)=3 and f(2)=7 re-derived by exact SAT; f(3)<=19 and f(4)<=67 by certified Paley witnesses; no lower bound moved
status: open
tier: bronze
reality_score: 0.62
effect: |-
  SAT arm re-derived f(1)=3 and f(2)=7 in both polarities (N=2,N=6 UNSAT; N=3,N=7 SAT, witnesses re-verified against the definition). Paley family arm: smallest q with S_4 is 67 => f(4)<=67, calibrated on q=3/S_1, q=7/S_2, q=19/S_3 (the Szekeres extremal example) with negative controls q=11,q=7 at n=3. UPPER BOUNDS ONLY - no lower bound moved. SAT arm did NOT close n=3 at N=19/N=18 in a 25-min budget; named obstruction is unbroken N! vertex-relabelling symmetry. Prior art NOT cleared: nearest mechanism collision 10.4153/cmb-1971-007-1.
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/ledger/statement-firewall-receipts/ERDOS-902-1d2c8ff3d5c96f8985274225598f0a33.json
open_threads: []
provenance: |-
  (not provided)
---

# Erdos #902 (Schutte): f(1)=3 and f(2)=7 re-derived by exact SAT; f(3)<=19 and f(4)<=67 by certified Paley witnesses; no lower bound moved

**Status: open** · tier `bronze` · reality_score 0.62

**Effect / numbers.**

SAT arm re-derived f(1)=3 and f(2)=7 in both polarities (N=2,N=6 UNSAT; N=3,N=7 SAT, witnesses re-verified against the definition). Paley family arm: smallest q with S_4 is 67 => f(4)<=67, calibrated on q=3/S_1, q=7/S_2, q=19/S_3 (the Szekeres extremal example) with negative controls q=11,q=7 at n=3. UPPER BOUNDS ONLY - no lower bound moved. SAT arm did NOT close n=3 at N=19/N=18 in a 25-min budget; named obstruction is unbroken N! vertex-relabelling symmetry. Prior art NOT cleared: nearest mechanism collision 10.4153/cmb-1971-007-1.

**Receipts.**

- `oracle/ledger/statement-firewall-receipts/ERDOS-902-1d2c8ff3d5c96f8985274225598f0a33.json`


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
