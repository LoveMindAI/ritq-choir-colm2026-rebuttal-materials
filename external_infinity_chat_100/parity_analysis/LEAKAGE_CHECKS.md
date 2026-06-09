# Profile Leakage Checks - Hivemind-100

This repeats the rebuttal-side leakage logic on the external Hivemind-100 corpus.

## Token Overlap

| Persona | Conditioned mean | Unconditioned baseline mean |
|---|---:|---:|
| brick | 0.451 | 0.415 |
| evie | 0.438 | 0.377 |
| mena | 0.490 | 0.423 |
| nimby | 0.510 | 0.462 |
| perse | 0.469 | 0.417 |

## Embedding Leakage

| Persona | n concepts | mean max cosine | median | p90 | pct > .5 |
|---|---:|---:|---:|---:|---:|
| brick | 330181 | 0.272 | 0.261 | 0.367 | 1.5% |
| evie | 328344 | 0.290 | 0.274 | 0.415 | 3.5% |
| mena | 329062 | 0.282 | 0.272 | 0.378 | 1.9% |
| nimby | 328311 | 0.294 | 0.284 | 0.393 | 2.1% |
| perse | 327502 | 0.287 | 0.277 | 0.387 | 2.2% |

## Correlations

Question-level embedding leakage vs conditioned multiplier: Pearson r = **0.444**, Spearman rho = **0.311**.
Question-level token overlap vs conditioned multiplier: Pearson r = **0.304**, Spearman rho = **0.264**.

Per-model embedding leakage vs persona recoverability: Pearson r = **0.830**, Spearman rho = **0.800**.
Per-model token overlap vs persona recoverability: Pearson r = **0.237**, Spearman rho = **0.067**.

Reading: leakage is measurable, and on Hivemind-100 it is more entangled with persona recoverability than it was in the original RITQ rebuttal corpus. The cautious interpretation is that profile-proximate language contributes to persona-surface signal here, while the stripping analysis tests whether the stronger model-signature result collapses when that surface-proximate content is removed.

Companion check: `STRIPPED_WITHIN_MODEL_PERSONA_RECOVERABILITY.md` applies the same stripping to the within-model persona classifier. Accuracy remains above five-way chance after all three cuts (0.318, 0.303, 0.284), so profile-proximate language contributes to but does not exhaust the within-model persona signal.
