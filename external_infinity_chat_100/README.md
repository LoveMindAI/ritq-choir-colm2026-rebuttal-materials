# External Infinity-Chat 100 CHOIR Packet

This folder contains a curated, reviewer-facing packet for an additional CHOIR run on **Infinity-Chat 100**, the representative prompt set used by Jiang et al. in *Artificial Hivemind: The Open-Ended Homogeneity of Language Models (and Beyond)*.

The purpose is narrow. Several reviewers asked whether CHOIR depends too heavily on the paper's own question inventory and how it should be positioned relative to work on LLM homogeneity and diversity extraction. This external run tests the same CHOIR elicitation and analysis loop on a prompt bank that was not designed for this paper.

## Scope

- Prompts: 100 prompts from the Infinity-Chat 100 evaluation set.
- Models: the 9-model post-replacement ensemble used in the rebuttal-facing analyses.
- Unconditioned CHOIR: Template A and Template B, temperatures 0.3, 0.7, and 1.0, five generations per cell.
- Conditioned extension: five synthetic persona profiles, Template A, temperatures 0.3, 0.7, and 1.0, five generations per cell.
- Extraction: the same fixed Haiku concept-extraction prompt used in the main rebuttal analyses.
- Analysis: per-question concept codebooks, Smith's S salience, rank-biased overlap, signal-to-chance, prompt-width taxonomy, model/persona recoverability, leakage checks, targeted ranking, and a matched prompt-anchoring probe.

The raw generation and extraction tree is intentionally not included here. It is approximately 32 GB locally and would make this reviewer-facing repository harder to inspect. The files here are compact summaries and machine-readable result tables.

## Headline Results

- 100/100 Infinity-Chat prompts were analysed.
- 93/100 prompts showed above-chance unconditioned signal-to-chance.
- Persona-conditioned same-persona convergence increased in 82/100 prompts.
- The width taxonomy separated 13 very-high-width prompts, 28 high-width prompts, 35 middle-width prompts, and 24 narrow/control-like prompts.
- Codebook-level model-cluster permutation tests were significant for 97/97 analysable prompts at p < .05 and 96/97 at p < .001.
- Nearest-centroid recoverability over conditioned cells recovered model identity strongly (0.877 accuracy) and persona identity weakly (0.101 accuracy).
- A targeted 12-prompt ranking subset completed 648/648 evaluator calls; the conditioned evaluator cohort selected conditioned-source buckets in 11/12 prompts and the unconditioned evaluator cohort did so in 8/12.
- A six-pair matched prompt-anchoring probe found that cue stripping lowered item-level and codebook-cluster anchor echo in 6/6 pairs.

## Interpretation

The external run supports the reframed contribution: CHOIR is a portable elicitation and concept-salience method, not a claim that the paper's original question inventory is a canonical benchmark.

The result is not that every open-ended prompt contains large recoverable diversity. Some prompts are genuinely narrow: repeated elicitation mostly returns the same few concepts. Other prompts have wider answer spaces: repeated elicitation recovers broader concept pools, and persona conditioning changes which parts of those pools become salient. This makes prompt width itself a measurable object of analysis.

The run should be read as complementary to *Artificial Hivemind*, not adversarial to it. Their work diagnoses homogeneity under repeated single-response sampling. CHOIR asks what additional stable concept structure becomes visible when models are asked to free-list many responses and those responses are analysed as salience profiles.

## Folder Map

| Folder | Contents |
|---|---|
| `width_taxonomy/` | Prompt-width taxonomy, prompt-echo quicklook, source-taxonomy join, and template/signature quicklook. |
| `parity_analysis/` | Leave-one-model-out sensitivity, codebook permutation tests, recoverability, leakage checks, and stripped-recoverability summaries. |
| `contest_subset/` | Targeted 12-prompt ranking results and the selected question IDs. |
| `taxonomy_alignment/` | Alignment of the paper's diagnostic prompts and Infinity-Chat 100 prompts to the published Artificial Hivemind / Infinity-Chat taxonomy. |
| `anchoring_probe/` | Six matched original-versus-cue-stripped prompt pairs and their echo/RBO/STC results. |

## What This Does Not Claim

This packet does not ask reviewers to re-review a second paper. It does not replace the submitted RITQ corpus. It also does not claim that LLM ranking is a measure of human preference. Its role is to make one point inspectable: the CHOIR method can be applied to an external homogeneity prompt bank, and it reveals a predictable distinction between narrow prompts and prompts with wider, recoverable concept structure.
