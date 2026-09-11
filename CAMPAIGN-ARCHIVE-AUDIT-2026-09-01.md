> **Published 2026-09-11, ten days after it was written.** This audit read the estate's own raw
> campaign archive and rejected fifteen of its claims. It had been sitting in a downloads folder.
>
> **The single most important line is in section 1:** of 135 kernel-checked receipts, **only 8 have
> a syntactically quantified or implicational conclusion.** The rest are finite Bool or instance
> fragments. A count of "135 kernel-checked" therefore says almost nothing about how many universal
> statements were proved.
>
> The other number worth reading twice: the route registry holds 3,886 lemma records of which
> **710 are labelled PROVED and 691 are labelled FALSE.** The audit says plainly that the 710 "are
> *not* all valid theorems", and then demonstrates it.
>
> **One rejection here refutes a find reported to me as PROVED on 2026-09-11.** An independent ore
> miner surfaced the Erdos 885 construction `N_i = i*lcm(1..2k)` as "closing the canonical statement
> affirmatively". This audit rejects it, because `0` lies in `D(N)` only when `N` is a perfect
> square, and those `N_i` are not squares. **Checked directly: for k = 3, none of N_1..N_5 is a
> square and none has 0 in its difference set.** The audit is right.
>
> Several rejections are quantifier errors rather than arithmetic ones, which is the harder class to
> catch: #881 refutes an existential with a single bad witness; #653 uses a low-value witness to
> upper-bound a maximum; #412 confuses the divisor sum with the aliquot sum, giving sigma(6)=6 when
> it is 12.
>
> **A note on why this document existed at all.** Reviewing what the estate's ingestion captured
> versus what it dropped, the pattern is consistent: constructions and positive theorems were
> reliably banked; **barrier theorems and negative results were the ones that fell through.** The
> refutations in this file are exactly the class of result the pipeline does not keep, which is why
> publishing them matters more than publishing another positive.

---

# ERDŐS RAW CAMPAIGN — GOLD-MINE AUDIT
**Snapshot audited:** 2026-09-01 raw archive.  **Policy:** prove-before-promote; registry labels are evidence, not truth.

## 1. What is actually in the archive
- **8,049 files** total; **252 Lean files**, **6,006 JSON**, **607 JSONL**, **173 logs**.
- Route registry: **3,886 lemma records**; statuses: UNTESTED=1393, COMPUTATION_SUPPORTED=1092, PROVED=710, FALSE=691.
- **710 records labeled PROVED** across **189 Erdős problem numbers**. These are *not* all valid theorems; see quarantine.
- Gold ledger: **941 assets** across **213 campaign labels**: PROVED_LEMMA=818, COUNTEREXAMPLE=81, VERIFIED_WITNESS=26, OBSTRUCTION_CASE_LAW=8, KERNEL_THEOREM=5, CITATION_CONDITIONAL_CLOSE=3.
- Cable: **207 formalization receipts** = **135 KERNEL_CHECKED** + **72 KERNEL_FAILED**. Among checked: **107 empty-axiom-footprint**, **17 need Mathlib**.
- Only **8 / 135** checked receipts have a syntactically quantified/implicational conclusion; most of the 135 are finite Bool/instance fragments. This is the single most important scope distinction.
- Witness closer: **40 receipts**, **22 VERIFIER_PASS**.
- Raw A/B transcript tree: **56 transcript files**, **1058 records**, about **480,315 assistant characters**. Raw campaign transcripts: **36 files / 404 records**.

## 2. Highest-confidence mathematical gold
These are the items I would send to the Lean formalizer first. “Audited” means the mathematical argument was independently checked in this pass; it does **not** assert novelty.
### A1 — #276
**Claim.** For every Fibonacci-type Nat recurrence a(n+2)=a(n+1)+a(n), d divides every term iff d divides gcd(a0,a1).
**Status.** ALREADY FULLY KERNEL_CHECKED.  **Leanability:** DONE.
**Why it matters.** One of the rare cable receipts whose conclusion is genuinely universally quantified, not a sampled Bool.
**Origin.** `cable-kernel-receipts/fmz-erdos276-campaign-001-R004-L1.cable.json`

### A2 — #400
**Claim.** For every m,k>=2, g_k(m!) >= m+k-3, witnessed by (m!-1,m,1,...,1); in fact the factorial product equals (m!)!.
**Status.** PROOF AUDITED; EXISTING LEAN ONLY CHECKS m=5,k=2.  **Leanability:** VERY HIGH.
**Why it matters.** Clean universal infinite-family lower bound. Existing cable receipt undersells it as a single instance.
**Origin.** `msl-machine/campaigns/erdos400-campaign-001/routes/registry.jsonl R003/L1`

### A3 — #400
**Claim.** For k=2, g_2(n) <= s2(a)+s2(b)-s2(n) <= 2 ceil(log2 n), hence g_2(n)=O(log n), by Legendre v2(t!)=t-s2(t).
**Status.** PROOF AUDITED.  **Leanability:** HIGH.
**Why it matters.** A genuine all-n analytic bound; independent of the archive’s false small-value claims.
**Origin.** `msl-machine/campaigns/erdos400-campaign-001/routes/registry.jsonl R005/L1`

### A4 — #700
**Claim.** If p,q are primes, f(pq)=min(p,q) for f(n)=min_{1<k<=n/2} gcd(n,C(n,k)).
**Status.** PROOF AUDITED.  **Leanability:** MEDIUM-HIGH.
**Why it matters.** Exact infinite family. Lower bound uses n/gcd(n,C(n,k)) | k; equality at k=max(p,q), with Lucas/Kummer.
**Origin.** `msl-machine/campaigns/erdos700-campaign-001/routes/registry.jsonl R005/L1`

### A5 — #289
**Claim.** In any consecutive interval of length >=2 the maximum 2-adic valuation is unique; therefore a single interval reciprocal sum is never an integer. More generally, if a union/multiset of intervals has integer reciprocal sum, an even number of intervals attain the global maximum v2.
**Status.** PROOF AUDITED; FINITE RECEIPT EXISTS.  **Leanability:** HIGH.
**Why it matters.** The universal parity theorem is stronger than the finite witness receipt and is exactly the sort of lemma Lean should bank.
**Origin.** `msl-machine/campaigns/erdos289-campaign-001/routes/registry.jsonl R004/L1 + witness receipt`

### A6 — #949
**Claim.** For every sum-free S⊂R, there exists q∈{1,2,3,4,5} with q∉S and 2q∉S.
**Status.** AUDIT STRENGTHENING OF VERIFIED RAW CLAIM.  **Leanability:** EXTREMELY HIGH.
**Why it matters.** Raw verifier searched {1..24} and q<=12. A two-case hand proof shrinks the entire finite core to {1..10}, q<=5.
**Origin.** `cable-kernel-receipts/fmz-erdos949-campaign-001-R001-L1.witness.json`

### A7 — #376
**Claim.** gcd(C(2n,n),105)=1 iff doubling n has no carries in bases 3,5,7; equivalently base-3 digits<=1, base-5<=2, base-7<=3.
**Status.** PROOF AUDITED AS STANDARD KUMMER REDUCTION.  **Leanability:** MEDIUM.
**Why it matters.** Exact pointwise reformulation of the open infinitude problem into simultaneous digit restrictions.
**Origin.** `msl-machine/campaigns/erdos376-campaign-001/routes/registry.jsonl R001/L1`

### A8 — #412
**Claim.** For n>=2, sigma(n)>=n+1, equality iff n is prime; every iterated-sigma orbit is strictly increasing.
**Status.** PROOF AUDITED; FINITE KERNEL FRAGMENT EXISTS.  **Leanability:** EXTREMELY HIGH.
**Why it matters.** Simple universal invariant that survived the audit even though the campaign’s separate sigma(6)=6 counterexample was nonsense.
**Origin.** `msl-machine/campaigns/erdos412-campaign-001/routes/registry.jsonl R004/L1`

### A9 — #247
**Claim.** If a_n is strictly increasing and limsup a_n/n=∞, then Σ 2^{-a_n} is irrational.
**Status.** PROOF AUDITED (PARTIAL VS TRANSCENDENCE TARGET).  **Leanability:** MEDIUM-HARD.
**Why it matters.** Rational binary expansions are eventually periodic; an infinite periodic tail has positive 1-density, forcing a_n=O(n).
**Origin.** `msl-machine/campaigns/erdos247-campaign-001/routes/registry.jsonl R001/L1`

### A10 — #313
**Claim.** If an Egyptian-prime solution begins (2,3,p), then m=6p/(p-6)=6+36/(p-6); integrality forces p-6|36, and the only prime p>3 is p=7.
**Status.** PROOF AUDITED.  **Leanability:** EXTREMELY HIGH.
**Why it matters.** Tiny exact Diophantine pruning lemma; good reusable branch-kill.
**Origin.** `msl-machine/campaigns/erdos313-campaign-001 routes / raw ledger`

### A11 — C(13,6,3)
**Claim.** The raw run contains a 21-block covering of all 286 triples; independently rechecked. Any hypothetical 20-block cover has every point degree at least 8.
**Status.** WITNESS VERIFIED + STRUCTURAL THEOREM AUDITED.  **Leanability:** HIGH.
**Why it matters.** Degree theorem: degree 7 would induce seven 5-subsets covering all 66 pairs of 12 points, contradicting Schönheim C(12,5,2)>=8.
**Origin.** `msl-eta-ab-2026-08-31/run20-frontier-C13-6-3/transcript-court.json and run23b fearless court`

### A12 — #689
**Claim.** Any double-cover by one residue class mod each prime p<=n requires Σ_{p<=n} ceil(n/p)>=2n. At n=100 the exact sum is 194<200.
**Status.** PROOF AUDITED; n=100 KERNEL_CHECKED.  **Leanability:** HIGH.
**Why it matters.** Clean double-count obstruction. Note archive’s decimal Σ_{p<=300}1/p≈2.026 is wrong; exact value is about 2.012855, still >2.
**Origin.** `cable-kernel-receipts/fmz-erdos689-campaign-001-R004-L1.cable.json`

## 3. Two especially good promotion proofs
### #949: shrink the 2^24 search to a 2-case proof on {1,…,10}
Assume for contradiction that a sum-free S contains at least one of q,2q for each q=1,…,5. If 1∈S, then 2∉S, so 4∈S; hence 5∉S, so 10∈S. Also 3∉S (otherwise 1+3=4), so 6∈S; then 4+6=10 contradicts sum-freeness. If 1∉S, then 2∈S, hence 4∉S and 8∈S. If 3∈S then 5∉S, so 10∈S, but 2+8=10; if 3∉S then 6∈S, but 2+6=8. Contradiction. Therefore some q≤5 has q,2q∉S.

### #400: exact factorial witness
Set n=m! and choose (a1,a2,a3,…,ak)=(m!−1,m,1,…,1). Then a1!a2!…ak!=(m!−1)!·m!=(m!)!=n!, so the divisibility constraint holds with equality. The objective is (m!−1)+m+(k−2)−m!=m+k−3. Thus g_k(m!)≥m+k−3 for every m,k≥2. The existing cable receipt checks only m=5,k=2; the universal theorem is strictly stronger and should replace it.

## 4. Verified finite/computational objects worth banking
- **C(13,6,3) ≤ 21:** the raw run20 21-block list covers all **286/286** triples; independently rechecked exactly.
- **Hypothetical 20-cover degree theorem:** every point has degree ≥8. This is a clean finite-combinatorial Lean target; do **not** promote the later claim that the 12 off-point blocks must cover all 220 off-point triples—that step is not valid.
- **#689 at n=100:** exact sum of capacities is 194<200; already axiom-free KERNEL_CHECKED.
- **#949:** existing verifier exhausts 2^24 subsets successfully; audit compresses it to a hand theorem q≤5.
- **#51:** witness receipt certifies the finite totient range t=32..63; useful as a finite object, but not a canonical close.
- **#595:** exhaustive n≤6 graph implication verifier passes.
- **#952:** exact finite Gaussian-prime unit-step chain bound ≤5 inside radius 200 passes after correcting the diagonal-step bug.

## 5. Red-alert false gold — do not send these to Lean as canonical claims
- **#243 — REJECT:** a1=2, a_{n+1}=a_n^2-a_n+2 has rational reciprocal sum 1 and refutes target. **Why:** First terms [2, 4, 14, 184, 33674]; reciprocal partial sum already 0.826893051421. Numerical tail gives ≈0.826893, not 1; telescoping was misapplied.
- **#400 — REJECT:** g2(24)=2 and g2(11)=3. **Why:** Exact exhaustive factorial-divisibility check gives g2(24)=3 at (4, 23) and g2(11)=2 at (6, 7).
- **#1038 — REJECT:** f=(x^2-1)/2 is monic and yields measure 2sqrt3. **Why:** Leading coefficient is 1/2, so the polynomial is not admissible. The Gold Report’s flagship counterexample fails the canonical hypothesis.
- **#168 — REJECT:** F(42)=30. **Why:** Explicit independently generated 34-element subset of [42] avoids every {n,2n,3n}; therefore F(42)>=34 and 30 is impossible.
- **#373 — REJECT:** (a!)! = (a!-1)! a! gives infinite canonical family. **Why:** To realize the identity one needs a1=a!-1, which equals n-1 and violates the strict hypothesis n-1>a1.
- **#740 — REJECT:** K_m is counterexample because its only full-chromatic subgraph is itself. **Why:** A subgraph need not be induced; K_m contains many spanning subgraphs with chromatic number m. The key step is false.
- **#120 — REJECT:** A=R is a counterexample. **Why:** Logic reversed: any proper positive-measure E avoids containing an affine copy of R, so A=R makes the existential witness easy, not impossible.
- **#412 — REJECT:** sigma(6)=6 fixed point. **Why:** sigma(6)=1+2+3+6=12. The campaign confused divisor-sum with aliquot sum. The separate sigma(n)>=n+1 lemma survives.
- **#881 — REJECT:** a particular infinite B whose complement is not a basis refutes an existential-B target. **Why:** Quantifier slip: one bad B cannot refute “there exists an infinite B”.
- **#260 — REJECT/REPAIR:** eventual periodicity of rational binary expansion directly controls support {a_n}, proving irrationality. **Why:** Terms are a_n/2^{a_n}; coefficients cause binary carries. The support argument valid for #247 does not transfer verbatim to #260.
- **#885 — REJECT:** N_i=i*lcm(1..2k) gives {0,...,k-1} subset of every factor-difference set. **Why:** 0 belongs to D(N) only when N is a square; these N_i are not all squares. The displayed construction cannot work as stated.
- **#396 — REJECT:** a prime p in (n/2,n-2] divides n(n-1)(n-2), killing k=2. **Why:** A prime merely lying in that interval does not divide one of n,n-1,n-2 (e.g. n=12,p=7). The proposed proof is invalid even if the conclusion might hold.
- **#1054 — REJECT:** f(p+1)=p for every prime p. **Why:** p=11 gives n=12, but m=6 has divisors 1,2,3,6 whose full sum is 12, so f(12)<=6<11.
- **#653 — REJECT:** a grid/generic configuration with few R-values refutes a lower bound on g(n), which is a maximum. **Why:** A low-value witness gives only a lower-bound datum for a maximum; it cannot upper-bound g(n). Several registry entries reverse the extremal quantifier.
- **#680 — INCOMPLETE:** showcase exceptional set centered on 1,3,7,13,31. **Why:** Exact direct search already finds failures <=1000 at [1, 3, 7, 13, 23, 31, 113, 115]; the report omits 23,113,115.
- **#689 — NUMERIC REPAIR:** sum_{p<=300} 1/p ≈ 2.026. **Why:** Exact rational sum is 2.012855408499; still >2, so the qualitative “counting obstruction vanishes by 300” point survives.

## 6. The stale GOLD-REPORT is not an authority
The archive’s own `GOLD-REPORT-2026-09-01.md` says “2 kernel-certified” and advertises several showcase counterexamples. The current receipts actually contain **135 KERNEL_CHECKED formalizations**, but the report’s three most prominent mathematical showcase claims (#400, #1038, #168) fail direct audit. Treat that report as a historical snapshot, not a truth ledger.

## 7. What the 135 kernel checks really mean
The cable is real, but scope is often tiny. Example: #400 R003/L1 is labeled KERNEL_CHECKED, yet its Lean conclusion is only `check_L1 5 2 = true`; it does **not** prove the universal m,k theorem. #689 proves the exact n=100 arithmetic core. By contrast, #276 R004/L1 really does quantify over every recurrence and every divisor. The CSV inventory records the exact Lean conclusion for every receipt so the semantic gap is visible.

## 8. Recommended kernel order
1. **Promote universal #400 factorial witness** (tiny proof, huge scope upgrade).
2. **Promote #949 q≤5 sum-free forcing** (tiny case proof, replaces 2^24 search).
3. **Promote #289 universal 2-adic parity theorem.**
4. **Promote #412 sigma growth/equality iff prime.**
5. **Promote #313 (2,3,p) divisibility classification.**
6. **Promote C(13,6,3) degree≥8 theorem + bank the 21-block witness.**
7. **Promote #700 semiprime formula** (needs binomial/Lucas/Kummer infrastructure).
8. **Promote #376 digit/carry equivalence** (same number-theory infrastructure).
9. **Keep #247 irrationality as a serious analytic formalization target.**
10. Only after that, revisit the remaining 700+ registry records with the same prove-before-promote filter.

## 9. Attached machine-readable inventories
- `ERDOS_REGISTRY_PROVED_710.csv` — every registry record labeled PROVED, with source path. **Unaudited unless promoted above.**
- `ERDOS_KERNEL_CHECKED_135.csv` — exact conclusion/axioms/backend/source for every checked cable theorem.
- `ERDOS_KERNEL_FAILED_72.csv` — every failed cable attempt and error payload.
- `ERDOS_WITNESS_RECEIPTS_40.csv` — all finite witness verifier receipts and claims.
- `ERDOS_GOLD_PROMOTION_QUEUE.csv` — curated high-confidence queue.
- `ERDOS_QUARANTINE_FALSE_GOLD.csv` — claims caught as false/incomplete/semantically broken.
- `ERDOS_KERNEL_CHECKED_BUNDLE_135.zip` — the checked Lean sources + their cable receipts + index.

## Bottom line
**Yes, this is a gold mine—but the gold is not the raw `PROVED` count.** The real payload is: (i) a 135-item kernel receipt corpus; (ii) several clean universal lemmas whose current receipts certify only toy fragments; (iii) strong finite witnesses/obstructions; and (iv) a valuable adversarial corpus of false-positive proof patterns. The best immediate move is to formalize the compact universal lemmas above, not to rubber-stamp the ledger.