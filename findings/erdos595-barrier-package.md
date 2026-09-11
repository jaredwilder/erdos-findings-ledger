# Erdős #595 — bounds, barriers and reformulations

# ABSENCE-PROVEN: the "no fourth forcing mechanism" statement in section 2 is a PROVEN absence, not
# an assumed one. Two independent instruments were actually pushed: (a) the estate's deterministic
# federated retrieval over the partition-calculus and chromatic-graph literature, receipts under
# oracle/evidence/erdos595/; (b) an outside model queried with an explicit licence to answer "I do
# not know", receipt under oracle/evidence/ask-gemini/. Both returned the same three mechanisms and
# no fourth. That is what "unavailable" means here — a door that was pushed, twice, and did not
# open. It is NOT a claim that no fourth mechanism can exist; a future session should re-push.

**Target (OPEN, $250, erdosproblems.com/595, Erdős–Hajnal).** Is there an infinite graph with no
K₄ that is *not* the union of countably many triangle-free graphs?

**Status: OPEN. Nothing here closes it.** This is a package of upper bounds on the triangle cover
number, barriers on where a witness could live, exact reformulations, and two routes killed by
explicit counterexample. Everything is stated against the predicate `IsCountableUnionOfTriangleFree`
transcribed verbatim from the DeepMind formal-conjectures file
`FormalConjectures/ErdosProblems/595.lean`, so it speaks the target's own vocabulary.

> The append-only session log of how this was built — every correction and retraction included —
> is kept beside this file as `erdos595-barrier-package.HISTORY.md`.

---

## The artifact

`oracle/evidence/erdos595/lean/Erdos595Library.lean` — **42 theorems, one file, zero `sorry`**,
verified as a single unit on the WSL Mathlib project. Every declaration's axiom footprint is
`propext, Classical.choice, Quot.sound` or smaller; four finite certificates and the re-indexing
lemma need **no choice at all**. Receipts under `oracle/frontier_formalizer/cable/receipts/erdos595-*`.

Notation: `tc(G)` = least cardinal κ with E(G) a union of κ triangle-free subgraphs; `τ(G)` = sup of
χ(H) over triangle-free H ≤ G; `ν(G)` = least number of vertex classes each inducing a triangle-free
graph; `γ(G)` = domination number.

## 1. Upper bounds — each one is a necessary condition on a witness, read backwards

For **every** graph G:

| bound | theorem |
|---|---|
| `tc ≤ κ` whenever `χ(G) ≤ 2^κ` — the cardinal logarithm of the chromatic number | `proper_binary_cover` |
| `tc ≤ κ` on `κ⁺` vertices, no hypothesis at all | `successor_cardinal_bound` |
| `tc ≤ χ(T_G)`, the triangle-adjacency graph on the edges | `triangle_adjacency_general` |
| `tc ≤ ν` (as `Sym2 ν`; equal to ν for infinite ν) | `vertex_partition_bound` |
| `tc ≤` upper-neighbourhood chromatic numbers under **any** linear order | `ordering_bound_general` |
| `tc ≤` a label of the **larger** endpoint separating each triangle's top two | `top_vertex_bound` |
| a countable **proper edge colouring** forces a countable cover | `proper_edge_colouring` |
| countable triangle-adjacency forces a countable cover | `countable_links` |
| `tc` is the sup over edge-separated parts — **a witness may be assumed connected** | `component_reduction` |
| monotone under subgraphs; re-indexes along any surjection, so it depends only on index **cardinality** | `monotone_general`, `reindex` |

For **K₄-free** G additionally: `tc ≤ τ` (`tc_le_tau_general`), `tc ≤ γ` for infinite γ
(`dominating_general`), refined to the number of groups in any interference-free grouping
(`interference_bound`), and `χ ≤ 2^τ` (`chi_le_two_pow_tau`).

## 2. The barriers

**Power blindness.** *Every graph on at most `2^κ` vertices is a union of κ triangle-free
subgraphs* — no hypothesis on the graph. Inject V into `κ → Bool`; for each edge choose *any*
coordinate where the codes differ; layer by it. Three pairwise-differing booleans do not exist. The
*least* coordinate is never needed, and properness suffices in place of injectivity.

> **Consequence: the smallest object that could certify a witness has size exactly `(2^ℵ₀)⁺`.**
> Nothing smaller, of any shape, is a witness or contains one. Sharp from the other side: with the
> K₄-free condition dropped, the complete graph on `(2^ℵ₀)⁺` vertices *is* a witness by Erdős–Rado
> (cited, retrieved, not re-derived). **So the entire difficulty is the K₄-free hypothesis, not the
> cardinality.**

**All three known forcing mechanisms fail inside a K₄-free host, and a search for a fourth came
back empty** (see the ABSENCE-PROVEN note at the top of this file for what was actually run).
Colour induction (Folkman, Nešetřil–Rödl) has no infinite base; diagonalization cannot enumerate
`2^λ` colourings in λ steps; and every partition-calculus pigeonhole concludes with a *large
monochromatic clique*, which K₄-freeness forbids outright.

**Every local condition is met by a non-witness.** A witness must contain a nonempty induced
subgraph in which *every* vertex has an uncountably chromatic neighbourhood — but the **cone tower**
(each vertex given its own fresh triangle-free graph of uncountable chromatic number, joined
completely) satisfies that and has `tc = 2`. The separating property is global.

## 3. Exact reformulations, all kernel-checked

- **Partition-arrow form**: G is a witness ⟺ every colouring of its pairs by ℕ leaves some triangle
  of G monochromatic.
- **Transversal duality**: G is a witness ⟺ its family of triangle transversals is *countably
  centered* over E(G); and τ = the sup of χ over triangle-transversal deletions.
- **Link characterization**: G is K₄-free ⟺ every edge's link (its set of triangle apexes) is
  independent. So the flagship asks for a *linear 3-uniform hypergraph of uncountable chromatic
  number realizable with every edge-link independent*.
- **The level-down contrast**: a graph is a countable union of **bipartite** graphs **iff**
  `χ ≤ 2^ℵ₀` — an exact iff. One rung up, the same construction gives only the one-way bound and the
  converse is false (a triangle-free graph has `tc = 1` and unbounded χ). **That one-directional
  failure is why #595 is hard**, and it is now kernel-visible rather than folklore.

## 4. Two routes killed by explicit objects

**The vertex-partition reformulation is dead.** An exhaustive sweep of every circulant on 13–17
vertices found exactly two with `ν ≥ 3`, on complementary connection sets at 17 vertices — and
`{1,2,4,8}` with its negatives is exactly the quadratic residues mod 17: the **Paley graph of order
17**, the classical `R(4,4) = 18` witness. It is K₄-free (**kernel-checked**, all 83,521 quadruples),
has `tc = 2` (**kernel-checked**: the connection set splits `{1,4}` ∪ `{2,8}`, all 4,913 triples, *no
choice used*), and `ν ≥ 3` (all 65,536 two-partitions, checked twice by independent scripts).
**So `ν > tc` for a K₄-free graph** — ν is not a lower bound for tc, and the flagship does not reduce
to a vertex-partition question.

**The naive assembly route is dead**: a countable assembly of finite obstructions has countably many
edges and is killed by the countable floor.

## 5. Measured, with denominators

- Over **all** 2,097,152 labelled graphs on ≤ 7 vertices, with τ computed **exactly**: zero
  violations of `tc ≤ τ`. Plus 250 graphs on 8 vertices (130 of them K₄-containing), exact τ: zero
  violations. **So the K₄-free hypothesis of the ceiling bound may be removable** — an open question
  of this estate, not a theorem; the sealed proof uses it essentially. It *is* proved removable on
  two strata: when `τ ≤ 2` (block classification into bipartite / K₄ / book), and on graphs of ≤ 16
  vertices (explicit GF(16) coset cover, kernel-checked).
- The ceiling bound is **loose**: on Paley(17), `tc = 2` against `τ ≥ 4`.
- A sweep of **11,306** K₄-free circulants on 18–34 vertices found **none** with `tc ≥ 3`; 170
  candidates hit the per-candidate time limit and are counted as UNDECIDED, not as negatives.
- ⛔ **The enumeration route is exhausted.** The smallest K₄-free graph with `tc = 3` has ≥ 20
  vertices by the published Folkman bound, so no reachable brute force tests anything that separates
  these invariants. An earlier "`tc = ν` on 2,927 graphs" observation was **degenerate** — both
  invariants are pinned at 2 below 10 vertices — and is retracted; the separating graph sits at 17.
- ⛔ **One correction, self-caught**: `tc ≤ γ` holds for *infinite* γ only. Eight sampled graphs have
  `tc = 2, γ = 1`. The Lean statement was always the honest one (`IsUTF (Sym2 (γ × Bool))`); the
  prose was not, and is now qualified. The `reindex` theorem supplies the infinite-case reading.

## Novelty

The system decides, and it returns **INCREMENTAL / PROMOTION_BLOCKED** on the two headline bounds
(core 0.536 over a 30-record corpus; method facet clear, mechanism and outcome crowded). **Prior art
is not cleared and nothing here may be presented as a new mechanism.**

## The bottleneck, stated exactly

A witness needs a forcing mechanism outside colour induction, diagonalization, and
partition-calculus pigeonhole; it must live on `(2^ℵ₀)⁺` vertices or more; and no conjunction of the
sealed necessary conditions separates it from the cone tower. **Erdős #595 remains OPEN.**
