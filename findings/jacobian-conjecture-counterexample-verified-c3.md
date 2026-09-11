---
id: jacobian-conjecture-counterexample-verified-c3
claim: |-
  Oracle-verified Jacobian Conjecture counterexample over C^3 (det -2, generically 3-to-1); essentially unique up to scaling; seed-search unblocked
status: validated-observational
tier: gold
reality_score: 0.9
domain: algebra
effect: |-
  Oracle independently VERIFIED (operator-provided; public Harvard/AI result) a counterexample to the Jacobian Conjecture as stated. F:C^3->C^3, F1=z(1+xy)^3+y^2(1+xy)(4+3xy), F2=y+3xz(1+xy)^2+3xy^2(4+3xy), F3=2x-3x^2y-x^3z. Receipts: det(JF)=-2 constant; three DISTINCT points (0,0,-1/4),(1,-3/2,13/2),(-1,3/2,13/2) map to (-1/4,0,0); generic fiber degree 3 => not injective. Torus-equivariant (x,y,z)->(tx,y/t,z/t^2), weights (-2,-1,+1). RIGIDITY (two machine-proven walls): (1) 17-param u=1+xy deg-3 deformation variety has tangent 6 = 4 scaling + 2 genuine, but genuine directions do NOT integrate off-orbit (collapse to the point); (2) the z^2 deformation via invariant x^2z is forced to 0 => affine-in-z is mandatory. So the C^3 map is essentially UNIQUE up to scaling. UNBLOCK (2026-07-24): the seed-finding blocker (cold Groebner on 14-17 cubics, which hung) is DISSOLVED by the cofactor identity det(JF)=V(F_n) with V = generalized cross product of the first n-1 gradients -- this makes the LAST component LINEAR (solve V(F_n)=c), and F(a)=F(b) is linear in the coefficients, so seeds are MANUFACTURED by linear algebra + collision-first, not nonlinear elimination. Validated (Run A): recovered the known F3 exactly by a linear solve. Baked permanent into oracle/kbk/engine/jacobian_deformation_hunter.py (cofactor_field / complete_last_component / collision_shadow), selftest green. Next: C^4 rank-two-invariant (u=xy,v=zt) hunt via collision-first + last-component completion.
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts:
  - oracle/kbk/engine/jacobian_deformation_hunter.py
  - oracle/kbk/engine/jacobian_conjecture_hunt.py
blades: |-
  T-ENGINE-jacobian-deformation-hunter, T-ENGINE-jacobian-conjecture-hunt, T-ENGINE-A17-groebner
open_threads: []
provenance: |-
  Oracle deterministic verification (exact sympy over Q), Cash session 2026-07-24; counterexample provided by operator; cofactor-completion firepower from operator debrief, validated + baked.
domain_lane: math
domain_lane_source: domain-exact
---

# Oracle-verified Jacobian Conjecture counterexample over C^3 (det -2, generically 3-to-1); essentially unique up to scaling; seed-search unblocked

**Status: validated-observational** · tier `gold` · reality_score 0.9 · domain algebra

**Effect / numbers.**

Oracle independently VERIFIED (operator-provided; public Harvard/AI result) a counterexample to the Jacobian Conjecture as stated. F:C^3->C^3, F1=z(1+xy)^3+y^2(1+xy)(4+3xy), F2=y+3xz(1+xy)^2+3xy^2(4+3xy), F3=2x-3x^2y-x^3z. Receipts: det(JF)=-2 constant; three DISTINCT points (0,0,-1/4),(1,-3/2,13/2),(-1,3/2,13/2) map to (-1/4,0,0); generic fiber degree 3 => not injective. Torus-equivariant (x,y,z)->(tx,y/t,z/t^2), weights (-2,-1,+1). RIGIDITY (two machine-proven walls): (1) 17-param u=1+xy deg-3 deformation variety has tangent 6 = 4 scaling + 2 genuine, but genuine directions do NOT integrate off-orbit (collapse to the point); (2) the z^2 deformation via invariant x^2z is forced to 0 => affine-in-z is mandatory. So the C^3 map is essentially UNIQUE up to scaling. UNBLOCK (2026-07-24): the seed-finding blocker (cold Groebner on 14-17 cubics, which hung) is DISSOLVED by the cofactor identity det(JF)=V(F_n) with V = generalized cross product of the first n-1 gradients -- this makes the LAST component LINEAR (solve V(F_n)=c), and F(a)=F(b) is linear in the coefficients, so seeds are MANUFACTURED by linear algebra + collision-first, not nonlinear elimination. Validated (Run A): recovered the known F3 exactly by a linear solve. Baked permanent into oracle/kbk/engine/jacobian_deformation_hunter.py (cofactor_field / complete_last_component / collision_shadow), selftest green. Next: C^4 rank-two-invariant (u=xy,v=zt) hunt via collision-first + last-component completion.

**Receipts.**

- `oracle/kbk/engine/jacobian_deformation_hunter.py`
- `oracle/kbk/engine/jacobian_conjecture_hunt.py`

**Blades.**

T-ENGINE-jacobian-deformation-hunter, T-ENGINE-jacobian-conjecture-hunt, T-ENGINE-A17-groebner

**Provenance.**

Oracle deterministic verification (exact sympy over Q), Cash session 2026-07-24; counterexample provided by operator; cofactor-completion firepower from operator debrief, validated + baked.


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
