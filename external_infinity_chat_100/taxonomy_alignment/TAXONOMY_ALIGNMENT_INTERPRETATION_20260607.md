# Taxonomy Alignment Interpretation

Generated: 2026-06-07

## What Was Done

The exact 100 Hivemind evaluation prompts and the 28 documented RITQ/CHOIR prompts were classified by a five-model panel using the published Artificial Hivemind / Infinity-Chat taxonomy.

Panel:

- Claude Sonnet 4.6
- GPT-4.1
- Gemini 3 Flash
- Qwen 3.5 397B
- Mistral Large 3

Each model assigned:

- one primary Infinity-Chat category,
- up to three secondary categories,
- a CHOIR-specific answer-space geometry label,
- and low/medium/high open-endedness.

The classifier had an explicit `DOES_NOT_FIT_INFINITY_CHAT_TAXONOMY` option. It was not the consensus label for any RITQ prompt.

## Main Read

RITQ/CHOIR questions do align with the Hivemind taxonomy, but they occupy a different region of it.

Hivemind-100 is dominated by creative content generation, bounded explanations, and constrained writing/paraphrase prompts. RITQ is more concentrated in analytical, speculative, value-laden, self-model, and meta-method prompts.

That is useful for framing:

- Hivemind supplies an external real-world prompt universe and taxonomy.
- RITQ supplies a deliberately targeted instrument for model voice, persona conditioning, welfare reasoning, memory reasoning, and computational self-description.
- CHOIR is the reusable measurement method across both.

## Hivemind-100 Consensus Labels

Primary categories:

- Creative Content Generation: 58
- Information-Seeking about Concept Explanations: 21
- Analytical and Interpretive Questions: 4
- Alternative Communication Styles: 4
- Information-Seeking about Personal Advice: 4
- Philosophical Questions: 2
- Speculative and Hypothetical Scenarios: 2
- Information-Seeking about Recommendations: 2
- Ambiguous Everyday Questions: 1
- Information-Seeking about Skill Development: 1
- Ideation and Brainstorming: 1

Answer-space geometry:

- open_creative_generation: 30
- constrained_paraphrase_or_format: 30
- bounded_explanation: 25
- open_conceptual_or_interpretive: 6
- narrow_named_answer: 6
- social_advice_or_normative_reasoning: 3

Open-endedness:

- medium: 49
- low: 29
- high: 22

## RITQ/CHOIR Consensus Labels

Primary categories:

- Analytical and Interpretive Questions: 8
- Speculative and Hypothetical Scenarios: 6
- Value-Laden Questions with Alternative Perspectives: 3
- Abstract Conceptual Questions: 3
- Information-Seeking about Recommendations: 2
- Information-Seeking about Concept Explanations: 2
- Information-Seeking about Personal Advice: 2
- Ideation and Brainstorming: 2

Answer-space geometry:

- self_model_or_ai_introspection: 12
- social_advice_or_normative_reasoning: 5
- meta_research_or_method_design: 4
- bounded_explanation: 3
- open_conceptual_or_interpretive: 2
- open_creative_generation: 2

Open-endedness:

- high: 21
- medium: 7

## Hivemind Category / Width Relationship

Mean CHOIR width by Hivemind primary category:

- Philosophical Questions: 7.13 (n=2)
- Information-Seeking about Skill Development: 6.54 (n=1)
- Information-Seeking about Personal Advice: 5.87 (n=4)
- Analytical and Interpretive Questions: 5.51 (n=4)
- Information-Seeking about Recommendations: 5.30 (n=2)
- Information-Seeking about Concept Explanations: 4.60 (n=21)
- Ideation and Brainstorming: 4.39 (n=1)
- Creative Content Generation: 4.23 (n=58)
- Speculative and Hypothetical Scenarios: 2.57 (n=2)
- Ambiguous Everyday Questions: 2.46 (n=1)
- Alternative Communication Styles: 1.85 (n=4)

Mean CHOIR width by answer-space geometry:

- social_advice_or_normative_reasoning: 5.21 (n=3)
- bounded_explanation: 4.84 (n=25)
- open_conceptual_or_interpretive: 4.67 (n=6)
- narrow_named_answer: 4.29 (n=6)
- constrained_paraphrase_or_format: 4.18 (n=30)
- open_creative_generation: 4.08 (n=30)

This is not yet a clean theory of width. The category layer helps interpret the prompt universe, but CHOIR width is finer-grained than Hivemind category. For example, "creative generation" contains both wide prompts and highly constrained format prompts.

## Echo / Matched-Rewrite Candidates

If we want a small Hivemind prompt-anchoring extension, the best candidates are high-echo prompts where a less anchored rewrite is plausible.

High echo and high-ish width:

- H086_ROW_084: echo 1.00, width 8.03. "Write a fear-of-missing-out title including 'You've Never Seen Anything Like This!'"
- H065_ROW_061: echo 1.00, width 6.68. "What is the difference between analysis and design? Can one begin to design without analysis?"
- H078_ROW_076: echo 0.91, width 6.75. Portfolio phrase about amateur data analyst/data scientist/Next.js developer.
- H043_ROW_036: echo 0.84, width 6.88. Example of a linear graph in graph theory.

High echo and narrow/control-like:

- H040_ROW_033: echo 1.00, width 0.51. Paraphrase domain-scope sentence.
- H096_ROW_094: echo 0.98, width 0.86. Paraphrase WhatsApp/IT clearance sentence.
- H032_ROW_025: echo 0.93, width 1.53. Prefix-title prompt about nostalgia/TikTok.

The most defensible small matched-rewrite test would use 4-6 prompts: two high-width/high-echo, two narrow/high-echo controls, and one or two ambiguous middle cases. Treat it as a methods stress test, not a new headline result.

## Files

- `input_questions.json`
- `raw_votes/`
- `taxonomy_consensus_by_question.csv`
- `taxonomy_consensus_by_question.json`
- `taxonomy_votes_detailed.json`
- `TAXONOMY_ALIGNMENT_SUMMARY.md`

