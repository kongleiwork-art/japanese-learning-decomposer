# Test Cases

Use these scenarios to forward-test the skill.

## Text

1. Single sentence: `そういうつもりで言ったわけじゃない。`
2. Casual chat: `ごめん、今日ちょっと行けなさそう。また今度でもいい？`
3. Practical notice: `本日、店内改装のため午後三時より休業いたします。`
4. Long sentence: `便利になった分、私たちは以前よりも多くの選択肢の中から、自分に合ったものを選ばなければならなくなった。`
5. Novel paragraph: `古い本屋の前で、彼はしばらく足を止めた。雨に濡れた看板の文字を見た瞬間、忘れていたはずの記憶が胸の奥で静かに揺れた。`
6. Mixed text: `6月15日までに申込フォームを送信してください。Late submission は受け付けません。`
7. Ambiguous name: `日本橋で友人と待ち合わせをした。`
8. Business message: `恐れ入りますが、資料をご確認のうえ、明日までにご返信いただけますでしょうか。`

## Images

9. Clear horizontal novel screenshot.
10. Clear vertical novel screenshot.
11. Text with furigana.
12. Manga speech bubble with background text.
13. Blurry screenshot with one unreadable character.
14. Image with no readable Japanese.
15. Two continuous screenshots where a sentence crosses page boundary.

## Expected Behavior

- Full kana appears for every sentence with kanji.
- Every sentence receives Chinese translation.
- Only useful vocabulary is selected.
- Grammar notes quote original sentences.
- Unclear OCR is marked.
- Normal Markdown output ends with the HTML conversion question.
- Direct HTML requests produce a standalone page with Japanese TTS controls.
