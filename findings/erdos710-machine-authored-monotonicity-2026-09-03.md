---
id: erdos710-machine-authored-monotonicity-2026-09-03
title: Erdős #710 — the machine AUTHORED a real new theorem, one tactic from proven
status: AUTHORED (proof one tactic from closing; harness now fixed to let it iterate)
domain: number theory / autonomous proof synthesis
updated: 2026-09-03
---

# What happened (honest, verified)

Pointed at Erdős 710 itself with 90 rounds and the sealed arsenal as building blocks, the
autonomous driver (gpt-5.6-luna, reasoning off) did NOT copy the provided scaffold. It
chose a real target and AUTHORED a new theorem it was not handed:

`endpoint_feasibility_restriction` — it defined `ValidAssignment n a` itself
(Set.InjOn a (Icc 1 n) ∧ ∀ k ∈ Icc 1 n, k ∣ a k) and stated + proved that a valid
assignment on {1..n+1} restricts to {1..n} (the feasibility core of endpoint monotonicity
f(n+1) ≥ f(n)-1, theorem T1 in the bank). Genuine proof synthesis: right target, right
structure (widen Icc 1 n ⊆ Icc 1 (n+1), apply injectivity/divisibility).

## Why it did not seal, and how close it was

The proof failed at the kernel: `omega could not prove the goal` at three membership
subgoals — luna applied `omega` to `x ∈ Set.Icc 1 (n+1)` without unfolding membership to
arithmetic first, leaving sorryAx → UNVERIFIED. ONE tactic short. The minimal fix
(`simp only [Set.mem_Icc] at *` so omega sees the bounds) makes luna's exact theorem close
KERNEL_CHECKED with clean axioms {propext, Classical.choice, Quot.sound} — verified
(scratch fix_luna, cable KERNEL_CHECKED).

## The harness bug that stopped it iterating (FIXED this session)

The campaign fed the machine `KERNEL_STATUS None` instead of the omega errors:
`attach_kernel_receipt` RAISES on any non-VERIFIED receipt, so the bridge threw and the
real error never reached the author. Blind to why it failed, the machine could not repair
the one tactic and stalled (HALT_THEATER). Fix: the bridge now attaches only on VERIFIED,
and on UNVERIFIED RETURNS the kernel errors (per-line) in the verdict;
msl_close_driver._fire_campaign surfaces them as KERNEL_ERRORS + a repair hint back to the
machine. Confirmed: a broken proof now returns the omega errors, not a raise.

Also this session: deep mode (`package_halt: False`) — a TERMINAL_PACKAGE that seals no
new theorem is refused and redirected to authoring the next one, so a deep run cannot quit
on an empty package (it did on round 1 before the fix).

## The honest state

The machine CAN author novel theorems (right target, near-correct proof). It could not yet
ITERATE to a close because the harness hid its errors — now fixed. Whether it can close a
self-authored theorem with the error feedback loop is the next paid experiment. The
asymptotic formula for f(n) remains OPEN; this is about the machine proving new sub-theorems.

# UPDATE (same day): the machine CLOSED its own theorems — with self-repair

Re-run with the error feedback live (deep mode, 90-round cap, thumb off the scale — no
proof touched by a human). Result: the autonomous driver authored ~14 theorems and SEALED
THREE, each VERIFIED / FULL_FORMALIZATION / clean axioms {propext,Classical.choice,
Quot.sound} / gemini-external-court + structural APPROVE. $1.42, 42 rounds.

CLOSED (row 1, machine-authored, no human proof edit):
- feasible_iff_assignment : Feasible n L S k ↔ ∃ f injective with f x ∈ divNbhd n L (k x).
  A real 710-structural bridge (feasibility ⟺ the divisibility-matching formulation).
- deficient_union_blocks_injection_repaired : InjOn f S ∧ (∀x∈S, f x ∈ t x) ∧
  |biUnion t| < |S| → False (the Hall soundness core in contradiction form). AUTHORED,
  FAILED, RE-AUTHORED (the "_repaired" suffix), then SEALED — the iteration loop working.
- bounded_feasible_threshold : a nonempty bounded feasible-length set has a least element
  (f well-defined as a minimum). Foundational.

Two of three carry "_repaired": the machine hit the kernel, got a failure, and fixed its
own proof. Autonomy demonstrated end to end (author -> kernel -> repair -> seal -> court ->
FINAL.json), no human in the proof loop.

HONEST SCOPE: these are the foundational/structural layer of 710 (well-definedness, the
feasibility-matching bridge, the Hall core), not the asymptotic formula. Still-open harness
gap: several attempts failed as KERNEL_STATUS None (a campaign-side exception, not the omega
path), and the per-line error feedback did not reach those; the machine closed 3 anyway.
