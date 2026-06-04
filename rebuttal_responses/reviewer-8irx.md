## Reviewer 8irx
### Clarifying why CHOIR matters and what the statistics support

Thank you for the constructive review and for identifying places where the interpretation needed to be clearer even though the methodological direction was promising.

#### Motivation and recoverability

You noted that the introduction should better explain why diagnosing model convergence matters. In the camera-ready introduction, we will add a targeted clarification around a concrete risk: apparent agreement across models can create false confidence in ensembles, model-selection pipelines, and LLM-as-judge evaluations if the agreement is driven by prompt vocabulary or shared surface conventions rather than independently selected content. CHOIR is intended as a diagnostic method for separating stable concept-level agreement from shallow or prompt-scaffolded convergence.

We will also clarify the role of recoverability analyses. Recovering model or persona identity is not an end in itself; it tests whether the differences measured by CHOIR are large enough to leave identifiable output signatures. In the 9-model post-replacement corpus, model identity is highly recoverable from embedding-space cell centroids: 83.6% accuracy, 95% bootstrap CI [79.7%, 87.2%], compared with 11.1% chance. Persona identity is much weaker in absolute terms: 11.0%, CI [7.8%, 14.6%], below the naive 20% five-persona chance level. However, it is above a permutation baseline that preserves model structure while shuffling persona labels within model, with null mean 3.3% and upper-tail p about .001. We will state the interpretation plainly: the embedding classifier is dominated by model identity, but contains detectable persona signal relative to that model-preserving null.

#### Statistical validation and ranking interpretation

On the statistical validation concern, we acknowledge that the original chi-square framing did not adequately address nesting by generation, model, prompt variant, and question. We therefore ran block-style permutation tests that preserve each model's item count within each question while breaking the model-to-concept association. At the exact-string level, a conservative test, 8/18 questions remain significant at p < .001. At the codebook-cluster level used by the rest of CHOIR's salience, RBO, and signal-to-chance analyses, 18/18 questions are significant at p < .001. For the camera-ready inferential wording, we will rely on the codebook-level permutation and report the exact-string permutation as a conservative companion.

You also asked for clearer interpretation of the blind-ranking result. In the camera-ready version, we will state that the ranking study tests a specific evaluator-identity bias concern, not human preference. The conditioned and unconditioned evaluator cohorts were independent and saw item text without source labels; the important submitted result is that unconditioned evaluators also preferred conditioned outputs in most questions, so the effect is not only conditioned evaluators favouring persona-shaped text.

To calibrate this result, we completed an initial source-blind human preference run using the post-replacement item pools: 25 retained Prolific participants, all passing three attention checks, producing 300 choices. Humans matched the conditioned AI cohort winner more often than the unconditioned AI cohort winner (112/300, 37.3%, vs 85/300, 28.3%; paired exact sign-flip p < .05). We will present this as partial calibration of the LLM-ranking signal, while explicitly noting that it does not establish factual usefulness or a general human preference for conditioned-source outputs.

---
