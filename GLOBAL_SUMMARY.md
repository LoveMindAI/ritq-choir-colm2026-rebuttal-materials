# Global Summary

These materials support the rebuttal for COLM 2026 Submission #3577. The reviewer concerns clustered around four themes: method visibility, LLM-judge circularity, leakage/mechanism claims, and statistical baselines. The files here collect the targeted additions prepared in response.

The question bank should be read as the study's instrument, not as the paper's central claim. The questions were chosen because they were useful probes for open-ended model behaviour. The contribution under discussion is CHOIR's free-list elicitation and analysis method: repeated ranked-list elicitation, concept extraction, codebook clustering, salience profiles, and cross-model consensus diagnostics.

## What We Added for Inspectability

The methods materials make the CHOIR pipeline directly readable:

- `methods/CHOIR_METHODS_APPENDIX.md` gives the pipeline steps, core algorithm, prompt templates, extraction rule, worked example, and question-domain coverage.
- `methods/QUESTION_BANK.md` lists the core question stems, prompt perturbations, domains, and design rationales.
- `methods/EXTRACTION_PROMPT_AND_WORKED_EXAMPLE.md` gives the extractor prompt and a raw-response-to-codebook example.

## What We Added for the LLM-Ranking Concern

The submitted ranking study used LLM evaluators, so the rebuttal narrows the claim and adds source-blind human calibration:

- `figures/F1_human_calibration.png` shows human alignment with conditioned vs unconditioned AI cohort winners, with 95% participant-bootstrap confidence intervals and paired-test significance stars.
- `human_calibration/HUMAN_PREFERENCE_STATS.md` summarises the 25-participant Prolific run.

The human result is not framed as proof of a general human preference for conditioned-source outputs. It is framed as partial calibration of the LLM-ranking signal.

## What We Added for Leakage and Mechanism Concerns

The rebuttal treats profile leakage as measurable rather than dismissing it:

- `supporting_results/RESULTS_AT_A_GLANCE.md` summarises the leakage checks, including the profile-overlap increase and the finding that leakage does not track the largest conditioning effects.
- The response narrows mechanism language from a causal/mechanistic claim to a behavioural interpretation with alternatives listed.

## What We Added for Statistical Validation

The rebuttal adds nonparametric checks and clearer baselines:

- `supporting_results/RESULTS_AT_A_GLANCE.md` summarises the codebook-level and exact-string permutation tests, recoverability CIs/nulls, and absolute-RBO interpretation.

## What We Added for the Model-Exclusion Concern

The rebuttal-facing corpus treats OLMo/Sarvam as a full model replacement rather than a partial deletion:

- `supporting_results/RESULTS_AT_A_GLANCE.md` summarises the replacement framing.

## What We Added for Question-Inventory and Related-Work Concerns

Reviewer comments also asked whether CHOIR depended too heavily on the paper's own question inventory and how the work relates to recent homogeneity/diversity papers. In response, we ran a curated external prompt-bank check on Infinity-Chat 100, the representative prompt set used by Jiang et al. in *Artificial Hivemind: The Open-Ended Homogeneity of Language Models (and Beyond)*.

- `external_infinity_chat_100/README.md` gives the scope and headline interpretation.
- `external_infinity_chat_100/DESIGN_MANIFEST.md` summarises the model ensemble, generation design, and run scale.
- `external_infinity_chat_100/width_taxonomy/` gives the prompt-width taxonomy and prompt-echo quicklook.
- `external_infinity_chat_100/parity_analysis/` gives codebook permutation, recoverability, leakage, and sensitivity summaries.
- `external_infinity_chat_100/contest_subset/` gives the targeted 12-prompt ranking result.
- `external_infinity_chat_100/taxonomy_alignment/` compares the paper's diagnostic prompts and Infinity-Chat 100 prompts under the published taxonomy.
- `external_infinity_chat_100/anchoring_probe/` gives the six-pair original-versus-cue-stripped prompt-anchoring probe.

This external packet is not intended to replace the submitted corpus. It supports the narrower framing that CHOIR is a portable elicitation and concept-salience method, while the paper's question inventory is a study instrument rather than a canonical benchmark.

## Reviewer Reply Files

The complete response set is in `rebuttal_responses/ALL_REBUTTAL_RESPONSES.md`. Individual replies are also broken out into reviewer-tagged files:

- `rebuttal_responses/reviewer-WTXz.md`
- `rebuttal_responses/reviewer-X6uu.md`
- `rebuttal_responses/reviewer-8irx.md`
- `rebuttal_responses/reviewer-btQW.md`

Additional detail replies are:

- `rebuttal_responses/additional-human-calibration-detail.md`
- `rebuttal_responses/additional-stripped-leakage-detail.md`
