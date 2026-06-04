# CHOIR/RITQ Human Preference Study - Rebuttal Stats

Generated for the COLM 2026 rebuttal response.

## Sample

- Participants retained: 25
- Finished rows: 25
- Passed all attention checks: 25
- Participant-question choices: 300 across 12 questions

## Main Result

Human participants matched the conditioned AI cohort winner more often than the
unconditioned AI cohort winner.

- Conditioned AI cohort winner matches: 112/300 (37.3%)
- Unconditioned AI cohort winner matches: 85/300 (28.3%)
- Paired participant-level difference: mean +1.08 choices per participant; exact sign-flip p = 0.0143

The same difference is concentrated in the 7 questions where the conditioned and
unconditioned AI evaluator cohorts chose different winners:

- Conditioned winner matches: 57/175 (32.6%)
- Unconditioned winner matches: 30/175 (17.1%)
- Participant-level exact sign-flip p = 0.0143

## Important Guardrail

This should not be reported as a general human preference for conditioned-source
items. Participants selected conditioned-source items 129/300
times (43.0%). Because the option sets were not
perfectly balanced by source, random choice within each question would have selected
conditioned-source items 132.9/300
times (44.3%).

The safer interpretation is: human choices partially corroborate the LLM ranking
result by aligning more often with the conditioned AI cohort winner, while also
showing distinct human preferences and no simple unconditional preference for
conditioned-source text.

## Agreement / Label Noise

Human interparticipant agreement was moderate rather than high. Across the 12
questions, the mean human modal-choice share was 51.3%, and observed pairwise
agreement was 38.1% versus a 29.4% uniform-choice baseline. See
`HUMAN_AGREEMENT_NOISE.md` for the per-question table.

## Modal Choices

- Human modal choice matched the conditioned AI cohort winner in 5/12 questions.
- Human modal choice matched the unconditioned AI cohort winner in 2/12 questions.
- AI evaluator cohorts agreed on the winner in 5/12 questions.

Per-question values are summarised in the aggregate counts above and in `human_preference_stats.json`.
