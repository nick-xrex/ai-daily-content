---
id: inbox_db033e6e
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0248-medium-tag-claude-the-four-techniques-that-make-claude-act-c0bd]]"
title: "The Four Techniques That Make Claude Actually Listen to You"
url: https://medium.com/@iamabhinav30/the-four-techniques-that-make-claude-actually-listen-to-you-03acc82ce00f?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-04-28T01:09:28+00:00
fetched_at: 2026-04-28T03:05:50.183297+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文整理了四種讓 Claude 更好理解指令的核心技巧：(1) 明確直接的措辭和行動動詞，(2) 具體的需求清單（如「限制烹飪時間 30 分鐘」），(3) 使用 XML 標籤（`<input>`, `<context>` 等）區隔指令和資料，(4) 提供輸入輸出範例進行少量示例學習。這四項技巧組合使用時產生「大於各部分之和」的效果，幾乎消除了所有歧義。來自 Anthropic 的實踐指南。"
key_points:
  - "XML 標籤結構分離指令與工作素材，根除歧義"
  - "單個輸入輸出範例勝過一段說明文字，更準確校準語氣、長度和格式"
  - "四種技巧組合效果非線性，質量躍升"
tags: [prompt-engineering, claude, instruction-design, xml-tags, few-shot-learning]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The Four Techniques That Make Claude Actually Listen to You

本文整理了四種讓 Claude 更好理解指令的核心技巧：(1) 明確直接的措辭和行動動詞，(2) 具體的需求清單（如「限制烹飪時間 30 分鐘」），(3) 使用 XML 標籤（`<input>`, `<context>` 等）區隔指令和資料，(4) 提供輸入輸出範例進行少量示例學習。這四項技巧組合使用時產生「大於各部分之和」的效果，幾乎消除了所有歧義。來自 Anthropic 的實踐指南。

### 重點
- XML 標籤結構分離指令與工作素材，根除歧義
- 單個輸入輸出範例勝過一段說明文字，更準確校準語氣、長度和格式
- 四種技巧組合效果非線性，質量躍升

**原文：** [medium-tag-claude](https://medium.com/@iamabhinav30/the-four-techniques-that-make-claude-actually-listen-to-you-03acc82ce00f?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@iamabhinav30/the-four-techniques-that-make-claude-actually-listen-to-you-03acc82ce00f?source=rss------claude-5"><img src="https://cdn-images-1.medium.com/max/702/1*CkFl641oHVdPVofnQr2V-g.png" width="702" /></a></p><p class="medium-feed-snippet">Most prompts fail for the same reason. Here&#x2019;s a practical guide to the craft of writing instructions that work &#x2014; drawn from Anthropic&#x2019;s&#x2026;</p><p class="medium-feed-link"><a href="https://medium.com/@iamabhinav30/the-four-techniques-that-make-claude-actually-listen-to-you-03acc82ce00f?source=rss------claude-5">Continue reading on Medium »</a></p></div>

</details>