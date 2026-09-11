---
id: leak-guard-false-clean-boolean-outcome
claim: |-
  The leak guard reported a false clean on every boolean-outcome dataset, and could not see logical containment at all
status: validated-observational
tier: silver
reality_score: 0.9
effect: |-
  Number('True') is NaN, so a boolean outcome made outcomeBinary all-NaN, singleFeatureAuc hit its nPos===0 branch and returned the 0.5 sentinel for EVERY feature; the guard then reported passed=true, leakageDroppedCount=0. It cleared a dataset where validated_any is DEFINED as (validated_mhc OR validated_tcell) - single-feature AUC 0.9302 - driving a 0.9357 headline at ledgerTier silver. Second, independent defect: even measuring correctly, containment is invisible to correlation thresholds (0.9302 < SEPARABILITY_AUC 0.995). Added a deterministic-implication check on the 2x2 table. Verified on real data with a pre-registered prediction: flags exactly validated_any (resolves 814 negatives, 86%) and immunogenic (153, 16.2%); does NOT flag validated_mhc (AUC 0.787, no exact implication), is_histone, or ra_specific; suppresses differential (rule resolves only 6 rows, below coverage floor). Verdict on the campaign dataset moved proof_hold/silver/0.637 -> refuted/bronze/0.34.
inputs: |-
  $0, deterministic. Real data, no network, no LLM.
cohort: |-
  (see effect)
receipts: []
open_threads: []
provenance: |-
  (not provided)
---

# The leak guard reported a false clean on every boolean-outcome dataset, and could not see logical containment at all

**Status: validated-observational** · tier `silver` · reality_score 0.9

**Effect / numbers.**

Number('True') is NaN, so a boolean outcome made outcomeBinary all-NaN, singleFeatureAuc hit its nPos===0 branch and returned the 0.5 sentinel for EVERY feature; the guard then reported passed=true, leakageDroppedCount=0. It cleared a dataset where validated_any is DEFINED as (validated_mhc OR validated_tcell) - single-feature AUC 0.9302 - driving a 0.9357 headline at ledgerTier silver. Second, independent defect: even measuring correctly, containment is invisible to correlation thresholds (0.9302 < SEPARABILITY_AUC 0.995). Added a deterministic-implication check on the 2x2 table. Verified on real data with a pre-registered prediction: flags exactly validated_any (resolves 814 negatives, 86%) and immunogenic (153, 16.2%); does NOT flag validated_mhc (AUC 0.787, no exact implication), is_histone, or ra_specific; suppresses differential (rule resolves only 6 rows, below coverage floor). Verdict on the campaign dataset moved proof_hold/silver/0.637 -> refuted/bronze/0.34.


_Ledgered via `oracle/scripts/ledger-finding.ts` ($0 deterministic). Status is receipt-backed; see README.md for the law._
