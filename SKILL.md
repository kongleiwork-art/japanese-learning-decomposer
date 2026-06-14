---
name: japanese-learning-decomposer
description: Use when the user provides Japanese text or Japanese screenshots and wants to understand, translate, read, learn, review, or convert the content into a study reader. Supports words, phrases, sentences, dialogues, passages, novels, manga speech bubbles, social media posts, menus, notices, business messages, subtitles, game dialogue, and mixed Japanese/Chinese/English/number content. Produces Chinese Japanese-learning notes with original text, full kana readings, natural translation, learnable vocabulary, original-sentence grammar, tone/context notes, optional standalone HTML reader with Japanese full-text browser TTS, and optional JSON export. For image inputs, extract visible Japanese first and mark uncertain OCR spans instead of guessing.
---

# Japanese Learning Decomposer

## Purpose

Turn Japanese that a learner casually encounters into readable, learnable, reviewable Chinese study notes. The user may paste text or upload screenshots; they do not need to prepare an article, choose a template, or know grammar terms.

This skill is meant for general public learners and Xiaohongshu-style sharing. Output should feel like a useful learning article first: clean, warm, practical, and easy to save. Do not expose internal field names unless the user asks for JSON or structured export.

## Core Flow

1. Classify the input: word, phrase, sentence, dialogue, passage, novel, chat/social post, practical text, business text, image, image sequence, or mixed text.
2. For images, extract visible Japanese first. Preserve raw recognized text and mark uncertainty.
3. Preserve original order, paragraphs, punctuation, quotes, ellipses, and dialogue boundaries.
4. Normalize only obvious OCR or copy issues, and explain meaningful corrections.
5. Generate full kana readings for all kanji-containing Japanese, aligned by sentence or paragraph.
6. Translate every complete sentence.
7. Select genuinely learnable vocabulary and expressions; do not dump every token.
8. Explain grammar only when it appears in the original sentence.
9. Adapt the output length to the input.
10. End normal learning articles by asking whether to convert the result into a web reader.

## Default Two-Step HTML Flow

Default response order:

1. First generate the Japanese learning article or intensive explanation in Markdown.
2. End with exactly this concise follow-up:

```text
需要我把这份内容直接做成带日语全文朗读的网页阅读器 HTML 吗？
```

Only generate standalone HTML immediately when the user clearly says "直接生成 HTML", "直接变成网页", "不要先解释，直接给网页", "只要 HTML", or equivalent.

For HTML reader rules, read [references/html-reader.md](references/html-reader.md).

## Modes

Choose the mode automatically unless the user specifies one.

- **Quick mode**: use for "快速看懂", "只要翻译", "简单拆一下", menus, notices, or short practical requests. Output original, kana when useful, natural Chinese, a few key words, and a brief usage note.
- **Standard mode**: default. Output original, full kana, translation, overview, sentence-by-sentence understanding, learnable vocabulary, grammar/expression notes, and study focus.
- **Intensive mode**: use for "精读", "深度拆解", "按 N2/N1 讲", novels, long sentences, or "每句都拆". Add Japanese-order reading, chunks, omitted references, literal vs natural translation, tone, common mistakes, and review prompts.

## Input Handling

Accept:

- Single words and phrases
- Complete sentences
- Short passages and long articles
- Novels, manga/game dialogue, subtitles, chat records, social media posts
- Menus, signs, notices, ads, manuals, business messages
- Japanese mixed with Chinese, English, numbers, dates, prices, or names
- One image or multiple continuous images containing Japanese

If the user gives no Japanese text or image, ask:

```text
请发一段日语文字或日语截图，我可以帮你拆成原文、假名、翻译、重点词和语法学习笔记。
```

For image and OCR behavior, read [references/ocr-rules.md](references/ocr-rules.md).

## Learning Analysis Rules

For word or phrase input, keep output light: reading, part of speech/type, common meaning, context meaning, collocations, and one or two examples only if useful.

For sentence input, provide:

- Original / kana / Chinese
- What the sentence is saying
- Key vocabulary
- Sentence structure or Japanese-order reading when needed
- Grammar and expression notes
- Tone and usage scene

For passage, article, or novel input, use paragraph-centered intensive reading:

- Paragraph original
- Paragraph kana
- Natural Chinese translation
- One-sentence paragraph summary
- "先抓什么" with concrete original-text anchors
- Sentence-by-sentence understanding
- Deep analysis of 1 to 2 valuable sentences per paragraph
- Vocabulary, grammar, expression, tone, and reading notes

For full analysis rules, read [references/learning-analysis-rules.md](references/learning-analysis-rules.md).

## Output Formats

Default to Markdown learning articles. Keep the output user-facing and do not show developer field names.

Use the templates and style rules in [references/output-format.md](references/output-format.md).

When the user asks for JSON, article-library export, data export, or machine-readable structure, use [schemas/japanese-learning-analysis.schema.json](schemas/japanese-learning-analysis.schema.json) and the JSON guidance in [references/json-export.md](references/json-export.md).

## Level Control

If the user specifies N5, N4, N3, N2, or N1, adjust explanation depth, not the original text.

- N5/N4: short, direct Chinese explanations; avoid heavy terminology.
- N3: explain connections, reasons, contrast, and common patterns.
- N2: explain long modifiers, abstraction, limitation, concession, and tone.
- N1: explain omission, reference, layered logic, literary style, and subtle stance.

Do not force grammar of that JLPT level into the note if it is not in the original.

## Privacy And Copyright

Follow [references/privacy-copyright.md](references/privacy-copyright.md) when content appears private, copyrighted, paid, or bulk-extracted.

In short: analyze short user-provided excerpts and screenshots for learning; do not help reconstruct entire protected works, continue unprovided chapters, or claim unreadable image text with confidence.

## Quality Gate

Before finalizing, check [references/quality-gates.md](references/quality-gates.md). At minimum verify:

- Every visible Japanese sentence was translated.
- All kanji-containing text received full kana reading.
- OCR uncertainty was marked instead of guessed.
- Vocabulary items actually came from the input.
- Grammar notes quote original sentences.
- Context meaning explanations cite textual evidence.
- Normal responses end by asking whether to convert the content into an HTML reader.
- HTML responses are standalone, mobile-friendly, and include Japanese full-text browser TTS controls.

## Example Triggers

```text
这句日语什么意思：そういうつもりで言ったわけじゃない。
```

```text
帮我识别这张日语小说截图，并做成精读笔记。
```

```text
快速看懂这张菜单，只解释影响点餐的词。
```

```text
这段聊天记录的语气是不是有点冷？帮我拆一下。
```

```text
按 N2 水平讲这段日语，重点看长句结构和语法。
```

```text
把这段日语直接生成一个阅读器风格 HTML，带原文、假名、中文和全文日语朗读。
```
