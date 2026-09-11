---
id: erdos710-autonomous-close-2026-09-03
title: Erdős #710 — first AUTONOMOUS certified close through the formalizer campaign
status: CERTIFIED (theorem, FULL_FORMALIZATION); parent problem OPEN
domain: number theory / formalization pipeline
updated: 2026-09-03
---

# The win

The autonomous close driver (gpt-5.6-luna, reasoning off), wired to the REAL frontier
formalizer campaign, produced a kernel-sealed, court-approved certified theorem WITHOUT a
human driving the campaign stages. $0.55, 271s, 16 rounds.

- Theorem: `e710_lower_bound_50` (+ _100, _125 in the same file) — a computed Hall-deficient
  index set has no injective transversal into its divisibility interval, hence f(n) > L at
  n in {50,100,125}. Concrete finite non-existence witnesses (a certified lower bound), via
  the sealed soundness lemma `hall_deficiency_blocks` specialized to `divNbhd`.
- Receipt: oracle/frontier_formalizer/work/gpt56-luna-LOWERBOUND-erdos710-2026-09-0-e710_lower_bound_50-20260903T144153/receipts/FINAL.json
- root_state VERIFIED, authority FULL_FORMALIZATION, axioms exactly
  {propext, Classical.choice, Quot.sound}, root_lean_sha256 bound to the proof bytes.
- Semantic court: close-driver-structural APPROVE + gemini-external-court (independent
  model) APPROVE on statement faithfulness (six axes).

# What this proves — and what it does NOT (honest)

PROVES: the autonomous execution+verification pipeline works end to end — the machine
computed the witnesses (real Python), authored the LEAN_THEOREM block, and drove it through
init -> external court -> kernel -> clean-axiom gate -> FINAL.json, with no human at the
stages. First autonomous FINAL.json in the MSL close program.

DOES NOT PROVE (Gemini flagged this at design review, honored here): novel LLM proof
SYNTHESIS. The soundness lemma and the proof scaffold were PROVIDED as a de-risked library
dependency; the machine's contribution was orchestration + witness computation + assembly,
not inventing the proof. The concrete lower bound is at specific n (n <= 125 for clean
decide); the asymptotic formula for f(n) remains OPEN.

# Known harness gap (repair item)

After the campaign closed at round 8, the driver did not recognize the campaign close as
CLOSURE_WORD TARGET_CLOSED and kept running until HALT_THEATER (three lint strikes at r16).
The close is real (summary campaign_closes carries it); the driver should halt cleanly on a
campaign close. Fix: on a CAMPAIGN_VERDICT CLOSED, treat as TARGET_CLOSED and stop.
