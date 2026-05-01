---
id: inbox_8b310fd6
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-claudeai-question-about-performance-in-long-conte-dad3]]"
title: "Question about performance in long context"
url: https://www.reddit.com/r/ClaudeAI/comments/1t0beap/question_about_performance_in_long_context/
source: reddit-claudeai
published_at: 2026-04-30T22:39:54+00:00
fetched_at: 2026-05-01T13:41:17.736464+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reddit 用戶發問 Claude 訂閱版本的 1M token context window 在實際應用中的表現如何，以及模型在該規模下是否能達到預期效能。提出三個核心問題：(1) 實際使用的 context 大小量測方式（詞、字符或 tokens）；(2) 在何處開始出現效能下降、幻覺或 Lost Context Retrieval (LCR) 問題；(3) 不同 Claude 模型間的長 context 效能差異。反映開發者社群對 Claude 超長 context 真實表現的疑慮。"
key_points:
  - "Claude 訂閱模型支援 1M token context，但實際效能邊界未被清晰量化"
  - "長 context 下的幻覺率與 LCR 是衡量效能下降的關鍵指標"
  - "不同 Claude 模型版本在超長 context 穩定性上可能存在差異"
tags: [claude, long-context, performance]
topics: [foundation_models.claude]
importance: 2
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Question about performance in long context

Reddit 用戶發問 Claude 訂閱版本的 1M token context window 在實際應用中的表現如何，以及模型在該規模下是否能達到預期效能。提出三個核心問題：(1) 實際使用的 context 大小量測方式（詞、字符或 tokens）；(2) 在何處開始出現效能下降、幻覺或 Lost Context Retrieval (LCR) 問題；(3) 不同 Claude 模型間的長 context 效能差異。反映開發者社群對 Claude 超長 context 真實表現的疑慮。

### 重點
- Claude 訂閱模型支援 1M token context，但實際效能邊界未被清晰量化
- 長 context 下的幻覺率與 LCR 是衡量效能下降的關鍵指標
- 不同 Claude 模型版本在超長 context 穩定性上可能存在差異

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t0beap/question_about_performance_in_long_context/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Hey, all! This is a question for everyone, but I'd really like to hear particularly from people that push the limits of the context window. I could be wrong, but I think the context window for all subscription models is 1 million tokens. But I'm skeptical about model performance at that size. So, for those of you who are chatting in extremely long-context chats:</p> <ol> <li>Do you have any sense of just how long your chats are? Words, characters, tokens? Any way of measuring would be helpful</li> <li>At what point have you experienced degraded performance, excessive hallucinations, and LCRs?</li> <li>Do you see a significant difference in long-context performance between the models?</li> </ol> <p>Thanks so much guys!</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/SumDoodWiddaName"> /u/SumDoodWiddaName </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t0beap/question_about_performance_in_long_context/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t0beap/question_about_performance_in_long_context/">[comments]</a></span>

</details>