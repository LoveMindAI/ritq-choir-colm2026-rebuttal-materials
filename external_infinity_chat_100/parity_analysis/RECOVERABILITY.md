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
