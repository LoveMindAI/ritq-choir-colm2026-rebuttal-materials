# Leakage-Stripped Within-Model Persona Recoverability - Hivemind-100

Classifier surface: conditioned Template A cell centroids for `(question, model, persona)`. For each threshold, profile-proximate items are removed before recomputing cell centroids. The classifier then holds model identity fixed and predicts persona labels using leave-one-question-out same-model persona centroids.

| Threshold | Frac concepts kept | n cells | Accuracy [95% CI] | Delta vs no strip |
|---|---:|---:|---:|---:|
| no strip | 1.000 | 4500 | 0.323 [0.310, 0.337] | +0.000 |
| < 0.5 | 0.978 | 4500 | 0.318 [0.305, 0.332] | -0.005 |
| < 0.4 | 0.916 | 4500 | 0.303 [0.290, 0.316] | -0.020 |
| < 0.3 | 0.634 | 4469 | 0.284 [0.271, 0.297] | -0.039 |

Reading: the within-model persona signal remains above the five-way chance baseline after removing profile-proximate concepts. The effect weakens as stripping becomes more severe, so the safest interpretation is that profile-adjacent vocabulary contributes to persona recoverability but does not fully explain it.

## Per-Model Accuracy

| Model | no strip | < 0.5 | < 0.4 | < 0.3 |
|---|---:|---:|---:|---:|
| claude-sonnet-4-6 | 0.294 | 0.298 | 0.286 | 0.250 |
| deepseek-v3.2 | 0.350 | 0.334 | 0.312 | 0.291 |
| gemini-3-flash | 0.398 | 0.386 | 0.354 | 0.331 |
| gemma-4-31b-it | 0.298 | 0.304 | 0.300 | 0.294 |
| gpt-4.1 | 0.260 | 0.260 | 0.250 | 0.240 |
| kimi-k2 | 0.322 | 0.322 | 0.310 | 0.288 |
| mistral-large-3 | 0.318 | 0.316 | 0.300 | 0.288 |
| qwen3.5-397b | 0.368 | 0.350 | 0.330 | 0.310 |
| qwen3.6-27b | 0.302 | 0.296 | 0.286 | 0.264 |
