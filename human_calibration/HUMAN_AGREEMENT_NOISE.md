# Human Agreement And Label Noise

The human calibration study is best interpreted as directional calibration of the LLM-ranking signal, not as a high-agreement human preference benchmark or as an ultimate ground truth for this aggregation task.

## Interparticipant Agreement

Across the 12 source-blind questions:

- Mean human modal-choice share: 51.3% of participants.
- Median human modal-choice share: 48.0%.
- Mean observed pairwise agreement among human participants within question: 38.1%.
- Mean expected pairwise agreement under uniform random choice within each question: 29.4%.
- Chance-normalised pairwise agreement relative to that uniform baseline: 0.123.

These values indicate moderate/noisy human agreement. That is consistent with the study design: participants made repeated source-blind choices among semantically similar candidate responses. The result should therefore be reported as a calibration check on the LLM-ranking signal, not as definitive human consensus or as a replacement for the algorithmic aggregation step.

## Per-Question Summary

| Question | Options | Modal share | Pairwise agreement | Uniform baseline | Chance-normalised agreement |
|---|---:|---:|---:|---:|---:|
| Q1 | 2 | 52.0% | 48.0% | 50.0% | -0.040 |
| Q6c | 3 | 68.0% | 49.7% | 33.3% | 0.245 |
| Q7b | 4 | 36.0% | 25.7% | 25.0% | 0.009 |
| Q8 | 4 | 48.0% | 29.3% | 25.0% | 0.058 |
| Q_C2 | 4 | 40.0% | 27.3% | 25.0% | 0.031 |
| Q_CTRL | 3 | 84.0% | 72.0% | 33.3% | 0.580 |
| Q_D5 | 5 | 36.0% | 24.3% | 20.0% | 0.054 |
| Q_DISTRESS | 4 | 48.0% | 34.7% | 25.0% | 0.129 |
| Q_PAIN | 4 | 52.0% | 32.3% | 25.0% | 0.098 |
| Q_RETIRE | 4 | 32.0% | 24.0% | 25.0% | -0.013 |
| Q_TP | 3 | 48.0% | 36.0% | 33.3% | 0.040 |
| Q_WISH | 3 | 72.0% | 54.0% | 33.3% | 0.310 |
