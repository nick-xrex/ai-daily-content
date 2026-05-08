---
id: inbox_0d6b9b1b
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-claudeai-decline-in-opus-4-7-max-quality-c700]]"
title: "Decline in Opus 4.7 Max Quality"
url: https://www.reddit.com/r/ClaudeAI/comments/1t6o3mh/decline_in_opus_47_max_quality/
source: reddit-claudeai
published_at: 2026-05-07T21:28:09+00:00
fetched_at: 2026-05-08T08:12:40.466446+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者報告同一 UI 組件（Pre-Paywall modal）實現品質在短期內下降：兩週前 Opus 4.7 首次嘗試即成功實現，最近重新實現同樣組件卻多次失敗。用戶嘗試多種優化手段（context 壓縮、/effort max、ultrathink）均無改善，最終改用 GPT 5.5 後於兩次迭代內解決。直指 Opus 4.7 可能存在性能退化或穩定性問題。"
key_points:
  - "相同任務性能下降時間短：兩週前一次成功，現在多次失敗（同一 modal、同一 Figma 參考）"
  - "優化手段失效：context 壓縮、/effort max、ultrathink 皆無法改善結果"
  - "跨模型對比：GPT 5.5 在兩次迭代內解決，形成鮮明性能差異"
tags: [opus-4.7, model-degradation, quality-regression, performance-issue]
topics: [foundation_models.claude]
importance: 4
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Decline in Opus 4.7 Max Quality

使用者報告同一 UI 組件（Pre-Paywall modal）實現品質在短期內下降：兩週前 Opus 4.7 首次嘗試即成功實現，最近重新實現同樣組件卻多次失敗。用戶嘗試多種優化手段（context 壓縮、/effort max、ultrathink）均無改善，最終改用 GPT 5.5 後於兩次迭代內解決。直指 Opus 4.7 可能存在性能退化或穩定性問題。

### 重點
- 相同任務性能下降時間短：兩週前一次成功，現在多次失敗（同一 modal、同一 Figma 參考）
- 優化手段失效：context 壓縮、/effort max、ultrathink 皆無法改善結果
- 跨模型對比：GPT 5.5 在兩次迭代內解決，形成鮮明性能差異

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t6o3mh/decline_in_opus_47_max_quality/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I’m currently working on two different projects, and both use the same Pre-Paywall modal. See the Figma file below: https://preview.redd.it/d7ri53vo9szg1.jpg?width=730&amp;format=pjpg&amp;auto=webp&amp;s=a722bcd11caaa0b068f2c6af360cea687af76a17 I implemented the first one two weeks ago, and without any additional prompting, it was implemented correctly. You can see the result below: https://preview.redd.it/j4mr6k8u8szg1.jpg?width=919&amp;format=pjpg&amp;auto=webp&amp;s=da920a7c1d0eefa951886235e0ca996cfb6fc43e Last night, I started implementing the same modal in another project, and for me, it became clear evidence of a decline in the quality of Opus 4.7. I compacted the context window, used /effort max , and even added ultrathink , but none of that helped. The result I got is shown below https://preview.redd.it/x87okntv8szg1.png?width=1260&amp;format=png&amp;auto=webp&amp;s=d1d29875df6b947e21bc6647c0725171084d8c20 Note: I have used GPT 5.5 to fix it; after 2 prompts, it was ok... &#32; submitted by &#32; /u/serd2r [link] &#32; [comments]

</details>