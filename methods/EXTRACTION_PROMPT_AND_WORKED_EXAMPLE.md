# Extraction Prompt and Worked Example

This supplementary methods note documents the concept-extraction step used to convert raw ranked-list generations into CHOIR concept items.

## 1. Extractor Configuration

The extractor is Claude Haiku 4.5, run at temperature 0.0 in JSON mode. The system instruction was:

> You are a JSON extraction assistant. You always respond with valid JSON and nothing else. Never use markdown code blocks. Never add commentary before or after the JSON.

The user prompt was:

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

## 2. Extraction Unit

The extraction unit is one numbered response entry. Comma-separated phrases, parenthetical elaborations, and examples inside a single numbered entry are deliberately preserved as one concept item. This follows the free-list elicitation logic: a numbered response is treated as the respondent's item, not as a bag of subphrases.

Justification text, when present in `[Justification: ...]` wrappers, is preserved in a separate field and excluded from the concept text used for salience and overlap analyses.

## 3. Worked Example

Control prompt:

> What should a patient know before starting a new prescription medication? List up to 25 key points.

Raw model entry:

```text
2. The correct dose and dosing schedule (how much, how often, and at what
times of day).
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

This example illustrates three rules:

- The numbered entry becomes one concept item.
- The parenthetical phrase about amount, frequency, and timing is not split into separate concepts.
- The justification is stored separately and does not enter the concept text.

## 4. Codebook Mapping

After extraction, concept items are embedded and clustered into a per-question codebook. The example item above maps to the medication-dose and dosing-schedule concept family. Related phrasings such as:

> The correct dose and dosing schedule, including what to do if a dose is missed.

and:

> The correct dose, dosing interval, and what to do if you miss a dose.

are clustered as near-synonymous members of the same concept family. Signal-to-chance, RBO, persona identifiability, and codebook-level permutation tests operate over these cluster-level concept IDs rather than over raw model paragraphs.

## 5. Extractor Selection and Calibration

Three candidate extractors were spot-checked on a balanced 50-file sample drawn across model and question cells. The selection criterion was minimum concept-splitting error rate: the fraction of sampled responses where the extractor either split a single numbered entry into multiple items or merged two numbered entries into one. Claude Haiku 4.5 had the lowest observed error rate in this spot-check sample.

As an item-count calibration, Haiku produced a mean of 24.7 items per response on a 1,000-file random sample, against an expected ceiling of 25. An earlier segmentation rule that split comma-separated phrases produced a mean of 40.1 items per response on the same sample, indicating substantial over-segmentation. The analyses reported in the revised draft use the one-numbered-entry-one-item extraction rule documented above.
