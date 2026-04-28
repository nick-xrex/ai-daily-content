---
id: inbox_ed3c9e6d
date: 2026-04-21
source_ref: "[[00-inbox/.../inbox_ed3c9e6d]]"
title: "Claude Code Is Not Broken. You Are Drowning It."
url: https://medium.com/@nuno.roberto/claude-code-is-not-broken-you-are-drowning-it-7d7635765c10?source=rss------artificial_intelligence-5
source: medium-tag-ai
published_at: 2026-04-21T21:07:49+00:00
fetched_at: 2026-04-28T03:31:27.219699+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Nuno Roberto 指出 Claude Code 性能下降的真正原因不在工具本身，而在於上下文管理不當。他透過親身經歷揭示：Claude 在前 30 分鐘表現卓越，但到 90 分鐘時開始漂移，提出與早期規範相悖的程式碼建議。隨著對話歷史累積，AI 逐漸失去對已建立慣例和決策的追蹤能力，導致建議不一致。問題根源不在 prompt 品質，而在開發者如何戰略性管理對話量，以維持模型的一致性和精度。這是一個架構洞察：成功使用 Claude Code 取決於上下文壽命管理，而非完美的初始 prompt。"
key_points:
  - "Claude Code 性能衰退源於累積上下文對一致性的侵蝕，而非模型能力不足；在 ~90 分鐘對話後開始出現決策漂移"
  - "核心問題：AI 隨著對話長度增加而遺忘早期規範，導致後期建議與先前規格矛盾"
  - "解決方案：戰略性管理對話上下文的廣度，而非依賴 prompt 工程；重點不在寫完美指令，而在維持模型的認知連貫性"
tags: [claude-code, context-management, prompt-engineering, llm-performance]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude Code Is Not Broken. You Are Drowning It.

Nuno Roberto 指出 Claude Code 性能下降的真正原因不在工具本身，而在於上下文管理不當。他透過親身經歷揭示：Claude 在前 30 分鐘表現卓越，但到 90 分鐘時開始漂移，提出與早期規範相悖的程式碼建議。隨著對話歷史累積，AI 逐漸失去對已建立慣例和決策的追蹤能力，導致建議不一致。問題根源不在 prompt 品質，而在開發者如何戰略性管理對話量，以維持模型的一致性和精度。這是一個架構洞察：成功使用 Claude Code 取決於上下文壽命管理，而非完美的初始 prompt。

### 重點
- Claude Code 性能衰退源於累積上下文對一致性的侵蝕，而非模型能力不足；在 ~90 分鐘對話後開始出現決策漂移
- 核心問題：AI 隨著對話長度增加而遺忘早期規範，導致後期建議與先前規格矛盾
- 解決方案：戰略性管理對話上下文的廣度，而非依賴 prompt 工程；重點不在寫完美指令，而在維持模型的認知連貫性

**原文：** [medium-tag-ai](https://medium.com/@nuno.roberto/claude-code-is-not-broken-you-are-drowning-it-7d7635765c10?source=rss------artificial_intelligence-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---artificial_intelligence-5"
author: "Nuno Roberto"
published_at: 2026-04-21T21:07:49+00:00
fetched_at: 2026-04-21T21:46:28.218563+00:00
content_hash: "7fb7ad2e7f550fba6c4f44c0d051938bf870e04c1191a876328dde09e4c39cff"
lang: en
caption_quality: None
raw: true
topics: []
---

# Claude Code Is Not Broken. You Are Drowning It.

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@nuno.roberto/claude-code-is-not-broken-you-are-drowning-it-7d7635765c10?source=rss------artificial_intelligence-5"><img src="https://cdn-images-1.medium.com/max/2600/1*2dZV5QJuOzJHhDO-NUXkhA.png" width="2752" /></a></p><p class="medium-feed-snippet">What separates a frustrating Claude Code session from a magical one is not the quality of your prompt.</p><p class="medium-feed-link"><a href="https://medium.com/@nuno.roberto/claude-code-is-not-broken-you-are-drowning-it-7d7635765c10?source=rss------artificial_intelligence-5">Continue reading on Medium »</a></p></div>

</details>