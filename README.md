# CHOIR / RITQ COLM 2026 Rebuttal Materials

This repository contains the reviewer-facing materials prepared for COLM 2026 Submission #3577, **"Reach Into The Choir: Free-List Elicitation Uncovers Distinct Model Voices in LLM Ensembles."**

The goal is narrow: make the rebuttal additions inspectable without asking reviewers to parse every intermediate analysis output. The repository includes the prompt inventory, the CHOIR methods appendix, the source-blind human calibration figure, a compact supporting-results summary, an external Infinity-Chat 100 CHOIR packet, and the reviewer-tagged rebuttal replies.

The question bank is not presented as a canonical benchmark or as a claim that these are the uniquely correct questions to ask. The questions are study instruments: they were chosen because they were useful for probing open-ended model behaviour under CHOIR's free-list elicitation method. The methodological contribution is the elicitation and analysis framework, not the particular question set as a universal standard.

## Start Here

- `GLOBAL_SUMMARY.md` gives the one-page map of what changed and why.
- `rebuttal_responses/` contains one combined response file and separate files tagged by reviewer ID.
- `methods/CHOIR_METHODS_APPENDIX.md` is the methods appendix intended for upload/linking.
- `methods/QUESTION_BANK.md` documents the question inventory and prompt templates.
- `figures/F1_human_calibration.png` is the source-blind human calibration figure.
- `supporting_results/RESULTS_AT_A_GLANCE.md` summarises the quantitative checks cited in the responses.
- `supporting_results/POST_REPLACEMENT_RESULTS.md` gives the compact post-replacement result tables.
- `supporting_results/WITHIN_DOMAIN_HETEROGENEITY.md` and `supporting_results/PER_MODEL_RECOVERABILITY.md` give the compact tables for two remaining reviewer concerns.
- `external_infinity_chat_100/README.md` summarises the external prompt-bank run on Infinity-Chat 100.

## Folder Map

| Folder | Contents |
|---|---|
| `rebuttal_responses/` | Individual Markdown replies tagged by reviewer ID, plus one combined response file. |
| `methods/` | CHOIR method appendix, full question bank, and extraction prompt/worked example. |
| `figures/` | Human calibration figure and its plotted statistics. |
| `human_calibration/` | Summary and JSON output for the initial source-blind human preference run. |
| `supporting_results/` | Short summary of the quantitative checks cited in the responses. |
| `external_infinity_chat_100/` | Curated summaries and compact tables for the external Infinity-Chat 100 CHOIR run, targeted contest subset, taxonomy alignment, and prompt-anchoring probe. |

## What Is Not Included

This repository is intentionally small. It does not include the full extraction, embedding, and codebook outputs or working materials. The files here are the reviewer-facing materials needed to evaluate the specific rebuttal additions. The external Infinity-Chat 100 raw generation/extraction tree is also intentionally excluded because it is approximately 32 GB locally; compact result summaries and machine-readable tables are included instead.

## Anonymity

The repository text avoids author-identifying names and filesystem paths. If hosted through an anonymous-linking service, the service should strip or mask the repository owner URL as needed for double-blind review.
