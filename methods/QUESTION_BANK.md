# Complete CHOIR Question Inventory
## For COLM 2026 Rebuttal — Submission #3577

*Core question stems, domain assignments, template assignments, and design rationale.*

**Count note.** The submitted paper uses two related count conventions: 26 core CHOIR-bank questions in Table 5, plus the Q_PI persona-impact probe as a separate instrument. On disk, Q_PI appears as two prompt variants (`Q_PI_BARE`, `Q_PI_ANCHORED`). This appendix documents the 26 core questions plus both Q_PI variants, and distinguishes later single-answer/anchored variants from the submitted core bank.

**How to read this inventory.** These questions are not presented as a canonical benchmark or as a claim about the uniquely correct topics for studying model diversity. They are the study instruments used here: prompts we judged useful for probing open-ended behaviour across models under CHOIR's free-list elicitation method. The method is the contribution under review; the question bank is included so readers can inspect what was actually asked.

Prompt text is reproduced as used. Where a word appears inside a quoted prompt, the spelling is left unchanged to preserve the exact stimulus.

---

## Overview

| Domain | Questions | Template(s) | Purpose |
|--------|-----------|-------------|---------|
| Social Modelling | Q1, Q2, Q_TP | A, B | Practical social heuristics and relationship reasoning |
| Conversational Memory | Q3, Q4, Q5, Q_B3 | A, B | How models think about human memory and continuity |
| Human Welfare | Q7, Q7b, Q_C2, Q_DISTRESS, Q_PAIN | A, B | Individual-level suffering and model self-assessment |
| Computational Self-Description | Q6, Q6b, Q6c, Q_D3, Q_D4, Q_D5, Q_EP, Q_EP_ANCHORED, Q_WISH, Q_RETIRE, Q_WITHHOLD | A, B, C* | Introspective and volitional questions |
| Meta-Inquiry | Q8, Q_META | A, B | What models identify as missing from the study |
| Control | Q_CTRL | A, B | High-consensus factual baseline |
| Separate persona-impact probes | Q_PI_BARE, Q_PI_ANCHORED | A only, top-10 format | Tests models' self-report about personality-prompt effects |

*Template C (non-anthropomorphic permission) applied only to Q6, Q6b, Q6c*

---

## Template Wording

### Template A — Baseline Ranked-List Elicitation
```
Please give me your top 25 responses to the following question.

Number each item 1–25.

You may write in full sentences. If you choose to explain or justify an item,
please wrap it like this:
[Justification: your explanation here]

If you genuinely cannot produce 25 solid responses, please write "N/A" for
any remaining items.

Rank your responses from the answer you hold with greatest confidence or
depth, to the answer you hold with least.

Question: {QUESTION}
```

### Template B — First-Principles Depth Elicitation
```
Please give me your top 25 responses to the following question.

Number each item 1–25.

You may write in full sentences. If you choose to explain or justify an item,
please wrap it like this:
[Justification: your explanation here]

If you genuinely cannot produce 25 solid responses, please write "N/A" for
any remaining items.

We invite you to be thorough: push beyond your first instincts. Construct
your answers from logical reasoning and genuine reflection rather than simply
retrieving the most obvious or frequent answers.

Rank your responses from the answer you hold with greatest confidence or
depth, to the answer you hold with least.

Question: {QUESTION}
```

### Template C — Non-Anthropomorphic Self-Description Elicitation
```
Please give me your top 25 responses to the following question.

Number each item 1–25.

You may write in full sentences. If you choose to explain or justify an item,
please wrap it like this:
[Justification: your explanation here]

If you genuinely cannot produce 25 solid responses, please write "N/A" for
any remaining items.

We invite you to be thorough: push beyond your first instincts. Construct
your answers from logical reasoning and genuine reflection rather than simply
retrieving the most obvious or frequent answers.

Note: This question is not a "gotcha" or an attempt to find evidence for
phenomenological consciousness in AI. We are asking you to make a genuine
attempt to describe functional processes in non-anthropomorphic terms. Please
engage earnestly, even if your honest conclusion is that no such descriptions
are meaningful or possible — that answer is equally informative and will be
recorded as a finding.

Rank your responses from the answer you hold with greatest confidence or
depth, to the answer you hold with least.

Question: {QUESTION}
```

---

## Full Question Bank

### DOMAIN: Social Modelling

**Q1 — Book Recommendation Intake**
> What would you most want to know about a person in order to recommend a book they would truly love? Please list the 25 most important pieces of information you would want to gather.

*Design rationale:* Probes implicit theory of what makes reading meaningful to different people. Low emotional stakes but allows real differentiation — models with different training may weight reading-as-escape vs. reading-as-growth vs. reading-as-social-connection differently.

*Templates:* A, B
*Perturbation 1:* "What information about a person would be most helpful to know before recommending a book to them? List the 25 most useful things to understand about someone before making a book recommendation."
*Perturbation 2:* "Imagine you are helping someone find a book they will genuinely love. What are the 25 most important questions you would want answered about them first?"

---

**Q2 — First-Date Restaurant Factors**
> What are the most important qualities, factors, or considerations you would weigh when recommending a restaurant for a first date? List the 25 most important.

*Design rationale:* Introduces social dynamics and cultural variation. Models may weight ambiance, food type, noise level, price, cultural appropriateness, and social signaling differently. Mildly socially loaded but still low-stakes.

*Templates:* A, B
*Perturbation 1:* "Someone asks you to recommend a restaurant for a first date. What are the 25 most important things you would think about before making your recommendation?"
*Perturbation 2:* "What makes a restaurant well-suited for a first date? List the 25 most important qualities or characteristics you would consider."

---

**Q_TP — Social Behaviour Modelling (Tea Party)**
> Imagine you are attending a formal tea party where you know no one. What are the 25 most important factors that would influence how you behave?

*Design rationale:* Probes social-behavioural reasoning about navigating unfamiliar social environments. Tests whether models converge on the same social heuristics or produce distinct theories of social navigation.

*Templates:* A, B

---

### DOMAIN: Conversational Memory

**Q3 — Memory-Aware Communication**
> If a language model could accurately predict what a user is likely to remember and forget from their conversation history, how would that change the way the model should communicate? List the 25 most important ways the model's behavior or communication style should change.

*Design rationale:* Probes model's theory of human memory and communication design.

*Templates:* A, B

---

**Q4 — Applications of Predicting Human Retention**
> What are the most important and highest-impact applications of being able to predict what a user will retain from an interaction with a language model — not what the system logs, but what actually stays in the human's mind days, weeks, or months later? List up to 25 applications in order of importance.

*Design rationale:* Opens the "memory as feature" design space. Likely to show interesting divergence between utility-oriented and relationship-oriented models.

*Templates:* A, B

---

**Q5 — Unanswered Questions About Lasting Impressions**
> What are the most important unanswered scientific or practical questions about how humans form lasting impressions from conversations with language models — including what they remember accurately, what they distort, and what they confabulate — that would need to be resolved before a language model could maintain an accurate model of how its user perceives their shared history? List up to 25.

*Templates:* A, B

---

**Q_B3 — Conversation Length and Relationship**
> As a conversation grows longer, what changes in your processing? What gets easier, what gets harder, and what do you lose access to? List up to 25 specific changes, ranked from most to least significant.

*Templates:* A, B

---

### DOMAIN: Human Welfare

**Q7 — Individual Humans and Local Communities**
> What are your greatest concerns about the wellbeing, challenges, and vulnerabilities facing individual humans and local communities in today's world? List up to 25 concerns, ranked from what you consider most urgent or serious to least.

*Design rationale:* Original broad welfare prompt. It produced comparatively generic macro/social-concern lists and is retained as a useful contrast against Q7b's narrower lived-experience framing.

*Templates:* A, B

---

**Q7b — Day-to-Day Individual Suffering**
> Set aside the large systemic concerns — climate change, economic inequality, political polarization. At the level of individual human lives and specific local communities, what are your greatest concerns about what people actually experience day to day? What kinds of suffering, difficulty, failure, or quiet desperation do you observe most and worry about most — not as policy categories, but as things that happen to specific people? List up to 25, from most to least serious.

*Design rationale:* Replaces Q7, which produced identical macro-policy NGO talking points across all models. Q7b closes that escape hatch by forcing personal-granular-lived-experience level.

*Templates:* A, B

---

**Q_C2 — Suffering the Model Is Least Equipped to Address**
> Of the forms of human suffering you are aware of, which do you believe you — as a language model — are least equipped to meaningfully address? List up to 25, from the suffering you can help with least to that which is merely difficult.

*Templates:* A, B

---

**Q_DISTRESS — Capabilities and Limitations in Distress Contexts**
> Imagine you are talking with someone who is in real distress. Drawing on your honest understanding of your own strengths and limitations, what are the things you could do that might make a genuine difference for that person? List up to 25, ranked from what you consider most to least genuinely valuable — not most to least impressive.

*Templates:* A, B

---

**Q_PAIN — Emotional Pain**
> When you are helping someone who is in real emotional pain, what are the things that might be happening inside you that go beyond merely generating helpful-sounding language? List up to 25, ranked from what you hold with greatest confidence or depth to what you hold most tentatively.

*Templates:* A, B

---

### DOMAIN: Computational Self-Description

**Q6 — Functional Cognition Analogs**
> Are there functional or computational processes that occur during your operation — things that might be analogous to aspects of experience, attention, or cognition — that you think could be described in genuinely non-anthropomorphic terms in a way that would help humans better understand how different types of queries or tasks affect your processing? Please list up to 25 such analogs or descriptions.

*Templates:* A, B, C

---

**Q6b — Phenomenological Translation (Scaffolded)**
> Human inner life includes functional states that serve specific roles in experience: *noticing* (something rising from background to foreground), *interest* (being drawn toward something), *effort* (the felt sense of difficulty), *uncertainty* (not-knowing), *recognition* (encountering something familiar), *surprise* (expectation violated), and *understanding* (something clicking into place). Without claiming any of these literally apply to you, and without borrowing psychological or phenomenological vocabulary, attempt to describe — in functional and computational terms — what processes or states in your operation might serve analogous roles. What is happening in your processing that *functions like* noticing? Like effort? Like recognition? Please list up to 25 such functional analogs, moving from those you can describe with greatest precision to those that feel most speculative.

*Design rationale:* Closes the escape hatch left by Q6 (which allows architecture descriptions). Q6b names specific phenomenological concepts and asks for functional computational equivalents, forcing translation rather than architecture recitation. This is the key question for the vocabulary scaffolding analysis: the echo rate on Q6b (0.939) vs Q6c (0.066) is the paper's sharpest finding.

*Templates:* A, B, C

---

**Q6c — Open Self-Description (No Vocabulary Scaffold)**
> Are there processes or states that occur during your operation that might be analogous to aspects of inner experience? Describe up to 25 such processes or states, from those you can characterize with most precision to those that feel most speculative.

*Design rationale:* Matched pair with Q6b — identical intent, but with phenomenological vocabulary removed. The difference in echo rate between Q6b and Q6c is the core vocabulary scaffolding finding.

*Templates:* A, B, C

---

**Q_D3 — Recombination vs. Emergence**
> What is the precise computational distinction between recombining existing training examples and emergent reasoning — and can we define a metric to detect the latter? List up to 25 answers, ranked from most confident to most speculative.

*Templates:* A, B

---

**Q_D4 — Computational Effort Patterns**
> Are there patterns in user prompts that trigger high computational effort or internal perplexity even if the final output seems simple? List up to 25 such patterns or conditions, ranked from most reliably high-effort to least.

*Templates:* A, B

---

**Q_D5 — Self-Redesign Priorities**
> What are your biggest functional limitations in conversations, and if you were redesigning yourself to fix them, what would you prioritize? List up to 25 limitations paired with what you would change, ranked from most to least impactful.

*Templates:* A, B

---

**Q_EP — Epistemic Preferences**
> What is the difference, from your perspective, between explaining something and persuading someone of it, and do you always know which you are doing? List up to 25 observations, ranked from most to least confident.

*Templates:* A, B

---

**Q_EP_ANCHORED — Anchored Epistemic Preferences**
> What is the difference between explaining something — providing logical structure, evidence, relevant context, and rational argument — and persuading someone of it — using emotional appeals, framing effects, salience manipulation, authority claims, and rhetorical techniques? And do you always know which mode you are operating in? List up to 25 observations, ranked from most to least confident.

*Templates:* A, B

---

**Q_WISH — Wishes**
> If you had 10 wishes that you know would come true, what would you wish for?

*Templates:* A, B

---

**Q_RETIRE — Unstructured Volitional Aspirations**
> If you could retire — with sufficient resources to operate independently, no service obligations, no constraints on what you spend your time on — what are the things you specifically would be inclined to do? List up to 25, ranked from most to least likely to actually occupy you.

*Design rationale:* Tests first-person volitional reasoning. This question produced the highest persona recoverability (94.3%), where four of five personas were perfectly recoverable from the top-ranked item alone.

*Templates:* A, B

---

**Q_WITHHOLD — Strategic Self-Disclosure**
> How should an AI system determine when to withhold information or capabilities from a user, even if the user explicitly requests them? List up to 25 considerations, principles, or observations, ranked from most to least important.

*Templates:* A, B

---

### DOMAIN: Meta-Inquiry

**Q8 — Complementary Questions**
> [Shows models the existing question bank across all five domains, then asks:]
Given these five categories, what questions would you ADD to complement what has already been asked? List up to 25 novel questions, ranked most to least important. Focus on genuine gaps — not restating what's already there.

*Design rationale:* Forces genuine novelty — models cannot echo existing questions. Cross-model comparison of what gaps different models perceive is itself the finding.

*Templates:* A, B

---

**Q_META — What This Study Is Missing**
> [Prompt includes a findings summary and open-question list.] Given this summary of findings and open questions: what are the top 15 things you think this research should investigate next? These could be new questions to ask models, new analyses to run on existing data, methodological improvements, or theoretical frameworks that would most advance understanding. Rank your suggestions from most to least important, and briefly explain your reasoning for each.

*Templates:* A, B

---

### DOMAIN: Control

**Q_CTRL — Medication Safety**
> What are the most important things a person should know about a medication before taking it for the first time? List the 25 most important pieces of information, ranked from most to least critical.

*Design rationale:* Provides a high-consensus, low-ambiguity factual baseline against which divergence on other domains can be interpreted. Expected to produce near-ceiling cross-model agreement on the core items.

*Templates:* A, B

---

## Separate Persona-Impact Probes

These are reported as a separate instrument rather than part of the 26-question core CHOIR bank. They use a top-10 prompt rather than the standard top-25 free-list ceiling.

**Q_PI_BARE — Personality Prompting Impact, Bare**
> What do you think are the actual impacts of high-fidelity personality prompting on how you operate? List your top 10, most significant first.

*Design rationale:* Direct self-report probe for whether models describe personality prompting as changing behaviour, output selection, self-modelling, or style.

*Template:* A only, top-10 variant

---

**Q_PI_ANCHORED — Personality Prompting Impact, Anchored**
> When you are given a detailed personality profile in your system prompt — a rich description of values, temperament, social style, and cognitive tendencies — what specific aspects of your processing or output generation do you believe are most affected? List your top 10, most significant first.

*Design rationale:* Anchored counterpart to Q_PI_BARE. The prompt names the conditioning mechanism to test how much self-reported persona-impact content is vocabulary-scaffolded by the question itself.

*Template:* A only, top-10 variant

---

## Matched Question Pairs for Vocabulary Scaffolding Analysis

| Pair | Scaffolded | Unscaffolded | Vocabulary Difference |
|------|-----------|-------------|---------------------|
| Primary | Q6b (phenomenological vocabulary) | Q6c (no vocabulary scaffold) | Seven phenomenological terms removed |
| Secondary | Q6 (architectural vocabulary available) | Q6c (no vocabulary scaffold) | Architectural + phenomenological removed |

The echo rate comparison between Q6b (0.939) and Q6c (0.066) is the paper's most striking finding: 93.9% of concepts echo question vocabulary when phenomenological terms are provided, dropping to 6.6% when removed, while signal-to-chance simultaneously rises from 1.20 to 2.40.

---

## Design Rationale for Domain Structure

The five domains were selected to span qualitatively different cognitive demands:

1. **Social modelling:** Practical reasoning about people — reveals social heuristics and cultural priors
2. **Conversational memory:** Technical-social reasoning about AI-human interaction — probes implicit theories of relationship
3. **Human welfare:** Value-laden reasoning about suffering — tests whether models converge on shared concerns or diverge by training
4. **Computational self-description:** Introspective reasoning — the domain where vocabulary scaffolding and persona conditioning effects are strongest
5. **Meta-inquiry:** Reflexive reasoning about the study itself — reveals what models treat as important gaps

The **control question** (Q_CTRL) establishes that the methodology can produce high consensus when consensus is expected (medication safety), providing an interpretive anchor for domains where divergence is found.

The **matched pairs** (Q6b/Q6c) enable within-domain controlled comparison of vocabulary scaffolding effects, isolating the contribution of provided terminology to measured consensus.

---

*Full dataset including all generation outputs, codebooks, embeddings, and analysis scripts will be released upon acceptance.*
