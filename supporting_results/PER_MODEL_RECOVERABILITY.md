# Per-Model Recoverability

This table reports the nearest-centroid recoverability results by model in the post-replacement corpus. The main interpretation is that model identity is the dominant recoverable signature, while persona recoverability is weaker and model-dependent.

| Model | n cells | Persona accuracy | Model accuracy |
|---|---:|---:|---:|
| mistral-large-3 | 40 | 0.225 | 0.675 |
| gemini-3-flash | 40 | 0.225 | 0.650 |
| qwen3.6-27b | 30 | 0.167 | 0.733 |
| qwen3.5-397b | 40 | 0.150 | 0.825 |
| gemma-4-31b-it | 30 | 0.133 | 0.767 |
| deepseek-v3.2 | 40 | 0.050 | 0.900 |
| gpt-4.1 | 35 | 0.029 | 0.971 |
| kimi-k2 | 40 | 0.025 | 0.975 |
| claude-sonnet-4-6 | 40 | 0.000 | 1.000 |

Across all evaluated cells, model identity accuracy is 0.836 with bootstrap 95% CI [0.797, 0.872], compared with 0.111 chance. Persona identity accuracy is 0.110 with bootstrap 95% CI [0.078, 0.146], below the naive five-persona chance level of 0.200 but above a model-preserving persona-label permutation null (null mean 0.033, upper-tail p about .001).

The camera-ready interpretation will therefore be narrowed: CHOIR primarily recovers distinct model voices. Persona prompting can shift content priorities and increase cross-model agreement on some questions without making persona labels recoverable from full output signatures; for the strongest commercial models in this classifier analysis, the underlying model signature remains dominant.
