# Profile-Proximate Stripping Sensitivity - Hivemind-100

For each conditioned item, we compute its maximum embedding cosine to the relevant persona profile sentences. Thresholded runs remove the most profile-proximate items before recomputing cell centroids.

| Threshold | Frac kept | n cells | Persona acc [95% CI] | Model acc [95% CI] | Delta persona vs no strip | Delta model vs no strip |
|---|---:|---:|---:|---:|---:|---:|
| no strip | 1.000 | 4500 | 0.101 [0.093, 0.110] | 0.877 [0.867, 0.886] | +0.000 | +0.000 |
| < 0.5 | 0.978 | 4500 | 0.093 [0.085, 0.102] | 0.885 [0.876, 0.894] | -0.008 | +0.008 |
| < 0.4 | 0.916 | 4500 | 0.079 [0.072, 0.087] | 0.898 [0.889, 0.907] | -0.022 | +0.021 |
| < 0.3 | 0.634 | 4469 | 0.096 [0.088, 0.105] | 0.861 [0.851, 0.872] | -0.000 | -0.020 |

Reading: the cautious claim is whether profile-proximate stripping collapses the model/persona signature. The exact direction of small deltas should not become load-bearing.
