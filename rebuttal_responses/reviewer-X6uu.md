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
