# Design Manifest

This is a compact manifest for the external Infinity-Chat 100 CHOIR run.

## Source Prompt Set

The prompts come from Infinity-Chat 100, the representative 100-prompt evaluation subset used by Jiang et al. in *Artificial Hivemind: The Open-Ended Homogeneity of Language Models (and Beyond)*.

## Model Ensemble

The run used the 9-model post-replacement ensemble used in the rebuttal-facing analyses:

- Claude Sonnet 4.6
- DeepSeek V3.2
- Gemini 3 Flash Preview
- Gemma 4 31B IT
- GPT-4.1
- Kimi K2
- Mistral Large 3
- Qwen 3.5 397B
- Qwen 3.6 27B

## Generation Design

Unconditioned CHOIR:

- Templates: A and B
- Temperatures: 0.3, 0.7, 1.0
- Generations per cell: 5

Conditioned extension:

- Five synthetic persona profiles
- Template A
- Temperatures: 0.3, 0.7, 1.0
- Generations per cell: 5

## Analysis Surface

The analysis uses the same core CHOIR operations described in the methods appendix:

- Haiku concept extraction
- per-question concept codebooks
- Smith's S salience
- rank-biased overlap
- signal-to-chance shuffle baseline
- same-persona conditioned cross-model convergence
- leave-one-model-out sensitivity
- codebook-level model-cluster permutation tests
- nearest-centroid model/persona recoverability
- profile-leakage checks and stripped-recoverability sensitivity
- targeted blind ranking on a 12-prompt subset
- matched prompt-anchoring probe on six original/cue-stripped prompt pairs

## Run Scale

- Planned generation cells: 94,500.
- Successful raw JSON files entering the completed analysis: 92,535.
- Successful extracted files entering the completed analysis: 92,525.
- Extracted item records entering taxonomy: 2,296,848.
- Mapped item records: 2,273,531.
- Analysed prompts: 100/100.

The full raw and extracted artifact tree is not included in this repository because it is too large for a reviewer-facing supplement. The result summaries and compact machine-readable tables are included instead.
