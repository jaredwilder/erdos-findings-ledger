# 800 Lean files, 0 proved, and a composition that launders a false hypothesis

**An audit of the `box-final` and `strengthen` pools, 2026-09-11.** Three findings were re-checked
directly and are marked **[re-checked]**.

I had described these pools as "1,372 math-bearing Lean files with no receipts" and treated them as
a publishing backlog. **They are not results. They are a statement corpus, and it contains
falsehoods.**

---

## 1. Every mathematical claim in the pool is `:= by sorry`

800 `.lean` files, 669 distinct by content. They come in six fixed roles: leaf claims (249),
triviality probes (112), strengthen base/step/implication (85), parent goals (84), definitions (74),
DAG bank arithmetic (48), propositional glue (29), and assorted probes (119).

**All 333 claim and parent files are `:= by sorry`. Not one exception.** The only files without
`sorry` are definitions, the triviality probes, the glue closed by a `tauto` cascade, and bank
arithmetic like `1/2 + 1/3 = 5/6`.

The machine's own ledger agrees: across 32 `LEAF-RESULTS.json` files, **7 leaves proved of 63, 8
compositions of 62**, and the strengthen report states outright *"VERIFIED_THEOREMs produced: 0."*

## 2. The only claims the pipeline ever closed are the vacuous ones

The 7 leaves marked `PROVED` include all three Erdős 1065 children, of the shape
`∃ p, p ∈ Icc 2 100 → False ∨ …` — take `p = 0`, the antecedent fails, `aesop` closes it instantly.
Another is a verbatim unfolding of a set definition.

**The pipeline's success set is precisely its degenerate set.**

## 3. A false claim, and the triviality probe endorsed it **[re-checked]**

Erdős 936, claim `c1`:

```lean
theorem msl_erdos936_demand_r020_l1_1_c1 (k : Nat) : 3 ∣ (2 ^ (6 * k + 2) + 1) := by sorry
```

**This is false.** `2^(6k+2) ≡ 1 (mod 3)`, so `2^(6k+2) + 1 ≡ 2 (mod 3)` for every `k`. Verified for
k = 0..5: the values 5, 257, 16385, 1048577, 67108865, 4294967297 are all `2 mod 3`.

The correct family is `6k+1`, where `2^(6k+1)+1` gives 3, 129, 8193, 524289, 33554433 — each
divisible by 3 and not by 9, which is exactly what the surrounding argument needs. **An off-by-one
in an exponent.**

What makes it worth publishing: the structure around it is the best-formed argument in the pool — a
valid three-lemma proof that an infinite family is never powerful — and **the triviality probe
returned "non-trivial, worth pursuing" on the false claim.** The machine's own signal for
"promising" fired on a falsehood.

## 4. A false row, and a composition that launders it **[re-checked]**

Erdős 18, parent claim, row 4:

```lean
ExactTuple (Nat.factorial 4) ({3, 4, 6, 8}) 4
```

**`3 + 4 + 6 + 8 = 21`, but `4! − 1 = 23`.** The row is false. Genuine solutions exist —
`{3,8,12}`, `{1,2,8,12}`, `{1,4,6,12}`, `{2,3,6,12}` — but the stated set is not one of them. Rows
2, 3, 5 and 6 check out.

**Then the composition file derives the entire five-way conjunction from that one false row alone**,
as `ExactTuple (4!) {3,4,6,8} 4 → (all five)` — and it passes, because `tauto` proves anything from a
hypothesis it never has to discharge.

That is the failure mode to remember: a composition step that is *formally valid* and
*mathematically worthless*, because its antecedent is false.

## 5. The same set asserted `Finite` and `Infinite` in one batch

Erdős 938: `{k : ℕ | IsNondegenerateAP3 …}.Infinite` in one file, `apStarts.Finite` and
`{k | TripleIsAP k}.Finite` in two others — **same batch, same set, opposite conclusions.**

Erdős 887 is the same pathology stated more precisely: the `A` and `B` parents are literal
negations of each other, quantifier for quantifier.

The problem is genuinely open, so neither is refuted. The machine simply has no idea which way it
points and emitted both as goals.

## 6. `#print axioms` reporting clean on a file that failed to compile

Thirteen files carry `rc=1` with parse errors while their main theorem still prints as axiom-free —
including one whose statement slot literally contains `theorem X : theorem Y … := by`.

**An axiom-footprint receipt is only meaningful alongside `rc=0`.** This is the same trap as reading
a textual absence of `sorry` as proof, one layer up.

Twelve further files use `native_decide`, putting the Lean compiler in the trusted base rather than
the kernel.

## What the pool is actually good for

It is a **well-typed statement corpus**, and that has real value. Roughly half the files are
machinery; the other half holds about 275 genuine Erdős statements across **33 problem numbers not
otherwise published here** — 9, 18, 28, 40, 124, 137, 168, 188, 208, 212, 288, 306, 324, 400, 421,
424, 456, 470, 507, 508, 786, 830, 853, 887, 931, 936, 938, 1052, 1060, 1065, 1101, 1106, 1145.

And there is a receipt trail better than a `verify.json`: `rescue/x/out/<batch>/<name>.log` plus
`.rc`. A claim with `rc=0` and only a sorry-warning **type-checks** — it is well-formed Lean, not a
syntax fantasy (147 of 341 are in this state; 152 fail to elaborate at all). Its triviality probe
returning `rc=1` with unsolved goals is **machine-checked evidence the claim is not closable by
`rfl/trivial/decide/norm_num/simp`**, so it is not a definitional restatement.

**79 claims carry both receipts.** That pair — elaborates, and is not trivially closable — is the
right filter for pointing a prover at something.

The three best targets by that filter: **Erdős 1052** (unitary perfect numbers to 10⁷, and the
asserted hit set `{6, 60, 90, 87360}` is correct), **Erdős 936** once the exponent is fixed to
`6k+1`, and **Erdős 288**'s `c1`, which is the classical Kürschák statement correctly formalised.

## The correction this forces on me

I previously described these as 1,372 unpublished math-bearing files and implied the work was
publishing them. **That was wrong twice over.** They are not proofs, and at least two of them are
false. Shipping them as a corpus of results would have repeated the cable-corpus error at four times
the scale.

A well-typed open statement is a useful artifact. It is not a theorem, and the distance between
those two things is this entire document.
