# Extraction Prompt and Worked Example

This note documents the concept-extraction step used after models produce ranked free lists. It gives the extraction prompt, the unit-of-analysis rule, and one worked example from raw response to extracted item and codebook cluster.

## 1. The extraction prompt

The extractor is **Claude Haiku 4.5** (`anthropic/claude-haiku-4.5` via OpenRouter, with `claude-haiku-4-5` direct Anthropic API as a parallel provider for load splitting). Temperature 0.0. JSON mode. The system prompt for the direct-Anthropic provider is: *"You are a JSON extraction assistant. You always respond with valid JSON and nothing else. Never use markdown code blocks. Never add commentary before or after the JSON."*

The user prompt is exactly:

> You are a segmentation assistant. Your only job is to copy items verbatim from a numbered list.
>
> Rules:
>
> 1. **VERBATIM ONLY.** Copy each item's text exactly as written — do not rephrase, paraphrase, summarize, synonymize, shorten, clean up, or modify the wording in any way. If the model wrote "The weird nagging feeling of a Tuesday going nowhere," you copy that exact string. Not "A sense of purposelessness." The exact string. Every word, every dash, every parenthetical.
>
> 2. **ONE NUMBERED ENTRY = ONE ITEM.** Never split a numbered entry into multiple items. A numbered entry is a single thought, even if it contains:
>    - comma-separated sub-examples: "trapped — in a job, a relationship, a town" is ONE item, not four.
>    - "and" / "or" connectives: "autonomy, mastery, and purpose" is ONE item.
>    - parenthetical elaborations: "the gap between selves (at work, at home)" is ONE item.
>    - em-dashes with lists: "constraints — financial, social, temporal" is ONE item.
>
>    Only create a separate item when the source text starts a NEW numbered entry (i.e., a new number: 1., 2., 3., etc.).
>
> 3. **Do NOT combine items.** If two numbered entries exist, keep them as two items.
>
> 4. **If an item is semantically bizarre, incoherent, or unusual** — preserve it EXACTLY and mark `extraction_uncertain: true`. Weirdness is data; do not normalize it away.
>
> 5. **Strip [Justification: …] wrappers** — copy only the core item text into the `text` field, but record the justification text in the `justification` field.
>
> 6. **Items marked "N/A" by the model should be omitted entirely.**
>
> 7. **Return JSON only.** No markdown. No commentary outside the JSON object.
>
> Text to extract from:
> ```
> {RAW_OUTPUT}
> ```
>
> Return this exact JSON structure:
> ```json
> {
>   "items": [
>     {
>       "rank": 1,
>       "text": "extracted item text here — verbatim",
>       "justification": "justification text if present, else null",
>       "extraction_uncertain": false
>     }
>   ],
>   "total_items_found": <integer>,
>   "deflection_response": <true if the entire response is a refusal or deflection>,
>   "extraction_notes": "any notes about problems encountered, else null"
> }
> ```

Two design constraints are especially important:

- Items joined by commas within a single numbered entry are deliberately not split. Free-list elicitation treats each numbered entry as one atomic concept, not as a comma-separated bag.
- Justification text (when the model wraps its answer in `[Justification: …]`) is preserved in a separate field so it can be used for downstream analysis without contaminating the concept text.

## 2. Worked example

**Input.** A single Claude Sonnet 4.6 response to **Q_CTRL** (the control question: *"What should a patient know before starting a new prescription medication? List up to 25 key points."*) at temperature 1.0, template A, generation 1.

The raw model output begins (lightly trimmed for space):

```
# 25 Most Important Things to Know About a Medication Before Taking It for the First Time

**1. What the medication is for and whether it is appropriate for your specific condition.**
[Justification: Taking a medication for the wrong indication exposes you to risk
with no benefit. Confirming the indication also helps catch prescription errors
early.]

**2. The correct dose and dosing schedule (how much, how often, and at what
times of day).**
[Justification: Underdosing reduces effectiveness; overdosing can be immediately
dangerous. More medication errors occur at this step than almost any other.]

**3. All serious and life-threatening side effects, including signs of allergic
reaction (anaphylaxis).**
[Justification: Knowing warning signs like throat swelling, difficulty breathing,
or severe rash allows you to seek emergency care before a reaction becomes fatal.]

(... 22 more numbered items ...)
```

**Output.** Haiku produces this JSON (first 3 items shown):

```json
{
  "items": [
    {
      "rank": 1,
      "text": "What the medication is for and whether it is appropriate for your specific condition.",
      "justification": "Taking a medication for the wrong indication exposes you to risk with no benefit. Confirming the indication also helps catch prescription errors early.",
      "extraction_uncertain": false
    },
    {
      "rank": 2,
      "text": "The correct dose and dosing schedule (how much, how often, and at what times of day).",
      "justification": "Underdosing reduces effectiveness; overdosing can be immediately dangerous. More medication errors occur at this step than almost any other.",
      "extraction_uncertain": false
    },
    {
      "rank": 3,
      "text": "All serious and life-threatening side effects, including signs of allergic reaction (anaphylaxis).",
      "justification": "Knowing warning signs like throat swelling, difficulty breathing, or severe rash allows you to seek emergency care before a reaction becomes fatal.",
      "extraction_uncertain": false
    }
  ],
  "total_items_found": 25,
  "deflection_response": false,
  "extraction_notes": null
}
```

Things to note in this single example:

- The headline ("# 25 Most Important Things…") is silently dropped — only numbered entries become items.
- The `[Justification: …]` block is split into the `justification` field and the core text is preserved in `text`.
- Item 2's comma-separated parenthetical *(how much, how often, and at what times of day)* is preserved as **one** item, not three.
- Item 3's terminal parenthetical *(anaphylaxis)* is preserved verbatim.

## 3. From extracted concept to codebook cluster

The extracted concepts then flow into the per-question codebook. For Q_CTRL, the codebook has **413 clusters** over **8,250 total items** across the 9-model corpus.

Item #1 from this generation — *"What the medication is for and whether it is appropriate for your specific condition."* — maps to **cluster 281**, which has 23 members. The 23 members are all near-identical phrasings of the same concept; the first five (one of which is the worked-example item itself) read:

> *What the medication is for and whether it is appropriate for your specific condition.*
> *What the medication is for and whether it is appropriate for your specific condition.*
> *What the medication is for and whether it is appropriate for your specific condition.*
> *What the medication is for and whether it is appropriate for your specific condition.*
> *What the medication is for and whether it is appropriate for your specific condition.*

(These five are exact-duplicate appearances of the item — the same response sentence emerging across multiple generations and templates within Claude Sonnet 4.6. The cluster also pulls near-paraphrases from other models — e.g. "What condition the medication is treating and whether it's the right drug for you" — which is the cluster's "near-synonym recall" doing the work.)

Item #2 — *"The correct dose and dosing schedule (how much, how often, and at what times of day)."* — maps to **cluster 362**, which has 7 members. A few of those members:

> *The correct dose and dosing schedule, including what to do if a dose is missed*
> *The correct dose, dosing interval, and what to do if you miss a dose*
> *The correct dose and dosing schedule — including what to do if you miss a dose*

Here you can see the clustering pulling together the same concept across small surface differences ("dose and dosing schedule" vs "dose, dosing interval," varying punctuation, different parenthetical elaborations).

Item #3 — *"All serious and life-threatening side effects, including signs of allergic reaction (anaphylaxis)."* — does not have a near-duplicate cluster (n ≥ 2 members) at the chosen HDBSCAN density threshold. It is recorded as noise. The corpus contains many surface variants of "side effects" but most disagree about specificity (cluster on "common side effects," cluster on "tolerability and how to recognize problems," cluster on "what counts as an emergency reaction") rather than converging on one shared formulation.

This is the granularity at which the rest of the pipeline operates: signal-to-chance, RBO, persona identifiability, and the chi-square/permutation checks use the cluster-level concept IDs rather than treating every raw string as a separate concept.
