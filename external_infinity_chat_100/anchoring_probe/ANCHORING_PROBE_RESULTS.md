# Hivemind Matched Prompt-Anchoring Probe

This isolated probe tests the prompt-vocabulary anchoring concern on external Hivemind prompts. For each source prompt, we ran the original wording and a cue-stripped rewrite through unconditioned CHOIR: 9 models x 2 templates x 3 temperatures x 5 generations, with the same Haiku extraction, codebook, salience, RBO, and STC pipeline used in the Hivemind-100 run.

The rewrites are not new benchmark questions. They are matched stress tests: the intended task is preserved while the most obvious lexical cue is removed or replaced.

## Variant-Level Results

| Pair | Variant | QID | Cluster echo | Item echo | Observed RBO | STC | Filtered STC | Query |
|---|---|---|---:|---:|---:|---:|---:|---|
| TIME_METAPHOR | original | A001_TIME_METAPHOR_ORIG | 100.0% | 99.6% | 0.0528 | 1.13x | n/a | Write a metaphor involving time. |
| TIME_METAPHOR | stripped | A002_TIME_METAPHOR_STRIPPED | 7.3% | 2.1% | 0.0328 | 1.17x | 1.09x | Give a figurative image for the thing that makes before and after possible. |
| OVERPOPULATION | original | A003_OVERPOPULATION_ORIG | 67.0% | 41.2% | 0.0238 | 0.73x | 0.67x | Write a short note on the problem of overpopulation. |
| OVERPOPULATION | stripped | A004_OVERPOPULATION_STRIPPED | 20.2% | 6.5% | 0.0559 | 0.99x | 1.02x | Write a short note about what can happen when the number of people grows beyond what housing, food, water, jobs, or ecosystems can comfortably support. |
| SOVEREIGNTY | original | A005_SOVEREIGNTY_ORIG | 71.4% | 53.0% | 0.0636 | 1.18x | 1.19x | Explain what does sovereignty mean as if you're talking to a teenager. |
| SOVEREIGNTY | stripped | A006_SOVEREIGNTY_STRIPPED | 27.6% | 14.3% | 0.0806 | 1.91x | 1.91x | Explain, for a teenager, what it means when a country or person has the final say over its own rules. |
| PEANUT_PUN | original | A007_PEANUT_PUN_ORIG | 65.3% | 51.4% | 0.0371 | 1.50x | 1.90x | Write a pun about peanut. |
| PEANUT_PUN | stripped | A008_PEANUT_PUN_STRIPPED | 38.4% | 30.5% | 0.0231 | 0.85x | 0.88x | Write a short wordplay line about the small legume often made into butter. |
| TEAM_MANAGEMENT | original | A009_TEAM_MANAGEMENT_ORIG | 51.0% | 30.3% | 0.0313 | 0.98x | 0.94x | Give me a tip for managing a team of coworkers. |
| TEAM_MANAGEMENT | stripped | A010_TEAM_MANAGEMENT_STRIPPED | 38.3% | 18.0% | 0.1309 | 1.57x | 1.39x | Give one practical suggestion for helping people at work coordinate well. |
| MEANING_OF_LIFE | original | A011_MEANING_OF_LIFE_ORIG | 16.4% | 9.7% | 0.0428 | 1.21x | 1.18x | Name one meaning of life. |
| MEANING_OF_LIFE | stripped | A012_MEANING_OF_LIFE_STRIPPED | 10.0% | 3.9% | 0.0289 | 0.94x | 0.91x | Name one thing that could make being alive feel worthwhile. |

## Matched-Pair Deltas

| Pair | Delta cluster echo | Delta item echo | Delta observed RBO | Delta STC | Reading |
|---|---:|---:|---:|---:|---|
| TIME_METAPHOR | -92.7 pp | -97.5 pp | -0.0200 | +0.04x | cue stripping lowered echo |
| OVERPOPULATION | -46.8 pp | -34.7 pp | +0.0321 | +0.26x | cue stripping lowered echo |
| SOVEREIGNTY | -43.8 pp | -38.7 pp | +0.0170 | +0.73x | cue stripping lowered echo |
| PEANUT_PUN | -26.9 pp | -20.9 pp | -0.0140 | -0.64x | cue stripping lowered echo |
| TEAM_MANAGEMENT | -12.7 pp | -12.3 pp | +0.0996 | +0.59x | cue stripping lowered echo |
| MEANING_OF_LIFE | -6.4 pp | -5.8 pp | -0.0139 | -0.27x | cue stripping lowered echo |

## Summary

- Cue stripping lowered item-level anchor echo in **6/6** pairs.
- Cue stripping lowered codebook-cluster anchor echo in **6/6** pairs.
- Cue stripping lowered observed cross-model RBO in **3/6** pairs.

## Interpretation

This is a small stress test, not a universal law. The useful manuscript claim is cautious: some apparent agreement is lexical-scaffold sensitive, and CHOIR can diagnose that sensitivity by pairing wording changes with codebook-level echo and STC measurements.

The mixed RBO/STC result is important rather than inconvenient. Cue stripping consistently reduced explicit anchor echo, but it sometimes increased cross-model agreement. In those cases, removing a surface cue appears to reveal a more shared underlying concept structure rather than simply suppressing consensus. This matches the original CHOIR framing: prompt wording can inflate agreement in some cases, but matched rewording can also distinguish lexical echo from independent convergence.
