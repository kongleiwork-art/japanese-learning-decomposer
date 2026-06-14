# HTML Reader Output

Use this as the second step after the normal learning article by default. Generate it immediately only when the user explicitly asks for direct HTML.

## Reader Requirements

Output a complete standalone `.html` file that can be saved and opened in a browser.

Build:

- Mobile-first learning reader suitable for Xiaohongshu users.
- Calm reading interface, not a marketing landing page.
- Article title or generated title.
- Overview with content type, estimated level, tone, and summary.
- Paragraph sections with original Japanese, kana reading, and Chinese translation aligned together.
- Sentence blocks for longer text.
- Highlighted key vocabulary and grammar notes.
- "先抓什么", "重点句顺读", "词义核对", and "表达语气" for passage-level or intensive outputs.
- OCR uncertainty warning area for image sources.
- No external CDN dependency unless the user explicitly allows it.
- No logos, ads, tracking, watermarks, or decorative clutter.

## Audio Reading

Use browser TTS by default:

- Use `window.speechSynthesis`.
- Set utterance `lang` to `ja-JP`.
- Read the Japanese original text, not the Chinese explanation.
- Provide Play, Pause/Resume, Stop, speed control, and sentence replay when practical.
- Keep a JavaScript sentence list and highlight the current sentence with `data-sentence-index`.
- Show this fallback if no Japanese voice is available:

```text
当前浏览器没有可用的日语朗读声音，请在系统语音设置中添加日语语音，或换用支持日语 TTS 的浏览器。
```

Do not claim an MP3 file was generated unless an actual audio-generation tool or user-provided audio file exists.

## Implementation Rules

- Put CSS and JavaScript inline.
- Escape user-provided text safely.
- Use semantic HTML.
- Keep Japanese text selectable.
- Keep the page readable without JavaScript.
- Add a sticky mini player at the bottom on mobile for longer content.
- Include "学习重点" or "今日复习" near the end.

## Minimum Structure

```html
<!doctype html>
<html lang="zh-CN">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>日语学习阅读器</title>
  <style>
    /* inline reader CSS */
  </style>
</head>
<body>
  <main class="reader">
    <header class="hero">
      <p class="eyebrow">日语学习阅读器</p>
      <h1>...</h1>
      <p class="summary">...</p>
    </header>

    <section class="audio-player" aria-label="日语全文朗读">
      <button id="playBtn">播放全文</button>
      <button id="pauseBtn">暂停</button>
      <button id="stopBtn">停止</button>
      <label>语速 <input id="rate" type="range" min="0.6" max="1.2" step="0.1" value="0.9"></label>
      <p id="voiceWarning" hidden>当前浏览器没有可用的日语朗读声音。</p>
    </section>

    <section class="paragraphs"></section>
    <section class="study-notes"></section>
  </main>

  <script>
    const sentences = [
      { original: "...", reading: "...", translation: "..." }
    ];
    // Use speechSynthesis with ja-JP voice and sentence highlighting.
  </script>
</body>
</html>
```
