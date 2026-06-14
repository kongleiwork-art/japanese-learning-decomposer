# OCR Rules

Use these rules for image inputs and copied text that may contain recognition errors.

## Image Reading Order

Identify layout before analysis:

- Horizontal text
- Vertical text
- Multi-column pages
- Manga speech bubbles
- Captions, signs, UI labels, and decorative text
- Existing furigana
- Multi-image sequence

For multi-image input, preserve upload order and page index. Do not assume images are continuous unless the text supports it. If a sentence crosses pages, merge it only when the join is clear and record the source pages in the note.

## Raw And Clean Text

Maintain two layers internally:

- `rawText`: faithful OCR or visual extraction.
- `normalizedText`: cleaned text for learning analysis.

Do not show field names to normal users unless JSON is requested. In normal Markdown, label these as "识别原文" and "清理后原文" when both matter.

## Uncertainty Marking

Use explicit marks:

```text
⟦候选：待つ / 持つ⟧
⟦无法确认 1 字⟧
```

Low-confidence image spans must remain visible in the output. Never silently pick a candidate because it makes the story read better.

## Allowed Corrections

Correct only high-confidence issues:

- Obvious half-width/full-width confusion
- `ロ` vs `口`
- `ー` vs `一`
- Hiragana/katakana shape confusion such as `へ` vs `ヘ`
- OCR line breaks that split a clear word
- Furigana accidentally mixed into body text

Every meaningful correction needs a short "识别提示" or "不确定项" note.

## Forbidden Behavior

Do not:

- Invent invisible text.
- Treat page numbers, watermarks, or decorations as body text unless relevant.
- Put furigana into the main sentence.
- Reverse vertical columns.
- Delete repeated punctuation, elongated sounds, or emotional marks.
- Rewrite dialect, casual speech, literary punctuation, old spelling, or variant characters.
- Claim an image is fully recognized when parts are blurry or cropped.
