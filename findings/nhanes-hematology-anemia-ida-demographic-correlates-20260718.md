---
id: nhanes-hematology-anemia-ida-demographic-correlates-20260718
claim: |-
  Real anemia and iron-deficiency-anemia (IDA) classification in NHANES reproductive-age women: 12.6% anemia prevalence, 62.6% IDA share, real age/poverty correlates of iron status, MCV-confirmed subtype validity
status: validated-observational
tier: bronze
reality_score: 0.5
domain: hematology
effect: |-
  Primary population (women 18-49, non-pregnant, pooled across 5 NHANES cycles with real ferritin data -- the CDC/WHO standard IDA-surveillance population): n=6435 complete-case, anemic (WHO Hgb<12.0 g/dL) n=813 (12.63 percent -- matches published US national anemia prevalence in reproductive-age women). Among anemic women, IDA (ferritin<15 ng/mL) n=509 (62.6 percent) vs non-IDA anemia (NIDA) n=304 (37.4 percent) -- matches published literature that iron deficiency is the leading cause of anemia in this population. driver_screen_run (log_ferritin outcome, age+PIR drivers, race-adjusted, BH-FDR+3-kill refutation): age adj_partial_r=0.1057 adj_p=1.89e-17 (refutation-confirmed, permutation_p=0.0005); poverty-income-ratio (PIR) adj_partial_r=0.0392 adj_p=0.00165 (refutation-confirmed, permutation_p=0.001) -- both real, independent correlates of iron status. Secondary check on 2017-2018 (the one cycle with an unrestricted full adult sample, both sexes 18-80): sex adj_partial_r=-0.4184 adj_p~1e-189 (refutation-confirmed) -- women have dramatically lower ferritin than men, as expected; age and PIR replicate in the same direction. stratification_run (PIR/poverty quintiles -> population IDA prevalence, age+race-adjusted): a real, statistically significant linear poverty gradient (Cochran-Armitage z=2.61, one-sided rising p=0.0045 when scored as poverty) but NOT a clean monotone dose-response (rate dips in the single poorest quintile) and the top/bottom risk ratio (1.31x) 95pct CI [0.98,1.74] crosses 1 -- the blade's strict promotion gate correctly withholds a 'big gradient' certification even though the underlying linear trend is real, an honest partial result, not a clean win. adjusted_effect_run internal validity check: among anemic women, IDA cases have real, large, age/race-adjusted lower MCV than NIDA cases (crude d=-0.7688, adjusted d=-0.7712, attenuation=-0.3 percent, band=robust, group_beta=-6.39 fL) -- independently confirms the ferritin-based subtype labels are biologically real (IDA cases really are microcytic). adjusted_effect_run on PIR within the anemic-only subset: NO real difference in poverty between IDA and NIDA cases (crude d=-0.057, adjusted d=-0.055, band=null_after_adjustment) -- an honest negative: poverty predicts BECOMING iron-deficient-anemic at the population level but does not further distinguish anemia SUBTYPE once a woman is already anemic. REAL METHODOLOGICAL FINDING along the way: cycles 2005-2006/2007-2008/2009-2010/2015-2016 measure ferritin ONLY in non-pregnant women 18-49 (a real NHANES iron-surveillance subsample design, confirmed empirically by age/sex composition, not assumed); only 2017-2018 sampled the full adult population. Naively pooling all 5 cycles would have confounded subsample design with demographic correlates (a Simpson's-paradox trap caught before any blade ran) -- this drove the two-frame analytic design (women-18-49 pooled cohort + 2017-2018-only full-population check) used throughout.
inputs: |-
  B2 bucket oracle-data-corpus, datasets/nhanes/{2005-2006,2007-2008,2009-2010,2015-2016,2017-2018}/{demographics,laboratory}/ (DEMO, CBC, FERTIN parquet files), streamed live via the existing _b2() connector (oracle/data_engine/data_catalog.py). Confirmed by direct B2 schema/listing check (not assumed) that 2011-2012/2013-2014 lack FERTIN and were correctly excluded. $0 deterministic pandas/numpy + statsmodels/scipy-backed Oracle blades (driver_screen_run, stratification_run, adjusted_effect_run). No LLM, no network beyond the already-provisioned B2 bucket.
cohort: |-
  NHANES adults age>=18, pregnant-at-exam excluded (RIDEXPRG==1), complete-case on age/sex/poverty-income-ratio/race-ethnicity(RIDRETH1 dummies) + valid hemoglobin + valid ferritin. Anemia: WHO 2011 non-pregnant-adult Hgb thresholds (male<13.0, female<12.0 g/dL). IDA subtype: anemic & ferritin<15 ng/mL (WHO adult absolute iron-deficiency threshold, NOT inflammation-adjusted -- hs-CRP unavailable across all 5 cycles, a documented limitation expected to UNDERESTIMATE true iron deficiency in anemic adults with concurrent inflammation). Two comparability-correct analytic frames used after discovering the real ferritin-subsample design difference across cycles: (1) women 18-49 pooled across all 5 cycles n=6435 (primary), (2) 2017-2018 only n=4492 both sexes ages 18-80 (sex-effect check).
receipts:
  - oracle/scientific_os/nhanes_hematology_iron_deficiency_anemia_cohort.py
  - oracle/runtime/cache/nhanes/hematology-ida-cohort.receipt.json
  - oracle/runtime/cache/nhanes/hematology-ida-women1849-cohort.csv
  - oracle/runtime/cache/nhanes/hematology-ida-women1849-anemic-subset-cohort.csv
  - oracle/runtime/cache/nhanes/hematology-ida-cycle2017-2018-full-cohort.csv
  - oracle/runtime/cache/nhanes/hematology-driver-screen-women1849-result.json
  - oracle/runtime/cache/nhanes/hematology-driver-screen-cyclej-result.json
  - oracle/runtime/cache/nhanes/hematology-stratification-women1849-poverty-ida-result.json
  - oracle/runtime/cache/nhanes/hematology-adjeffect-women1849anemic-mcv-result.json
  - oracle/runtime/cache/nhanes/hematology-adjeffect-women1849anemic-pir-result.json
blades: |-
  oracle/reality/sensors/causal_epi/driver_screen_run.py (covariate_adjusted_partial_correlation_driver_screen_bh_fdr_plus_refutation) + oracle/reality/sensors/causal_epi/stratification_run.py (ordinal_quintile_stratification_cochran_armitage_trend_top_bottom_rr) + oracle/reality/sensors/causal_epi/adjusted_effect_run.py (general_covariate_adjusted_cohen_d), all pre-existing, self-validating (--selftest/--validate with RED mutations) armory blades, driven via their bridges with JSON specs -- not hand-rolled statistics
open_threads:
  - {blade: iron_panel_full_fetib, value: med, data: partial, cost: med, why: "Only 2 of 5 cycles (2005-2006, 2017-2018) also carry FETIB (TIBC/transferrin saturation) -- a second independent iron marker could cross-validate the ferritin-only IDA label if pooled across just those 2 cycles."}
  - {blade: inflammation_adjustment, value: med, data: needs-acquire, cost: med, why: "hs-CRP is not consistently available across all 5 cycles -- an inflammation-corrected ferritin threshold (e.g. BRINDA adjustment) would tighten the IDA label but needs a same-cycle CRP source."}
provenance: |-
  session 2026-07-18, hematology campaign -- genuinely new disease domain (real blood-disorder epidemiology: anemia classification + IDA subtyping) distinct from the same-session psychiatric CBC/NLR-inflammation-proxy campaign. $0 deterministic pandas/numpy/statsmodels/scipy only, real B2-streamed NHANES data, no LLM.
domain_lane: biomedical
domain_lane_source: domain-exact
---

# Real anemia and iron-deficiency-anemia (IDA) classification in NHANES reproductive-age women: 12.6% anemia prevalence, 62.6% IDA share, real age/poverty correlates of iron status, MCV-confirmed subtype validity

**Status: validated-observational** · tier `bronze` · reality_score 0.5 · domain hematology

**Effect / numbers.**

Primary population (women 18-49, non-pregnant, pooled across 5 NHANES cycles with real ferritin data -- the CDC/WHO standard IDA-surveillance population): n=6435 complete-case, anemic (WHO Hgb<12.0 g/dL) n=813 (12.63 percent -- matches published US national anemia prevalence in reproductive-age women). Among anemic women, IDA (ferritin<15 ng/mL) n=509 (62.6 percent) vs non-IDA anemia (NIDA) n=304 (37.4 percent) -- matches published literature that iron deficiency is the leading cause of anemia in this population. driver_screen_run (log_ferritin outcome, age+PIR drivers, race-adjusted, BH-FDR+3-kill refutation): age adj_partial_r=0.1057 adj_p=1.89e-17 (refutation-confirmed, permutation_p=0.0005); poverty-income-ratio (PIR) adj_partial_r=0.0392 adj_p=0.00165 (refutation-confirmed, permutation_p=0.001) -- both real, independent correlates of iron status. Secondary check on 2017-2018 (the one cycle with an unrestricted full adult sample, both sexes 18-80): sex adj_partial_r=-0.4184 adj_p~1e-189 (refutation-confirmed) -- women have dramatically lower ferritin than men, as expected; age and PIR replicate in the same direction. stratification_run (PIR/poverty quintiles -> population IDA prevalence, age+race-adjusted): a real, statistically significant linear poverty gradient (Cochran-Armitage z=2.61, one-sided rising p=0.0045 when scored as poverty) but NOT a clean monotone dose-response (rate dips in the single poorest quintile) and the top/bottom risk ratio (1.31x) 95pct CI [0.98,1.74] crosses 1 -- the blade's strict promotion gate correctly withholds a 'big gradient' certification even though the underlying linear trend is real, an honest partial result, not a clean win. adjusted_effect_run internal validity check: among anemic women, IDA cases have real, large, age/race-adjusted lower MCV than NIDA cases (crude d=-0.7688, adjusted d=-0.7712, attenuation=-0.3 percent, band=robust, group_beta=-6.39 fL) -- independently confirms the ferritin-based subtype labels are biologically real (IDA cases really are microcytic). adjusted_effect_run on PIR within the anemic-only subset: NO real difference in poverty between IDA and NIDA cases (crude d=-0.057, adjusted d=-0.055, band=null_after_adjustment) -- an honest negative: poverty predicts BECOMING iron-deficient-anemic at the population level but does not further distinguish anemia SUBTYPE once a woman is already anemic. REAL METHODOLOGICAL FINDING along the way: cycles 2005-2006/2007-2008/2009-2010/2015-2016 measure ferritin ONLY in non-pregnant women 18-49 (a real NHANES iron-surveillance subsample design, confirmed empirically by age/sex composition, not assumed); only 2017-2018 sampled the full adult population. Naively pooling all 5 cycles would have confounded subsample design with demographic correlates (a Simpson's-paradox trap caught before any blade ran) -- this drove the two-frame analytic design (women-18-49 pooled cohort + 2017-2018-only full-population check) used throughout.

**Inputs.**

B2 bucket oracle-data-corpus, datasets/nhanes/{2005-2006,2007-2008,2009-2010,2015-2016,2017-2018}/{demographics,laboratory}/ (DEMO, CBC, FERTIN parquet files), streamed live via the existing _b2() connector (oracle/data_engine/data_catalog.py). Confirmed by direct B2 schema/listing check (not assumed) that 2011-2012/2013-2014 lack FERTIN and were correctly excluded. $0 deterministic pandas/numpy + statsmodels/scipy-backed Oracle blades (driver_screen_run, stratification_run, adjusted_effect_run). No LLM, no network beyond the already-provisioned B2 bucket.

**Cohort.**

NHANES adults age>=18, pregnant-at-exam excluded (RIDEXPRG==1), complete-case on age/sex/poverty-income-ratio/race-ethnicity(RIDRETH1 dummies) + valid hemoglobin + valid ferritin. Anemia: WHO 2011 non-pregnant-adult Hgb thresholds (male<13.0, female<12.0 g/dL). IDA subtype: anemic & ferritin<15 ng/mL (WHO adult absolute iron-deficiency threshold, NOT inflammation-adjusted -- hs-CRP unavailable across all 5 cycles, a documented limitation expected to UNDERESTIMATE true iron deficiency in anemic adults with concurrent inflammation). Two comparability-correct analytic frames used after discovering the real ferritin-subsample design difference across cycles: (1) women 18-49 pooled across all 5 cycles n=6435 (primary), (2) 2017-2018 only n=4492 both sexes ages 18-80 (sex-effect check).

**Receipts.**

- `oracle/scientific_os/nhanes_hematology_iron_deficiency_anemia_cohort.py`
- `oracle/runtime/cache/nhanes/hematology-ida-cohort.receipt.json`
- `oracle/runtime/cache/nhanes/hematology-ida-women1849-cohort.csv`
- `oracle/runtime/cache/nhanes/hematology-ida-women1849-anemic-subset-cohort.csv`
- `oracle/runtime/cache/nhanes/hematology-ida-cycle2017-2018-full-cohort.csv`
- `oracle/runtime/cache/nhanes/hematology-driver-screen-women1849-result.json`
- `oracle/runtime/cache/nhanes/hematology-driver-screen-cyclej-result.json`
- `oracle/runtime/cache/nhanes/hematology-stratification-women1849-poverty-ida-result.json`
- `oracle/runtime/cache/nhanes/hematology-adjeffect-women1849anemic-mcv-result.json`
- `oracle/runtime/cache/nhanes/hematology-adjeffect-women1849anemic-pir-result.json`

**Blades.**

oracle/reality/sensors/causal_epi/driver_screen_run.py (covariate_adjusted_partial_correlation_driver_screen_bh_fdr_plus_refutation) + oracle/reality/sensors/causal_epi/stratification_run.py (ordinal_quintile_stratification_cochran_armitage_trend_top_bottom_rr) + oracle/reality/sensors/causal_epi/adjusted_effect_run.py (general_covariate_adjusted_cohen_d), all pre-existing, self-validating (--selftest/--validate with RED mutations) armory blades, driven via their bridges with JSON specs -- not hand-rolled statistics

**Open threads (next blades).**

- **iron_panel_full_fetib** (value med · data partial · cost med) — Only 2 of 5 cycles (2005-2006, 2017-2018) also carry FETIB (TIBC/transferrin saturation) -- a second independent iron marker could cross-validate the ferritin-only IDA label if pooled across just those 2 cycles.
- **inflammation_adjustment** (value med · data needs-acquire · cost med) — hs-CRP is not consistently available across all 5 cycles -- an inflammation-corrected ferritin threshold (e.g. BRINDA adjustment) would tighten the IDA label but needs a same-cycle CRP source.

**Provenance.**

session 2026-07-18, hematology campaign -- genuinely new disease domain (real blood-disorder epidemiology: anemia classification + IDA subtyping) distinct from the same-session psychiatric CBC/NLR-inflammation-proxy campaign. $0 deterministic pandas/numpy/statsmodels/scipy only, real B2-streamed NHANES data, no LLM.


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
