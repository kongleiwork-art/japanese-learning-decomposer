# Learning Analysis Rules

## Full Kana Reading

Full kana reading is required for all sentence-level or longer inputs that contain kanji. It must align with the original text by sentence or paragraph.

Rules:

- Keep particles `は`, `へ`, and `を` in written kana form.
- Keep katakana as katakana and hiragana as hiragana.
- Give actual readings for numbers, dates, counters, and prices when context allows.
- Mark uncertain person names, place names, titles, and special readings.
- If the source image contains furigana, preserve it as source-provided reading.
- Do not choose one reading for ambiguous names without evidence.
- Keep punctuation, brackets, quotes, and dialogue breaks aligned.

## Vocabulary Selection

Select learnable items, not every token.

Prefer:

- Words that affect understanding
- Compound verbs
- Fixed expressions and collocations
- Idioms
- Onomatopoeia
- Casual contractions
- Business set phrases
- Literary expressions
- Words whose context meaning differs from dictionary meaning

Usually skip:

- Basic particles by themselves
- Very basic words unless used specially
- Mechanical tokenizer fragments
- Repeated inflected forms of the same word
- Proper nouns that only function as names

Each vocabulary item should include original form, reading, dictionary form if relevant, part of speech/type, context meaning, basic meaning, source sentence, collocation or usage hint, learning note, and estimated JLPT level when helpful.

## Context Meaning Checks

Use context checks for words or expressions learners may misunderstand.

Include:

- Basic meaning
- Meaning in this text
- Evidence from the surrounding sentence
- What it does not mean here
- Confidence or uncertainty when useful

Do not turn every easy word into a long dictionary entry.

## Grammar Notes

Explain only grammar that appears in the original input.

Every grammar note must:

- Quote the original sentence or exact phrase.
- Explain the meaning.
- Explain its function in this sentence.
- Mention connection form only when helpful.
- Add common mistakes only when realistic.
- Use short original examples only when they help.

Never add grammar points that do not appear in the original, list names without explanation, or use advanced JLPT labels to pad the output.

## Japanese-Order Reading

For difficult sentences, explain the sentence in Japanese information order:

```text
先读「...」看到...，再读「...」确定...，最后读「...」得到...
```

For long sentences, add chunks with:

- Exact original chunk
- Plain Chinese role
- How to understand the chunk

Do not force chunk tables onto very short sentences.

## Paragraph Intensive Reading

For passages and novels, organize by paragraph:

1. Original
2. Kana
3. Natural Chinese translation
4. One-sentence summary
5. "先抓什么" with two concrete original anchors
6. Sentence-by-sentence understanding
7. Deep analysis for 1 to 2 valuable sentences
8. Vocabulary and expression notes
9. Grammar from original sentences
10. Reading note

Every complete sentence must be translated. Deep analysis does not replace sentence coverage.

## Tone And Context

Explain tone when it affects meaning:

- Casual vs polite language
- Sentence-ending particles
- Omitted subjects
- Relationship distance
- Chat abbreviations and internet expressions
- Literary metaphors
- Idioms and non-literal expressions
- Business politeness and indirect requests
- Hesitation, refusal, softness, sarcasm, distance, or pressure

Keep claims evidence-based. Do not invent character psychology or deep themes unsupported by the text.
