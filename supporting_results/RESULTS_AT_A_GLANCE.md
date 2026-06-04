# Supporting Results at a Glance

This file gives a compact map of the quantitative checks cited in the reviewer responses. It is intentionally brief; the point of this repository is to make the rebuttal additions inspectable, not to reproduce every intermediate analysis output.

## Human Calibration

The initial source-blind human calibration run retained 25 Prolific participants, all of whom completed the survey and passed all three attention checks, yielding 300 participant-question choices across 12 questions.

- Human choices matched the conditioned AI cohort winner more often than the unconditioned AI cohort winner: 112/300 (37.3%) vs 85/300 (28.3%), paired participant-level exact sign-flip p < .05.
- On the 7 questions where the two AI evaluator cohorts disagreed, the split was 57/175 (32.6%) vs 30/175 (17.1%), paired exact sign-flip p < .05.
- This is not treated as evidence of a general conditioned-source preference: participants selected conditioned-source items 129/300 times (43.0%), close to the 132.9/300 (44.3%) expected from random choice within question given the option mix.
- Human interparticipant agreement was moderate: mean modal-choice share 51.3%, observed pairwise agreement 38.1% vs a 29.4% uniform-choice baseline.

See `figures/F1_human_calibration.png`, `human_calibration/HUMAN_PREFERENCE_STATS.md`, and `human_calibration/HUMAN_AGREEMENT_NOISE.md`.

## Statistical Validation

To address concerns about parametric chi-square assumptions, we ran block-style permutation tests that preserve each model's item count within each question while breaking the model-to-concept association.

- Exact-string permutation: 8/18 questions significant at p < .001.
- Codebook-cluster permutation: 18/18 questions significant at p < .001.

The camera-ready inferential wording will rely on the codebook-level permutation because that is the granularity used by the main CHOIR salience, RBO, and signal-to-chance analyses. The exact-string result is treated as a conservative companion.

## Recoverability Baselines

For the nearest-centroid recoverability analysis in the 9-model post-replacement corpus:

- Model identity accuracy: 83.6%, 95% bootstrap CI [79.7%, 87.2%], compared with 11.1% chance.
- Persona identity accuracy: 11.0%, 95% bootstrap CI [7.8%, 14.6%], below the naive five-persona chance level of 20%.
- Persona identity is nevertheless above a model-preserving permutation baseline: null mean 3.3%, upper-tail p about .001.

The interpretation is that the classifier is dominated by model identity but contains detectable persona signal relative to a null that preserves model structure.

See `supporting_results/PER_MODEL_RECOVERABILITY.md` for the per-model table, including the Claude/GPT-4.1 cases where persona labels are not recoverable under this classifier.

## Vocabulary Leakage

We treat profile leakage as measurable rather than dismissing it:

- Token overlap rises from 0.479 unconditioned to 0.571 conditioned.
- Nearest-profile-sentence embedding similarity rises from 0.330 to 0.371.
- Across the 13 conditioned questions, profile-output similarity does not track the largest conditioning effects: Spearman rho = -0.24.
- Two counterexamples illustrate this: Q_CTRL has low profile similarity but a high conditioning multiplier, while Q6c has high profile similarity but a low multiplier.

The stripped sensitivity check supports cautious wording: profile-proximate concepts carry some persona-surface signal, but the strong model-signature result is not explained by those concepts.

## Model Replacement

The rebuttal-facing corpus treats OLMo/Sarvam as a full model replacement rather than a partial deletion. Gemma 4 31B and Qwen 3.6 27B fill the intended open-weight, mid-parameter design slot. The analyses cited in the responses use the resulting 9-model post-replacement corpus.

See `supporting_results/POST_REPLACEMENT_RESULTS.md` for the compact signal-to-chance, leave-one-model-out, and absolute-RBO tables that will be included in the camera-ready appendix.

## Within-Domain Heterogeneity

Domain-level summaries are treated as organisational rather than inferential because several domains contain only a small number of questions. See `supporting_results/WITHIN_DOMAIN_HETEROGENEITY.md` for per-domain ranges and per-question values.
