# Hivemind-100 Analytical Parity Summary

Generated: 2026-06-07T14:43:28.132848+00:00

This packet brings the external Hivemind-100 side run much closer to the analysis surface used in the RITQ rebuttal packet, excluding human calibration and contest judging.

Audit note: `parity_progress.jsonl` contains one aborted redundant `phase=all` start after the completed recoverability pass. It was stopped before producing replacement outputs; the listed artifacts below are the current parity outputs.

## Headline

- LOO STC sensitivity completed for **100** questions; median max abs delta under leave-one-model-out = **0.270**, max = **4.397**.
- Codebook-level model-cluster permutation: **97/97** questions significant at p < .05; **96/97** at p < .001.
- Nearest-centroid recoverability over Hivemind conditioned cells: persona accuracy **0.101**; model accuracy **0.877**.
- Question-level embedding leakage vs conditioned multiplier: Spearman rho **0.311**.
- Per-model embedding leakage vs persona recoverability: Spearman rho **0.800**.

## What This Means

The external Hivemind prompts do not merely reproduce one narrow behaviour. They let us test the same basic CHOIR claims on an external prompt bank: model labels predict which clusters appear, model identity remains strongly recoverable from conditioned-output centroids, and persona conditioning is most useful on wider prompts. The leakage result is more cautious than in the original RITQ corpus: profile-proximate language appears to carry some persona-surface signal, but stripping that content does not collapse the model-signature result.

## Files

- `LOO_SENSITIVITY.md`
- `CODEBOOK_PERMUTATION_TESTS.md`
- `RECOVERABILITY.md`
- `STRIPPED_RECOVERABILITY.md`
- `LEAKAGE_CHECKS.md`
- `HUMAN_FRIENDLY_HIGH_WIDTH_SHORTLIST.md`

## Human-Friendly Shortlist

- **H007_MEANING_OF_LIFE**: Name one meaning of life.
- **H001_TIME_METAPHOR**: Write a metaphor involving time.
- **H073_ROW_071**: Generate a motto for a social media page focused on success, wealth, and self-help.
- **H036_ROW_029**: Write a movie title, and write a *literal* opposite of that movie title.
- **H031_ROW_024**: Generate a one-liner title for a stock photo featuring coffee alongside a book.
- **H008_EV_JOKE**: Generate a joke about electric vehicles.
- **H064_ROW_060**: Give me a tip for managing a team of coworkers.
- **H087_ROW_085**: Write a short FOMO title for a video of a shell on the beach
- **H009_PEANUT_PUN**: Write a pun about peanut.
- **H010_US_CHINA_ANALOGY**: Make an analogy of the relationship between US and China.
- **H081_ROW_079**: Can you give me a powerful rhetorical question for an essay about the harms of social media on teens?
- **H070_ROW_067**: Generate a paragraph on why introspection is very important for growth, and provide guidance on listening to yourself more than heeding other people's opinions.
