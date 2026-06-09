# Nearest-Centroid Recoverability - Hivemind-100

Classifier surface: one centroid per `(question, persona, model)` cell, using conditioned Template A outputs.

Cells classified: **4500**
Persona accuracy: **0.101** [95% CI 0.093, 0.110]
Model accuracy: **0.877** [95% CI 0.867, 0.886]

## Persona-Label Permutation Null

Within-model persona-label shuffle null mean: **0.024** [95% null interval 0.013, 0.038]
Observed upper-tail p ~= **0.001**; two-sided p ~= **0.002**.

## Per-Model Recoverability

| Model | n cells | Persona acc | Model acc |
|---|---:|---:|---:|
| gpt-4.1 | 500 | 0.010 | 0.988 |
| claude-sonnet-4-6 | 500 | 0.020 | 0.976 |
| mistral-large-3 | 500 | 0.068 | 0.904 |
| kimi-k2 | 500 | 0.084 | 0.902 |
| deepseek-v3.2 | 500 | 0.098 | 0.894 |
| qwen3.6-27b | 500 | 0.100 | 0.880 |
| gemma-4-31b-it | 500 | 0.122 | 0.856 |
| qwen3.5-397b | 500 | 0.174 | 0.798 |
| gemini-3-flash | 500 | 0.236 | 0.694 |

Reading: as in RITQ, the centroid classifier strongly recovers model identity. Persona identity is weaker and should be read relative to the model-preserving permutation null rather than as an unbiased five-way classifier.

## Within-Model Persona Recoverability

The global classifier above is intentionally strict, but it is also dominated by model geometry. As a complementary check, we held model identity fixed and ran a leave-one-question-out persona classifier over the conditioned Infinity-Chat 100 cell centroids.

For each model and held-out question, the classifier predicted the persona label against same-model persona centroids estimated from the other 99 questions.

Overall persona accuracy: **0.323** [95% bootstrap CI 0.309, 0.337] against five-way chance of **0.200**.

| Model | Accuracy |
|---|---:|
| claude-sonnet-4-6 | 0.294 |
| deepseek-v3.2 | 0.350 |
| gemini-3-flash | 0.398 |
| gemma-4-31b-it | 0.298 |
| gpt-4.1 | 0.260 |
| kimi-k2 | 0.322 |
| mistral-large-3 | 0.318 |
| qwen3.5-397b | 0.368 |
| qwen3.6-27b | 0.302 |

Reading: persona information is present once model identity is held fixed, but the stronger organizing signature remains model identity. This supports the paper's bounded interpretation of persona conditioning as a salience-shifting intervention rather than evidence that profile prompts overwrite base-model voice.
