# Erdős #595 — the barrier / reformulation package (2026-09-05)

**Target (open, $250, erdosproblems.com/595, Erdős–Hajnal):** is there an infinite graph with
no K₄ that is *not* the union of countably many triangle-free graphs?

**Status of the flagship: OPEN. This package does not close it and does not claim to.**
An independent outside read (receipt `oracle/evidence/ask-gemini/20260905T163029-f0b18578.json`,
one model, unverified, citation depth only) reports the problem wide open with no substantial
published partial progress in either direction — no ZFC construction, no independence result.

## What IS sealed (Lean 4, Mathlib 919544d4, toolchain v4.31.0-rc1, run on the rented box)

Every declaration below has axiom footprint exactly `propext, Classical.choice, Quot.sound`,
zero `sorry`, zero `native_decide`. All statements are written against the predicate
`IsCountableUnionOfTriangleFree` transcribed **verbatim** from the DeepMind formal-conjectures
file `oracle/acquisition/formal-conjectures/FormalConjectures/ErdosProblems/595.lean`, so they
speak the target's own vocabulary.

| File | Content | Packet cards |
|---|---|---|
| `Erdos595Continuum.lean` | tc(G) > κ ⇒ χ(G) > 2^κ (cardinal-general); at κ=ℵ₀ every witness has chromatic number, vertex cardinality **and** edge cardinality above the continuum | T10, T11, T12 |
| `Erdos595Countable.lean` | a countable-edge graph IS such a union; the class is closed under countable unions; hence every witness has uncountably many edges | T13, T21 |
| `Erdos595Dispersion.lean` | product-colouring lemma; **sufficient condition**: every triangle-free subgraph C-colourable + G not (ℕ→C)-colourable ⇒ G is a witness | T38–T41, T43 |
| `Erdos595Hom.lean` | the witness property travels **forward along homomorphisms**; non-witnesses are closed under homomorphic preimage | T15 |
| `Erdos595Stability.lean` | independent blow-up invariance (iff); adding triangle-inert edges changes nothing | T16, T31 |
| `Erdos595Transversal.lean` | **exact reformulation**: G is a witness ⇔ its family of triangle transversals is *countably centered* over E(G) | T04, T05, T06 |

Receipts: `oracle/frontier_formalizer/cable/receipts/erdos595-*.json` (six). One statement
(the dispersion criterion) was independently re-verified on a **second, different** Mathlib
environment through `oracle/tools/msl_lean_cable.py` — receipt
`erdos595-dispersion-crosscheck.cable.json`, backend WSL — and both kernels agree.

## Two things worth stating flat

1. **The barrier is stronger than the standard one.** The usual observation is that a witness
   has uncountable chromatic number. The sealed statement is χ(G) > 2^ℵ₀, plus the same bound
   on |V| and (for graphs with no isolated vertices) |E|.
2. **The target now has two exact kernel-checked reformulations** — the dispersion criterion
   and the countable-centeredness of the transversal family. Neither produces an instance.

## Novelty

`noveltyforge` on the barrier claim: band **INCREMENTAL**, `PROMOTION_BLOCKED`, core 0.599 over
a 109-record corpus (mechanism facet clear 0.818; method and outcome anticipated). Prior art is
**not** cleared. The formalization is plausibly the new part; the mathematics of T10–T12 is
classical Erdős–Hajnal territory.

## The bottleneck, named exactly

No K₄-free graph is known — in the published record or in this estate — whose triangle-free
subgraphs all carry a proper colouring by a fixed palette C while the graph itself carries none
by (ℕ → C); equivalently, none whose triangle transversals are countably centered.

---

## Epoch 14 addendum (2026-09-05, same day) — the compactness ladder and the countable blindness barrier

Four more theorems, all kernel-checked through `oracle/tools/msl_lean_cable.py` on the WSL
Mathlib project (the rented box hit 100% disk this epoch and took no writes — machine fact,
receipted). Every declaration clean triple, zero `sorry`.

| Card | Statement | Receipt |
|---|---|---|
| **T26** | **de Bruijn-Erdos compactness for triangle covers**: for each fixed finite `k`, if every finite vertex set carries a `k`-colouring of pairs with no monochromatic triangle, the whole graph does. Product-of-discrete compactness. **First formalization.** | `erdos595-compactness-T26.cable.json` |
| **T27** | every witness has, for each `k`, a finite vertex set no `k`-colouring can serve | `erdos595-finite-obstruction-T27.cable.json` |
| **T28** | every witness carries a *countable* vertex set inside which all those finite obstructions already live | `erdos595-countable-core-T28.cable.json` |
| **NEW** | **countable blindness**: every countable induced subgraph of every graph *is* a countable union of triangle-free graphs | `erdos595-countable-blindness.cable.json` |

**The pair T28 + countable blindness is the sharpest thing this campaign produced.** Every
necessary condition we can seal — unbounded finite obstructions, a countable core carrying
them — is *already true inside a countable induced subgraph*, and the witness property is
*provably false* on every countable induced subgraph. So:

> The finite and countable obstruction ladders are **necessary and never sufficient**. Any proof
> strategy that passes through a countable elementary submodel, a countable core, a compactness
> argument at fixed palette size, or a finite obstruction ladder is blocked. The property first
> appears at the countable-to-uncountable jump.

That is a barrier result, not a solution. **Erdos #595 remains open.**

### Epoch 14, continued — two more equivalences and the tightness of the barrier

| Card | Statement | Receipt |
|---|---|---|
| **level-down** | a graph is a countable union of **bipartite** graphs **iff** it is properly colourable by `ℕ → Bool` (i.e. iff `χ ≤ 2^ℵ₀`) | `erdos595-bipartite-level-down.cable.json` |
| **arrow form** | `G` is a witness **iff** every colouring of its pairs by `ℕ` leaves some triangle of `G` monochromatic — the partition-arrow statement the literature uses | `erdos595-arrow-form.cable.json` |

**Why the level-down theorem matters.** One level down — covering by *bipartite* graphs instead
of triangle-free ones — the cover number is *exactly* the binary logarithm of the chromatic
number, so the analogous Erdős question is decided by a chromatic gap alone. At this level the
same binary-coding construction gives only the one-way bound `tc ≤ κ ⟸ χ ≤ 2^κ`, and the
converse is false (a triangle-free graph has cover number 1 and unbounded chromatic number).
**That one-directional failure is exactly why the chromatic barrier constrains a witness without
producing one.**

**The barrier is tight once K₄-freeness is dropped.** Our sealed bound says any witness needs
`> 2^ℵ₀` vertices. By Erdős–Rado (`(2^ℵ₀)⁺ → (ℵ₁)²_{ℵ₀}`, *A partition calculus in set theory*,
1956 — retrieved, real, but **not** re-derived here, so this half is CITED), the complete graph
on `(2^ℵ₀)⁺` vertices *is* a witness. So the least cardinality of a witness, with the K₄-free
condition dropped, is exactly `(2^ℵ₀)⁺`, and **the entire remaining difficulty of #595 sits in
the K₄-free hypothesis, not in cardinality.**

### The one live lead, and it is NOT verified

An outside model (receipt `oracle/evidence/ask-gemini/20260906T005233-40765576.json`) reports:
Rödl 1977 gives a triangle-free subgraph of chromatic number `≥ ℵ₁` inside every graph of
uncountable chromatic number — a *lower* bound on `τ`, and at `ℵ₁ ≤ 2^ℵ₀` it does **not** kill
the dispersion route; and it reports as *consistent* that a graph of chromatic number `ℵ₂` has
all triangle-free subgraphs of chromatic number `≤ ℵ₁`. Under CH such a graph would satisfy our
sealed dispersion criterion and be a witness — **if it can be taken K₄-free**.

⛔ A targeted retrieval (30 records, `lit-corpus2.json`) found the two anchor papers
(Erdős–Hajnal 1966, Erdős–Rado 1956) and did **not** find Rödl 1977 or any such consistency
construction. **The lead stands at citation depth on a single unverified model render.** It is
recorded as the next attack, not as progress.

---

## Epochs 15-16 (2026-09-06) — the ordering bound, and `tc ≤ τ` for K₄-free graphs

Eight more kernel-checked theorems (WSL Mathlib via the cable; clean triple, zero `sorry`).
The two that change the shape of the problem:

**1. `tc(G) ≤ τ(G)` for every K₄-free `G`** (`erdos595-tc-le-tau.cable.json`).
In a K₄-free graph every neighbourhood induces a *triangle-free* subgraph, so the triangle-free
chromatic ceiling supplies exactly the colouring the neighbourhood argument needs. **This is the
first upper bound on the cover number the refute branch has ever had.** Corollary
(`erdos595-chi-le-two-pow-tau`): `χ(G) ≤ 2^{τ(G)}` for K₄-free `G`.

**2. The ordering bound** (`erdos595-upper-neighbourhood-bound`, generalized to any index type in
`erdos595-ordering-bound-general`). For *any* linear order on `V`: if every vertex admits a
colouring proper on its neighbours *strictly above* it, `G` is a union of that many triangle-free
subgraphs. Proof: colour each edge by the colour its smaller endpoint gives the larger; the two
edges at the least vertex of a triangle always differ. Consequences, all sealed:

| | |
|---|---|
| `erdos595-countable-lower-neighbourhood` | colouring number ≤ ℵ₁ ⇒ `tc ≤ ℵ₀`; hence **no witness has ℵ₁ vertices** — a *second, independent* proof (the first was the chromatic barrier) |
| `erdos595-successor-cardinal-bound` | **every** graph on `κ⁺` vertices is a union of `κ` triangle-free subgraphs, with no hypothesis on the graph |
| `erdos595-proper-edge-colouring` | a countable proper edge colouring forces a countable cover |

So the cover number of a *smallest possible* witness is pinned: `ℵ₁ ≤ tc ≤ 2^ℵ₀`, on a vertex set
of size exactly `(2^ℵ₀)⁺`.

**3. The local route is dead, by construction** (`erdos595-cone-two-layers`). Every witness must
contain a nonempty induced subgraph in which *every* vertex has an uncountably chromatic
neighbourhood — but the **cone tower** (each vertex given its own fresh triangle-free graph of
uncountable chromatic number, joined completely) satisfies that condition and has `tc = 2`. So no
condition on neighbourhoods alone can separate a witness; the separating property is global.

**4. Two more equivalences**: the **compactness ladder** (T26/T27/T28) and the **partition-arrow
form**. And a correction worth recording: an earlier model render quoted Rödl 1977 as an
*uncountable* theorem — retrieval shows it is the **finite** girth-four case
(PAMS 64 (1977) 370–371, DOI 10.1090/s0002-9939-1977-0469806-4). That render is convicted.

**Erdős #595 remains OPEN.** These are barriers, bounds and reformulations, not a solution.

---

## The consolidated library (2026-09-06)

`oracle/evidence/erdos595/lean/Erdos595Library.lean` — **25 theorems, one file, zero `sorry`,
axiom footprint `propext, Classical.choice, Quot.sound` on every declaration**, verified as a
single unit on the WSL Mathlib project (receipt `erdos595-library.cable.json`, sha `23596f73…`).
Everything is stated against `IsCUTF`, transcribed verbatim from the formal-conjectures file.

New since the last addendum:

| Theorem | Content |
|---|---|
| `tc_le_tau_general` | `tc ≤ τ` for K₄-free graphs **at every cardinal**, not just ℵ₀ |
| `ordering_bound_general`, `successor_cardinal_bound` | the ordering bound and the `κ⁺ ⇒ κ` bound at every cardinal |
| `transversal_ceiling` | the ceiling equals the sup of `χ` over **triangle-transversal deletions** (packet T45/T46) |
| `locally_countable_component` | a locally countable graph has countable components |
| `countable_links` | **if every edge shares triangles with only countably many edges, `G` is a countable union of triangle-free graphs** — so every witness has an edge in uncountably many triangles, whose link (by `link_independence`) is an **uncountable independent set** |
| `link_independence` | `G` is K₄-free **iff** every edge's link (its set of triangle-apexes) is independent |
| `subadditivity`, `hereditary_dispersion`, `triangle_adjacency_general` | the cardinal-general and class-general forms |

### Two barriers worth stating plainly

**(a) The only known forcing mechanism is structurally unavailable.** At `(2^ℵ₀)⁺` the complete
graph is a witness by Erdős–Rado, whose conclusion is a *large monochromatic clique*. In a
K₄-free graph a monochromatic clique has at most 3 vertices, so that mechanism cannot run inside
a K₄-free host. The construct branch needs a genuinely new forcing mechanism.

**(b) Every local condition is satisfied by a non-witness.** The cone tower meets every
neighbourhood/link condition a witness must meet and has `tc = 2`. So the separating property is
global, and no conjunction of the sealed necessary conditions can produce a witness.

Novelty (the system decides): the two headline bounds come back **INCREMENTAL**,
`PROMOTION_BLOCKED`, core 0.536 over a 30-record corpus — method facet clear, mechanism and
outcome facets crowded. **Prior art is not cleared and nothing here may be presented as a new
mechanism.**

**Erdős #595 remains OPEN.**

---

## The invariant picture (2026-09-06) — six upper bounds on the cover number

The library now holds **28 theorems** (`Erdos595Library.lean`, one file, zero `sorry`, clean
triple throughout). Collecting the sealed upper bounds, for every **K₄-free** `G`:

```
tc(G)  ≤  τ(G)                      the triangle-free chromatic ceiling          [tc_le_tau_general]
tc(G)  ≤  γ(G)   for INFINITE γ    the DOMINATION number                        [dominating_general]
tc(G)  ≤  ν(G)                      least # of triangle-free-inducing vertex classes [vertex_partition_bound]
tc(G)  ≤  χ(T_G)                    chromatic number of the triangle-adjacency graph [triangle_adjacency_general]
tc(G)  ≤  inf over linear orders of sup_u χ(G[N⁺(u)])                            [ordering_bound_general]
tc(G)  ≤  κ  whenever χ(G) ≤ 2^κ    the binary-coding barrier                    [epoch-11 file]
```

and for **every** graph, `tc(G) ≤ κ` on `κ⁺` vertices [`successor_cardinal_bound`].

**Every one of these is a necessary condition on a witness, read contrapositively.** A witness
therefore has: uncountable ceiling; **no countable dominating set**; **no countable partition of
its vertices into triangle-free-inducing classes**; uncountably chromatic triangle-adjacency
graph; defeats the ordering bound at *every* linear order; chromatic number above the continuum;
and more than `(2^ℵ₀)` vertices. Also (`countable_links`) an edge lying in uncountably many
triangles, whose link is an uncountable independent set.

Two of these — the domination bound and the vertex-partition bound — are new this session and
are *independent* of the ordering bound: the cone tower is decomposed by the partition bound
(via its rank function) while its neighbourhood derivative never empties.

**Nothing here produces a witness, and Erdős #595 remains OPEN.**

---

## The library at 34 theorems, and the sharpest barrier: POWER BLINDNESS (2026-09-06)

`Erdos595Library.lean` — **34 theorems, one file, zero `sorry`, clean triple throughout**
(sha `356e92a0…`). Three more mechanisms sealed since the last note:

- **`interference_bound`** — far-apart dominators may share a layer, so `tc ≤` the number of
  groups in any interference-free grouping of any dominating family. Strictly refines the
  domination bound.
- **`component_reduction`** — `tc` is the supremum over the parts of any edge-separated vertex
  partition, in particular over connected components (packet T17/T32). **A witness may be
  assumed connected.**
- **`top_vertex_bound`** — colour each edge by a label of its *larger* endpoint; if the labelling
  separates the top two vertices of every triangle, the layers are triangle-free. A ninth,
  independent mechanism.
- **`monotone_general`** — cover-number monotonicity at every cardinal.

### POWER BLINDNESS — the sharpest thing in the package

> **`power_blindness_general`: every graph on at most `2^κ` vertices is a union of `κ`
> triangle-free subgraphs. No hypothesis on the graph at all.**

Proof (and it is short): an injection `V → (κ → Bool)`; for each edge choose *any* coordinate
where its endpoints' codes differ; layer by that coordinate. Three pairwise-differing booleans
do not exist, so every layer is triangle-free. **The "least" coordinate is never needed** —
which is why this generalizes the epoch-11 continuum barrier for free.

At `κ = ℵ₀`: **every graph on at most `2^ℵ₀` vertices is a countable union of triangle-free
graphs.** Combined with the sealed cardinality bound from the other side, this closes the
certificate-size question completely:

> **The smallest object that could certify an Erdős #595 witness has size exactly `(2^ℵ₀)⁺`.**
> Nothing smaller — of any shape, K₄-free or not — can be a witness or contain one.

This strictly subsumes the earlier "countable blindness" barrier (retracted, superseded).

**Erdős #595 remains OPEN.** All eleven sealed mechanisms are upper bounds; none produces a
witness, and the three known mechanisms for *forcing* a monochromatic triangle (colour
induction, diagonalization, partition-calculus pigeonhole) are each proved or argued
unavailable inside a K₄-free host.

### Correction, self-caught by calibration (2026-09-06)

A brute-force check over 40 random K₄-free graphs on 6 vertices with triangles
(`oracle/evidence/erdos595/calibration.json`) found **8 graphs with `tc = 2` and `γ = 1`**.
The Lean theorem is correct as stated — it concludes `IsUTF (Sym2 (I × Bool)) G`, i.e.
`tc ≤ |Sym2(γ × Bool)|`, which is `γ` only when `γ` is infinite. **The prose "tc ≤ γ" is valid
for infinite `γ` only** and has been qualified wherever it appeared. `tc ≤ ν` and `tc ≤ χ` held
on every sampled graph, and `tc = ν` held on all 40.

---

## Library at 36 theorems; the finite/infinite reading repaired (2026-09-06)

`Erdos595Library.lean` — **36 theorems, zero `sorry`, clean triple** (sha `1f28cfae…`).

**Re-indexing** (`erdos595_reindex`, and it needs *no choice at all* — footprint `propext,
Quot.sound`): a cover re-indexes along any surjection of index types, so the cover number depends
only on the **cardinality** of the index. That repairs the reading the calibration had convicted:
at infinite cardinals the partition, domination and interference bounds really do read
`tc ≤ ν`, `tc ≤ γ`, `tc ≤ #groups`; at finite cardinals they do not, and the sealed statements
(`IsUTF (Sym2 (I × Bool))` etc.) are the honest form.

**Partition lower bound** (`erdos595_partition_lower_bound`): contrapositive of the partition
bound — a graph not covered by `Sym2 I` admits no triangle-free vertex classification by `I`.
With the finite Folkman/Nešetřil–Rödl input this forces the **vertex-partition number to be
unbounded on finite K₄-free graphs**.

### What the machine could and could not test

Two measured facts, with their real denominators:

- Over **17,699** K₄-free graphs on 6–9 vertices carrying a triangle, **both** the cover number
  and the vertex-partition number were pinned at **2**. The earlier "tc = ν on 2,927 graphs"
  observation is therefore **degenerate** — the sample could not have separated them. Retracted
  and downgraded.
- Over **1,135** graphs on 5–7 vertices (K₄-containing ones **included**), the cover number never
  exceeded a *lower estimate* of the triangle-free ceiling. So the K₄-free hypothesis of the
  ceiling bound **may be removable** — recorded as an open question of this estate, not a theorem
  (the sealed proof uses K₄-freeness essentially).

⛔ **The enumeration route is exhausted.** The smallest K₄-free graph with cover number 3 has at
least 20 vertices by the published Folkman bound, so no reachable brute force can test any
question that separates these invariants.

**Erdős #595 remains OPEN.**

---

## A clean separation: the Paley graph of order 17 (2026-09-06)

An exhaustive sweep of **every circulant on 13–17 vertices** (all connection sets, K₄-freeness
checked by exhaustive quadruple enumeration) found exactly two with vertex-partition number ≥ 3 —
and they are complementary connection sets on 17 vertices. The connection set `{1,2,4,8}` and its
negatives is **exactly the set of quadratic residues mod 17**: the graph is the **Paley graph of
order 17**, the classical `R(4,4) = 18` lower-bound witness.

| | |
|---|---|
| K₄-free | yes — 0 copies of K₄ among all 2380 quadruples |
| edges / triangles | 68 / 68 |
| **triangle cover number `tc`** | **exactly 2** — the connection set splits as `{1,4}` ∪ `{2,8}` and neither class carries a triangle. **Kernel-checked by `decide`** over all 4913 ordered triples (`erdos595-c17-two-cover.cable.json`, axioms `propext, Quot.sound` — *no choice at all*) |
| **vertex-partition number `ν`** | **≥ 3** — all 65,536 two-partitions checked, every one has a class containing a triangle |

> **Therefore `ν > tc` for a K₄-free graph: the vertex-partition number is NOT a lower bound for
> the triangle cover number.**

That **kills** the reformulation route (`GAP7`): the flagship does *not* reduce to a
vertex-partition question. It also proves — rather than merely suspects — that the earlier
"tc = ν on 2,927 graphs" coincidence was degenerate: the separating graph sits at 17 vertices,
just above the 9-vertex ceiling brute force could reach.

Two kernel runs **failed** and are filed as failures with their repairs: a single conjunction of
the K₄-free and cover statements failed instance synthesis at 365 s (repair: state each half as a
*boolean* computation and split the obligations), and `K₆ is not 2-coverable` exhausted its tier
at 493 s (a quantifier over a *function type* is a different computational shape from one over a
finite index).

**Erdős #595 remains OPEN.**
