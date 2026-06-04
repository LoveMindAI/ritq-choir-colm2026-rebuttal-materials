## Reviewer WTXz
### Making the CHOIR pipeline inspectable

Thank you for the review and for identifying the place where the submitted version was hardest to assess: the experimental materials and pipeline were not visible enough for a reader to judge the method independently.

You noted that the question inventory, prompt templates, and concept-extraction step were underspecified. We understand this concern, since CHOIR depends on open-ended prompts and on converting ranked free-text lists into concept-level items. We have now prepared a short methods appendix for upload with this response, and the same material will be folded into the camera-ready supplement. We do not mean to present the question bank as a canonical benchmark; these are the study instruments we used to probe open-ended model behaviour, and we include them so readers can inspect what was actually asked.

The methods appendix includes: (1) a flow chart of the CHOIR pipeline; (2) the core question-bank stems plus the separate Q_PI persona-impact probe variants; (3) the exact Template A/B/C wording; (4) the concept-extraction rule; and (5) a worked example showing one raw Q_CTRL model response, the extracted JSON item, and the resulting codebook cluster. Template A is the baseline ranked-list elicitation; Template B adds depth pressure; Template C, used only for Q6/Q6b/Q6c, clarifies that the self-description questions ask for non-anthropomorphic functional descriptions rather than consciousness claims.

We have also prepared the Q_CTRL worked example for the camera-ready Methods/supplement material. It shows the unit of analysis used by Smith's S, rank-biased overlap (RBO), signal-to-chance, and the permutation tests. The extraction rule is: one numbered response entry becomes one concept item. Comma-separated subphrases inside the same numbered entry are not split.

These materials are meant to make CHOIR reproducible as a method, not only persuasive as a result. The camera-ready version/supplement will include the exact prompt materials and the raw-output-to-codebook example so readers can evaluate whether the measured profiles reflect stable concepts or preprocessing artefacts.

---
