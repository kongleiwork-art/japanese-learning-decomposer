# JSON Export

Only output JSON when the user explicitly asks for JSON, data export, article-library format, machine-readable structure, or similar.

Use [../schemas/japanese-learning-analysis.schema.json](../schemas/japanese-learning-analysis.schema.json) as the target structure.

## Export Principles

- Normal users should receive Markdown, not JSON.
- Image/OCR content should default to `review.status = "pending"`.
- Preserve raw text, cleaned text, full reading, paragraph readings, uncertain spans, and normalization changes.
- Keep all sentence translations in `intensiveReading[].sentenceTranslations`.
- Put only selected valuable sentences in `sentenceBreakdown`.
- Ensure `vocabularyIds` reference real vocabulary items.
- Do not mark OCR-derived content as publication-ready without human review.

## Required Top-Level Sections

- `meta`: source type, mode, page count, layout, estimated JLPT, OCR confidence, review need.
- `source`: raw text, normalized text, full reading, paragraphs, paragraph readings, uncertain spans, normalization changes.
- `overview`: content type, summary, guide, tone, style.
- `vocabulary`: learnable word cards.
- `readingOverrides`: special or uncertain readings.
- `intensiveReading`: paragraph-level reading analysis.
- `learningFocus`: concise review focus.
- `review`: status and warnings.

## Consistency Checks

Before output:

- Every paragraph has matching reading and translation.
- Every complete sentence appears in `sentenceTranslations`.
- Every grammar note has `sourceSentence` copied from the original.
- `chunks[].text` appears in the source sentence.
- `uncertainSpans` are not silently resolved.
- JSON is valid and does not include comments.
