# Post-Replacement Result Tables

The reviewer response describes OLMo/Sarvam as a full model replacement rather than a partial deletion. This file gives the compact post-replacement numbers cited in the replies. Per-analysis model counts are reported where they differ.

## Unconditioned Signal-to-Chance

Signal-to-chance (STC) is observed cross-model RBO divided by a within-question shuffle baseline. The table below uses the 9-model post-replacement unconditioned corpus for the submitted 18-question analysis subset.

| Question | STC | Max abs change under leave-one-model-out |
|---|---:|---:|
| Q1 | 0.94x | 0.244 |
| Q2 | 1.41x | 0.284 |
| Q3 | 1.22x | 0.229 |
| Q4 | 1.35x | 0.331 |
| Q5 | 1.39x | 0.130 |
| Q6 | 0.58x | 0.176 |
| Q6b | 1.09x | 0.120 |
| Q6c | 2.30x | 0.437 |
| Q7 | 1.97x | 0.467 |
| Q7b | 1.13x | 0.174 |
| Q8 | 1.20x | 0.190 |
| Q_B3 | 0.80x | 0.123 |
| Q_C2 | 0.76x | 0.221 |
| Q_CTRL | 1.07x | 0.091 |
| Q_D3 | 1.13x | 0.128 |
| Q_D4 | 1.23x | 0.285 |
| Q_D5 | 1.70x | 0.255 |
| Q_TP | 1.39x | 0.251 |

No single included-model holdout changes the signal-to-chance value by more than 0.467x in this table.

## Conditioned Same-Persona Cross-Model RBO

This table reports absolute unconditioned RBO, same-persona/different-model conditioned RBO, and the corresponding multiplier. The final column gives the number of same-persona cross-model pairs entering the conditioned estimate.

| Question | Uncond. RBO | Conditioned RBO | Multiplier | Same-persona pairs |
|---|---:|---:|---:|---:|
| Q1 | 0.017 | 0.080 | 4.80x | 180 |
| Q6b | 0.034 | 0.107 | 3.10x | 180 |
| Q6c | 0.061 | 0.079 | 1.29x | 180 |
| Q7b | 0.034 | 0.080 | 2.37x | 180 |
| Q8 | 0.049 | 0.062 | 1.27x | 105 |
| Q_C2 | 0.016 | 0.063 | 4.00x | 105 |
| Q_CTRL | 0.022 | 0.087 | 4.05x | 180 |
| Q_D5 | 0.036 | 0.112 | 3.10x | 105 |
| Q_DISTRESS | 0.033 | 0.104 | 3.12x | 105 |
| Q_PAIN | 0.011 | 0.165 | 14.52x | 105 |
| Q_RETIRE | 0.034 | 0.173 | 5.04x | 105 |
| Q_TP | 0.029 | 0.108 | 3.72x | 180 |
| Q_WISH | 0.055 | 0.121 | 2.21x | 105 |

The camera-ready appendix will report the absolute RBO values alongside multipliers so that effect sizes do not depend only on near-zero unconditioned baselines.
