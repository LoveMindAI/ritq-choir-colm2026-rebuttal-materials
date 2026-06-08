# RITQ / CHOIR Review Discussion to Revised Draft Map

Date: 2026-06-08  
Associated paper: COLM 2026 Submission #3577, *Reach Into The Choir: Free-List Elicitation Uncovers Distinct Model Voices in LLM Ensembles*  
Associated draft in this materials packet: `revised_draft/CHOIR_COLM2026_DISCUSSION_STAGE_REVISED_DRAFT_20260608.pdf`

## Purpose

This document maps the review-discussion concerns to the revised discussion-stage draft and supporting materials. It is intended to make the response to reviewer concerns inspectable without requiring readers to reconstruct the full OpenReview exchange.

The revised draft clarifies the paper's scientific object: CHOIR is a portable free-list elicitation and concept-salience method for measuring the answer space beneath first-pass LLM responses. The RITQ prompts are targeted diagnostic probes. Infinity-Chat 100 is the external prompt bank used to test portability and prompt-width behaviour.

## High-Level Changes

1. **Method/instrument separation.** CHOIR is framed as the method; the RITQ question bank is framed as a diagnostic probe set, not a validated scale or universal inventory.
2. **External prompt-bank spine.** Infinity-Chat 100 is used as an external test bed from recent open-ended homogeneity work; the RITQ probes are retained as a mechanism-isolating diagnostic set.
3. **Research-question structure.** Related Work ends in four explicit research questions; Results and Discussion answer those same questions in order.
4. **Clearer implications.** The Introduction, Discussion, and Conclusion state why the method matters for false plurality, ensemble auditing, prompt-width diagnosis, candidate triage, and rare-but-stable concept discovery.
5. **Narrower persona claim.** Persona conditioning is treated as a salience-shifting intervention, not as evidence that profiles overwrite base-model identity or create new knowledge.
6. **Ranking narrowed to triage.** Source-blind LLM ranking is described as algorithmic candidate filtering for later validation, not as human preference, truth, or practical usefulness.
7. **Improved inspectability.** The appendix includes elicitation templates, RITQ probe stems, Infinity-Chat 100 prompts, extraction rules, a worked raw-to-codebook example, the ranking protocol, and the human calibration summary.
8. **Supporting evidence made findable.** The materials packet includes compact evidence summaries for the external run, prompt anchoring, human calibration, codebook permutation tests, leakage checks, and classifier uncertainty.

## Draft Location Map

| Concern area | Revised draft location | What changed |
|---|---|---|
| Motivation and significance | Abstract; Introduction; Discussion; Conclusion | The draft motivates homogeneity as a false-plurality problem and closes by framing CHOIR as a diagnostic measurement method rather than a single similarity score. |
| Related-work positioning | Related Work: open-ended homogeneity and diversity; log probabilities; free-list elicitation; persona conditioning | CHOIR is positioned inside the homogeneity/diversity literature while distinguishing it from diversity-maximisation methods and token-level log-probability analysis. |
| Explicit research questions | End of Related Work | Four research questions now define prompt width, model/persona signatures, mechanism checks, and candidate triage. |
| CHOIR as framework | Method: The CHOIR algorithm | The draft adds a compact algorithm table: elicit, extract, codebook, score, compare, diagnose. |
| Question inventory status | Method: Prompt banks, study roles, and models; Appendix: Prompt Materials and Question Banks | RITQ probes are explicitly described as diagnostic probes, not a validated scale; exact RITQ and Infinity-Chat prompts are included. |
| Extraction and codebooks | Method: Extraction, codebook construction, and salience; Appendix: Concept extraction unit and worked example; `methods/EXTRACTION_PROMPT_AND_WORKED_EXAMPLE.md` | The draft and supplement document the extraction unit, the worked example, clustering details, and the exact extraction prompt. |
| External portability | Method; Results RQ1; Figure 1; Table 3 | CHOIR is run on all 100 Infinity-Chat seed prompts at full elicitation depth and reports prompt-width results. |
| Persona conditioning scope | Results RQ2; Discussion RQ2 | The draft states that model identity dominates the full output signature while persona prompts shift salience without overwriting model voice. |
| Prompt-vocabulary echo | Results RQ3; Appendix: Additional Diagnostic and Ranking Figures | The draft reports both the targeted RITQ matched cue-word result and an external six-pair cue-stripping extension. |
| Ranking interpretation | Results RQ4; Appendix: Ranking Protocol and Human Calibration | Ranking is reframed as candidate triage and the human calibration is treated cautiously. |
| Limitations | Discussion: Limitations | The draft names the prompt-width heuristic, English-only scope, long persona profiles, small human calibration, and the fact that CHOIR is not a fixed benchmark. |

## Reviewer Concern Map

### Motivation, Implications, Baselines, and Interpretation

**Concern.** The paper needed clearer motivation, broader implications, better explanation of recoverability, clearer interpretation of the blind-ranking result, and stronger statistical baselines.

**Response in the revised draft and materials.**

- The Introduction explains why apparent cross-model agreement can be harmful: it can create false plurality and cognitive smoothing when users believe they are seeing independent perspectives.
- The Discussion states the implication directly: before using LLM agreement for evaluation, ensemble design, or curation, one should ask whether agreement reflects a narrow prompt, lexical cueing, a default attractor, or recoverable deeper alternatives.
- Recoverability is tied to the paper's model-selection and ensemble-design implications: provider diversity is not the same thing as cognitive diversity.
- Ranking is framed as candidate triage for large elicited item pools, with human calibration treated as noisy and appendix-light.
- Statistical validation is supported by:
  - `supporting_results/RESULTS_AT_A_GLANCE.md`
  - `supporting_results/POST_REPLACEMENT_RESULTS.md`
  - `supporting_results/PER_MODEL_RECOVERABILITY.md`
  - `external_infinity_chat_100/parity_analysis/PARITY_ANALYSIS_SUMMARY.md`

**Scope limit.** The draft does not claim that CHOIR validates factual correctness or human usefulness. It claims CHOIR maps elicited concept structure and helps prioritise candidate items for later validation.

### LLM-Judge Circularity, Leakage, Model Replacement, and Persona/Model Tension

**Concern.** The LLM-judge result could be circular; persona effects might be vocabulary leakage; model selection could bias the ensemble; broad domain-level summaries could mask question-level heterogeneity; and the relationship between persona conditioning and model-identifiability results needed reconciliation.

**Response in the revised draft and materials.**

- **LLM-judge circularity.** Ranking is narrowed to candidate triage, not validation. The human calibration appears only as a small directional check: participants more often matched the conditioned AI cohort winner, but conditioned-source selection itself was near within-question chance.
- **Vocabulary leakage.** Persona conditioning is treated as an output-level salience intervention, with leakage and stripping analyses supplied in the supporting materials:
  - `supporting_results/RESULTS_AT_A_GLANCE.md`
  - `external_infinity_chat_100/parity_analysis/LEAKAGE_CHECKS.md`
  - `external_infinity_chat_100/parity_analysis/STRIPPED_RECOVERABILITY.md`
- **Model replacement.** The revised draft reports a clean nine-model corpus including Gemma 4 31B and Qwen 3.6 27B in the intended open-weight design slot. The refreshed claim set is based on this replacement corpus.
- **Question-level heterogeneity.** The draft foregrounds per-question and prompt-width analysis rather than leaning on broad domain averages. Infinity-Chat 100 supplies a larger external prompt universe; RITQ supplies targeted probes.
- **Persona/model tension.** The apparent tension is now the finding: persona prompts shift surfaced content priorities, but the full output signature remains dominated by base model.

**Scope limit.** The paper does not claim a mechanistic account of persona conditioning. It reports behavioural salience shifts and recoverability patterns.

### CHOIR as Framework, Inventory Validity, Related Work, and Communication

**Concern.** The paper needed clearer structure: what CHOIR entails, whether the question inventory is valid or theoretically motivated, how the work relates to diversity extraction, and why the results matter beyond the immediate setup.

**Response in the revised draft and materials.**

- CHOIR is defined as an elicitation-and-analysis method with explicit stages.
- The RITQ inventory is described as a diagnostic probe set, not a new measure or psychometric instrument.
- Infinity-Chat 100 supplies the external prompt-bank test, so the method is not dependent on the paper's own questions.
- Related Work explicitly positions CHOIR relative to homogeneity and diversity-extraction work, including diverse-perspective extraction and multilingual prompting.
- The log-probability comparison clarifies why CHOIR works at concept level rather than as a token-local probability analysis.
- Results and Discussion follow the same research-question structure, so the reader can see question, test, result, and implication in sequence.

**Scope limit.** The paper does not claim that the RITQ inventory is a validated cognitive instrument. It claims CHOIR can be applied to open-ended prompt banks and can reveal which prompts behave as narrow, broad, lexically scaffolded, or persona-sensitive.

### Inspectability of Questions, Templates, and Extraction

**Concern.** The experimental pipeline was difficult to review because the submitted paper did not include full question examples, exact templates, or a concrete concept-extraction description.

**Response in the revised draft and materials.**

- The appendix includes Template A, Template B, and Template C wording.
- The appendix includes a worked extraction example from raw model entry to JSON item to codebook cluster.
- The appendix includes the full targeted RITQ diagnostic probe bank.
- The appendix includes the full Infinity-Chat 100 prompt table with descriptive taxonomy labels.
- The exact extraction prompt and fuller worked example are included at `methods/EXTRACTION_PROMPT_AND_WORKED_EXAMPLE.md`.

**Scope limit.** The PDF appendix keeps the extraction example compact for readability; the exact full extraction prompt is provided in the supplementary methods file.

## Supporting Materials Map

| File | Main purpose | Draft claim it supports |
|---|---|---|
| `revised_draft/CHOIR_COLM2026_DISCUSSION_STAGE_REVISED_DRAFT_20260608.pdf` | Revised discussion-stage paper draft | Main revised manuscript. |
| `methods/EXTRACTION_PROMPT_AND_WORKED_EXAMPLE.md` | Exact extraction prompt and full worked example | Inspectability of concept extraction and codebook construction. |
| `external_infinity_chat_100/README.md` | External 100-prompt CHOIR summary | Infinity-Chat 100 portability and prompt-width framing. |
| `external_infinity_chat_100/width_taxonomy/HIVEMIND100_WIDTH_TAXONOMY.csv` | Prompt-width table | RQ1 prompt-width taxonomy and Figure 1. |
| `external_infinity_chat_100/parity_analysis/PARITY_ANALYSIS_SUMMARY.md` | External parity checks | Recoverability, codebook permutation, LOO sensitivity, leakage summaries for Infinity-Chat 100. |
| `external_infinity_chat_100/taxonomy_alignment/TAXONOMY_ALIGNMENT_INTERPRETATION_20260607.md` | Infinity-Chat/RITQ taxonomy alignment | Why Infinity-Chat and RITQ play different study roles. |
| `external_infinity_chat_100/anchoring_probe/ANCHORING_PROBE_RESULTS.md` | Six original-vs-cue-stripped external prompt pairs | External extension of prompt-vocabulary echo diagnostics. |
| `external_infinity_chat_100/contest_subset/HIVEMIND100_CONTEST_APPROVED12_20260607.md` | Source-blind ranking on 12 external prompts | RQ4 candidate-triage result. |
| `human_calibration/HUMAN_PREFERENCE_STATS.md` | Prolific source-blind calibration | Cautious human calibration of the ranking signal. |
| `supporting_results/RESULTS_AT_A_GLANCE.md` | Compact statistical summary | Main quantitative checks cited in responses. |
| `supporting_results/POST_REPLACEMENT_RESULTS.md` | Post-replacement corpus results | Replacement-corpus claim surface. |
| `supporting_results/PER_MODEL_RECOVERABILITY.md` | Per-model recoverability table | Model/persona recoverability interpretation. |

## Claims Deliberately Not Made

- The RITQ prompt bank is not presented as a validated scale.
- Infinity-Chat 100 is not treated as exhaustive of open-ended prompting.
- Persona prompts are not claimed to create new identities or overwrite base-model signatures.
- LLM ranking is not treated as human preference, factual accuracy, or practical usefulness.
- The human calibration is not presented as a complete solution to LLM-judge circularity.
- The prompt-width score is not presented as a finished benchmark metric.
- No mechanistic claim is made about model activations.

## One-Sentence Trace

The review discussion identified a need for greater inspectability, clearer positioning, narrower claims, and stronger communication of implications; the revised draft responds by separating method from instrument, adding an external Infinity-Chat 100 spine, making prompt and extraction materials inspectable, narrowing persona and ranking claims, and structuring the paper around four explicit diagnostic questions.
