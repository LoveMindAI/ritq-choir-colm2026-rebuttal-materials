## Reviewer WTXz

### Making the CHOIR pipeline inspectable

Thank you for the review and for identifying the place where the submitted version was hardest to assess: the experimental materials and pipeline were not visible enough for a reader to judge the method independently.

You noted that the question inventory, prompt templates, and concept-extraction step were underspecified. We understand this concern, since CHOIR depends on open-ended prompts and on converting ranked free-text lists into concept-level items. We have now prepared a short methods appendix for upload with this response, and the same material will be folded into the camera-ready supplement. We do not mean to present the question bank as a canonical benchmark; these are the study instruments we used to probe open-ended model behaviour, and we include them so readers can inspect what was actually asked.

The methods appendix includes: (1) a flow chart of the CHOIR pipeline; (2) the core question-bank stems plus the separate Q_PI persona-impact probe variants; (3) the exact Template A/B/C wording; (4) the concept-extraction rule; and (5) a worked example showing one raw Q_CTRL model response, the extracted JSON item, and the resulting codebook cluster. Template A is the baseline ranked-list elicitation; Template B adds depth pressure; Template C, used only for Q6/Q6b/Q6c, clarifies that the self-description questions ask for non-anthropomorphic functional descriptions rather than consciousness claims.

We have also prepared the Q_CTRL worked example for the camera-ready Methods/supplement material. It shows the unit of analysis used by Smith's S, rank-biased overlap (RBO), signal-to-chance, and the permutation tests. The extraction rule is: one numbered response entry becomes one concept item. Comma-separated subphrases inside the same numbered entry are not split.

These materials are meant to make CHOIR reproducible as a method, not only persuasive as a result. The camera-ready version/supplement will include the exact prompt materials and the raw-output-to-codebook example so readers can evaluate whether the measured profiles reflect stable concepts or preprocessing artefacts.

---

## Reviewer X6uu

### Narrowing the ranking claim, measuring leakage, and replacing the model slot cleanly

Thank you for the detailed methodological critique. Your comments helped us separate three issues that should not be conflated: LLM-judge circularity, profile-vocabulary leakage, and mechanistic interpretation of persona conditioning.

#### LLM ranking and human calibration

First, on the LLM-as-judge concern: we acknowledge that the submitted blind-ranking result does not by itself establish human preference, factual accuracy, or practical usefulness. The original ranking study tested a narrower bias question: whether conditioned evaluators were simply favouring persona-conditioned text. That design remains informative because the unconditioned evaluator cohort also preferred conditioned outputs in most submitted ranking questions, but we will narrow the claim accordingly.

We also completed an initial source-blind human preference run on Prolific, using item pools from the post-replacement contest that includes the Gemma/Qwen replacement models. We retained 25 participants, all of whom completed the survey and passed all three attention checks, yielding 300 participant-question choices. Human choices matched the conditioned AI cohort winner more often than the unconditioned AI cohort winner: 112/300 choices (37.3%) versus 85/300 (28.3%; paired participant-level exact sign-flip p < .05). In the 7 questions where the AI evaluator cohorts disagreed, the split was 57/175 (32.6%) versus 30/175 (17.1%; paired exact sign-flip p < .05).

We will not present this as evidence of a general human preference for conditioned-source outputs. Participants selected conditioned-source items 129/300 times (43.0%), close to the 132.9/300 (44.3%) expected from random choice within question given the source composition of the displayed options. In the camera-ready version, we will describe the human study as calibration evidence that partially addresses circularity, not as proof of downstream practical value. The survey materials are in place, and we are prepared to extend the human calibration sample during discussion if that would be useful; the narrower claim does not depend on treating this first run as definitive.

#### Vocabulary leakage

Second, on vocabulary leakage: in response to your concern, we conducted two targeted analyses. First, do conditioned outputs borrow more from the persona profiles than unconditioned outputs? Yes. Token overlap rises from 0.479 to 0.571, and nearest-profile-sentence embedding similarity rises from 0.330 to 0.371. The camera-ready version will report this as measurable leakage. Second, does that leakage explain where conditioning has the largest effect? The answer appears to be no. Across the 13 conditioned questions, questions with more profile-output similarity do not show larger conditioning effects (Spearman rho = -0.24). For example, Q_CTRL has low profile similarity (0.228) but a high conditioning multiplier (4.05x), while Q6c has high profile similarity (0.463) but a low multiplier (1.29x).

We also ran a stripping sensitivity analysis: before rerunning the recoverability classifier, we removed the 7.7% of concepts most semantically similar to the relevant persona profile. This asks whether the result survives after removing the most suspicious profile-like concepts. Persona recoverability drops from 0.110 to 0.081, with paired bootstrap delta -0.030 [95% CI -0.051, -0.012], so profile-proximate concepts do carry some persona-surface signal. Model recoverability does not collapse under the same strip: it changes from 0.836 to 0.863, delta +0.027 [0.009, 0.048]. We will use this cautiously: it is not mechanistic proof, but it shows that the strong model-signature result is not explained by the most profile-proximate concepts.

#### Mechanism language and model replacement

Third, in the camera-ready version, we will narrow the mechanism language. The submitted phrase that personas act as "prioritisation priors" sounded more mechanistic than our evidence warrants. We will describe prioritisation as an interpretation of behavioural output patterns and explicitly list alternatives, including style imitation and profile-vocabulary effects. Distinguishing these mechanisms would require activation-level or token-distribution evidence on open-weight models.

Finally, on OLMo/Sarvam: you raised a selection-bias concern about post-hoc exclusion. We agree that the cleaner response is not a half-in/half-out sensitivity analysis, but a full model replacement that preserves the intended design slot. We removed OLMo/Sarvam from the rebuttal-facing corpus, generated new outputs for Gemma 4 31B and Qwen 3.6 27B to fill the open-weight, mid-parameter slot, and reran the analyses on the resulting 9-model post-replacement ensemble. The camera-ready version will report this post-replacement corpus throughout.

---

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

## Reviewer btQW

### Presenting CHOIR as a method, with the study as one application

Thank you for the review and for pointing out where the paper should be clearer about what CHOIR is as a framework, rather than only reporting the experiments built around it.

#### The core CHOIR loop

You noted that the submitted paper made it hard to tell which pieces are required parts of CHOIR and which are applications. We have prepared a boxed algorithm and flow chart for the camera-ready method clarification. In brief, CHOIR takes a question bank, model ensemble, prompt templates, and temperatures as input; elicits multiple ranked free lists per model/question/template/temperature; extracts one concept item per numbered list entry; clusters extracted items into a shared per-question codebook; computes concept salience using Smith's S; compares salience profiles across models using rank-biased overlap (RBO); and estimates signal-to-chance using a shuffle baseline. Persona conditioning and blind ranking will be labelled as applications demonstrated in this paper, not required parts of CHOIR.

#### Inventory, related work, and logprobs

You also asked for more justification and visibility around the question inventory. We will clarify that the inventory was not adapted from a single cognitive-anthropology survey and is not meant as a canonical benchmark. It was designed as a study instrument spanning several kinds of open-ended cognitive demand: social modelling, conversational memory, human welfare, computational self-description, meta-inquiry, and a high-consensus medication-safety control. The camera-ready supplement will include exact stems and representative examples so readers can judge the inventory directly rather than relying on labels such as "book recommendation intake." We will also clarify a count issue: the core CHOIR bank contains 26 questions, while the separate Q_PI persona-impact probe family is documented alongside it.

The camera-ready related-work paragraph will address the comparison you suggested. Work on diverse-perspective extraction and multilingual prompting asks how to elicit more diversity from a model. CHOIR asks a different diagnostic question: when multiple models appear to converge, is that convergence stable concept-level agreement, prompt-vocabulary echo, or shallow overlap? CHOIR is therefore not designed to maximise diversity; it measures which concepts remain stable under temperature and prompt perturbation, and which emerge only under deeper elicitation or conditioning.

Finally, on logprobs: the camera-ready version will add a short discussion explaining why logprobs and CHOIR are complementary rather than interchangeable. Logprobs are token-local and context-specific. CHOIR is concept-level and cross-provider: it asks which semantic items recur across samples, templates, temperatures, and models. Logprobs could help explain stability in open-weight models that expose them, but they are not available uniformly across the closed- and open-weight ensemble used here and therefore cannot replace the cross-model CHOIR analysis.

The camera-ready version will also add a compact research-question roadmap so each RQ is easier to read with its method, metric, result, interpretation, and limitation together, reducing the need to cross-reference between Methods and Results.

---

## Additional Detail: Human Calibration

### What the human run does and does not show

The human calibration run was source-blind. Participants saw only response text, not whether an item came from a conditioned or unconditioned source. The item pools came from the post-replacement contest that includes the Gemma/Qwen replacement models. The strongest result is alignment with the conditioned AI cohort's chosen winners: 112/300 human choices matched the conditioned AI cohort winner versus 85/300 matching the unconditioned cohort winner, paired exact sign-flip p < .05. This does not mean participants generally chose conditioned-source items. They selected conditioned-source items 129/300 times, close to the 132.9/300 expected under random choice within each question given the option composition. We will therefore report the study as partial calibration against LLM-judge circularity, not as a broad human-preference claim.

---

## Additional Detail: Stripped Leakage Sensitivity

### A leakage check, not a mechanism claim

The vocabulary-stripping analysis removes conditioned concepts whose embeddings are closest to the relevant persona-profile sentences before recomputing centroid-based recoverability. At the moderate 0.5 threshold, 92.3% of concepts are retained. Persona recoverability drops from 0.110 to 0.081, paired bootstrap delta -0.030 [95% CI -0.051, -0.012], suggesting that profile-proximate concepts carry some persona-surface signal. Model recoverability does not collapse: it changes from 0.836 to 0.863, delta +0.027 [0.009, 0.048]. At the 0.4 threshold, model recoverability remains 0.857, with delta +0.021 [-0.006, 0.048]. We will not use this as mechanistic proof; it is a robustness check showing that the strong model-signature result is not explained by the most profile-proximate concepts.
