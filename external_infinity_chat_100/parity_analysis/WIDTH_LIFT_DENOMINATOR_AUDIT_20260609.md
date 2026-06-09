# Prompt Width / Relative Lift Denominator Audit

Date: 2026-06-09

## Why This Audit Exists

The original prompt-width analysis compared an unconditioned width score against a relative persona-lift ratio. The width score uses unconditioned cross-model RBO, and relative lift is defined as same-persona cross-model RBO divided by unconditioned cross-model RBO. Those two quantities therefore share the same denominator term.

The revised paper keeps the prompt-width taxonomy, but no longer treats relative lift as independent validation of width. It reports absolute unconditioned RBO, absolute same-persona RBO, and relative lift together.

Table note: relative lift is averaged per prompt within each width bin. It is not computed as the ratio of the displayed bin-mean same-persona RBO to the displayed bin-mean unconditioned RBO, so small differences between the lift column and the ratio of the two RBO columns are expected. The figure and table use the same `HIVEMIND100_WIDTH_TAXONOMY.csv` artifact and the same bin assignment: top 13, next 28, next 35, and bottom 24 prompts by width score.

## Key Checks

Observed width score vs relative persona lift:

- Pearson `r = .774`, `p = 3.66e-21`
- Spearman `rho = .791`

Observed width score vs absolute same-persona RBO:

- Pearson `r = -.648`, `p = 3.02e-13`

Residualized relative lift:

- Residualized on unconditioned RBO: Pearson `r = .303`, `p = .002`
- Residualized on unconditioned RBO and number of clusters: Pearson `r = .305`, `p = .002`

Null checks:

- Constant-numerator null correlation: `r = .853`
- Shuffle-numerator denominator-preserving null mean: `r = .700` [95% interval `.620`, `.771`]
- Observed correlation (`r = .774`) is only slightly above the denominator-preserving null (`p_upper = .019`), so denominator structure explains much of the association even though the current artifact leaves a modest residual positive relation.

## Width-Bin Values Used In The Draft

| Width bin | n | STC | Unconditioned RBO | Same-persona RBO | Relative lift | STC > 1 | Lift > 1 |
|---|---:|---:|---:|---:|---:|---:|---:|
| Very high | 13 | 1.09 | .031 | .110 | 3.55 | 9 | 13 |
| High | 28 | 1.32 | .057 | .104 | 1.82 | 26 | 27 |
| Middle | 35 | 1.92 | .135 | .163 | 1.22 | 34 | 30 |
| Low width | 24 | 6.52 | .239 | .223 | .95 | 24 | 12 |

## Revised Interpretation

Prompt width remains useful descriptively because it separates high-baseline narrow prompts from lower-baseline broader prompts. The relative persona-lift ratio is still informative as baseline-normalised behaviour, but it should not be read without the absolute RBO columns because denominator structure is a major component of the association. The current artifact also leaves a modest residual association after controlling for unconditioned RBO, so the cautious reading is not that width is meaningless; it is that relative lift alone overstates what width proves. The draft has been changed accordingly.
