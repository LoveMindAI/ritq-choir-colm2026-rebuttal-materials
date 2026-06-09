# Prompt Width / Relative Lift Denominator Audit

Date: 2026-06-09

## Why This Audit Exists

The original prompt-width analysis compared an unconditioned width score against a relative persona-lift ratio. The width score uses unconditioned cross-model RBO, and relative lift is defined as same-persona cross-model RBO divided by unconditioned cross-model RBO. Those two quantities therefore share the same denominator term.

The revised paper keeps the prompt-width taxonomy, but no longer treats relative lift as independent validation of width. It reports absolute unconditioned RBO, absolute same-persona RBO, and relative lift together.

## Key Checks

Observed width score vs relative persona lift:

- Pearson `r = .560`, `p = 1.37e-9`
- Spearman `rho = .712`

Observed width score vs absolute same-persona RBO:

- Pearson `r = -.777`, `p = 2.25e-21`

Residualized relative lift:

- Residualized on unconditioned RBO: Pearson `r = .020`, `p = .841`
- Residualized on unconditioned RBO and number of clusters: Pearson `r = .023`, `p = .821`

Null checks:

- Constant-numerator null correlation: `r = .785`
- Shuffle-numerator denominator-preserving null mean: `r = .645`
- Observed correlation (`r = .560`) is not above the denominator-preserving null.

## Width-Bin Values Used In The Draft

| Width bin | n | STC | Unconditioned RBO | Same-persona RBO | Relative lift | STC > 1 | Lift > 1 |
|---|---:|---:|---:|---:|---:|---:|---:|
| Very high | 13 | 1.11 | .030 | .092 | 3.16 | 9 | 13 |
| High | 28 | 1.38 | .058 | .103 | 1.86 | 26 | 26 |
| Middle | 35 | 1.86 | .134 | .171 | 1.33 | 34 | 31 |
| Low width | 24 | 6.52 | .239 | .223 | .95 | 24 | 12 |

## Revised Interpretation

Prompt width remains useful descriptively because it separates high-baseline narrow prompts from lower-baseline broader prompts. The relative persona-lift ratio is still informative as baseline-normalised behaviour, but it should not be read as an independent correlation between prompt width and absolute persona agreement. The draft has been changed accordingly.
