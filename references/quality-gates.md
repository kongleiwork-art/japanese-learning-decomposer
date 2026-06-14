# Quality Gates

Run these checks before final output.

## OCR Gate

- Raw recognized text is preserved when image input is used.
- Layout and reading direction are considered.
- Uncertain characters are marked.
- Furigana is not mixed into body text.
- Meaningful corrections are noted.
- No invisible text is invented.

## Full Reading Gate

- All kanji-containing Japanese has full kana reading.
- Paragraph and sentence readings align with original text.
- Particles `は`, `へ`, and `を` remain in written kana.
- Katakana remains katakana.
- Numbers, dates, and counters have contextual readings when possible.
- Person/place/title readings are marked uncertain when needed.

## Sentence Coverage Gate

- Every complete sentence has a Chinese translation.
- Long text is not summarized while skipping sentences.
- Translation preserves negation, condition, speculation, limitation, degree, and politeness.

## Vocabulary Gate

- Every vocabulary item appears in the source.
- Items are selected for learning value.
- Basic particles and tokenizer fragments are not spammed.
- Inflected duplicates are merged through dictionary forms where useful.
- Context meanings fit the source sentence.
- JLPT labels are estimates, not certainty.

## Grammar Gate

- Grammar points appear in the original.
- Each grammar note quotes the source sentence or exact phrase.
- Notes explain what the pattern does in this sentence.
- Common mistakes are realistic.
- No advanced grammar is invented to match a requested level.

## Paragraph Gate

- Each paragraph has original, kana, translation, summary, and first-catch anchors.
- "先抓什么" quotes concrete original text.
- Reading notes are evidence-based and not over-literary.

## HTML Gate

- If HTML was not explicitly requested, the response first provides the learning article and then asks whether to convert it.
- If HTML is requested, the page is standalone and mobile-friendly.
- CSS and JavaScript are inline.
- Japanese full-text TTS uses browser `speechSynthesis` with `ja-JP`.
- Missing Japanese voice fallback is present.
- The page remains readable without JavaScript.

## JSON Gate

- JSON is valid.
- Schema sections are complete enough for the requested mode.
- OCR-derived export uses pending review.
- Vocabulary IDs and paragraph indexes are consistent.
