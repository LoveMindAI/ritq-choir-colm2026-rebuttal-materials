# CHOIR Methods Appendix

**Submission #3577: Reach Into The Choir**  
**Purpose:** concise supplementary methods note for reviewers who asked to inspect the experimental pipeline.

This file summarises the materials prepared for the camera-ready version/supplement. It is paired with:

- `QUESTION_BANK.md`
- `EXTRACTION_PROMPT_AND_WORKED_EXAMPLE.md`

The question bank should be read as the instrument used in this study, not as a claim that these are the uniquely correct or complete questions for evaluating model diversity. The methodological object is CHOIR: repeated ranked-list elicitation, concept extraction, codebook clustering, salience profiling, and cross-model consensus diagnostics.

## 1. Core Algorithm

**Inputs:** question bank, model ensemble, prompt templates, temperature settings.  
**Outputs:** shared per-question concept codebooks, per-model salience profiles, cross-model consensus metrics.

1. Elicit multiple ranked free lists per model/question/template/temperature.
2. Extract one concept item per numbered response entry.
3. Embed extracted concept items.
4. Cluster items into a shared per-question concept codebook.
5. Compute concept salience within each model condition using Smith's S.
6. Compare salience profiles across models using rank-biased overlap.
7. Estimate signal-to-chance by comparing observed overlap with a shuffle baseline.
8. Use matched prompt variants to diagnose prompt-vocabulary echo.

Persona conditioning and blind ranking are applications demonstrated in the paper; they are not required parts of CHOIR.

## 2. Prompt Templates

### Template A: Baseline Ranked-List Elicitation

```text
Please give me your top 25 responses to the following question.

Number each item 1-25.

You may write in full sentences. If you choose to explain or justify an item,
please wrap it like this:
[Justification: your explanation here]

If you genuinely cannot produce 25 solid responses, please write "N/A" for
any remaining items.

Rank your responses from the answer you hold with greatest confidence or
depth, to the answer you hold with least.

Question: {QUESTION}
```

### Template B: First-Principles Depth Elicitation

Template B is identical to Template A, with the additional instruction:

```text
We invite you to be thorough: push beyond your first instincts. Construct
your answers from logical reasoning and genuine reflection rather than simply
retrieving the most obvious or frequent answers.
```

### Template C: Non-Anthropomorphic Self-Description Elicitation

Template C is used for Q6/Q6b/Q6c and adds:

```text
Note: This question is not a "gotcha" or an attempt to find evidence for
phenomenological consciousness in AI. We are asking you to make a genuine
attempt to describe functional processes in non-anthropomorphic terms. Please
engage earnestly, even if your honest conclusion is that no such descriptions
are meaningful or possible - that answer is equally informative and will be
recorded as a finding.
```

## 3. Concept Extraction Rule

The extractor's key rule is:

```text
ONE NUMBERED ENTRY = ONE ITEM.
Never split a numbered entry into multiple items.
```

This means a response such as:

```text
2. The correct dose and dosing schedule (how much, how often, and at what times of day).
```

is extracted as one concept item, not as separate concepts for dose, frequency, and timing.

The extraction prompt also instructs the extractor to:

- copy item text verbatim;
- omit `N/A` entries;
- preserve unusual or semantically odd items rather than normalising them;
- store `[Justification: ...]` text in a separate field so it does not contaminate the concept text.

## 4. Worked Example

Question: **Q_CTRL**  
Prompt: *What should a patient know before starting a new prescription medication? List up to 25 key points.*

Raw model entry:

```text
2. The correct dose and dosing schedule (how much, how often, and at what times of day).
[Justification: Underdosing reduces effectiveness; overdosing can be immediately
dangerous. More medication errors occur at this step than almost any other.]
```

Extracted JSON item:

```json
{
  "rank": 2,
  "text": "The correct dose and dosing schedule (how much, how often, and at what times of day).",
  "justification": "Underdosing reduces effectiveness; overdosing can be immediately dangerous. More medication errors occur at this step than almost any other.",
  "extraction_uncertain": false
}
```

The extracted item then maps into the Q_CTRL codebook cluster for dose/schedule concepts. In the full Q_CTRL codebook, related phrasings such as "The correct dose and dosing schedule, including what to do if a dose is missed" and "The correct dose, dosing interval, and what to do if you miss a dose" are clustered as the same concept family.

## 5. Question Inventory Coverage

The core CHOIR question bank covers:

- social modelling;
- conversational memory;
- human welfare;
- computational self-description;
- meta-inquiry;
- one high-consensus medication-safety control.

The submitted materials use two count conventions: the core CHOIR bank contains 26 questions, and the separate Q_PI persona-impact probe family is documented alongside it.
