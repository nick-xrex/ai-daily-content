---
id: inbox_545b788b
date: 2026-07-19
source_ref: "[[00-inbox/.../inbox_545b788b]]"
title: "Onboarding Agent from Scratch. Part 4: Prompts You Can Test, Not Just Tweak"
url: https://medium.com/@spodsky/onboarding-agent-from-scratch-part-4-prompts-you-can-test-not-just-tweak-81059de2783e?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-07-19T18:42:27+00:00
fetched_at: 2026-07-20T01:00:20.922418+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "該文為「從零開始的 Onboarding Agent」系列第 4 部分，重點是讓 prompt 能被測試而非僅能手工調整。第 3 階段透過強制工具使用在 prompt 中建立結構化契約：保證每次都返回 {answer, source, confidence} 的結構。這個方法利用工具使用的確定性強制 agent 遵守輸出格式，使 prompt 工程從試錯轉向可驗證的測試驅動開發。通過架構約束而非 prompt 措辭提升輸出一致性，是構建可靠 AI 系統的關鍵原則。"
key_points:
  - "強制工具使用作為契約機制：透過工具定義確保 agent 輸出結構（answer、source、confidence）一致"
  - "從調整轉向測試：prompt 工程轉向測試驅動開發，可驗證輸出品質而非反覆調整文案"
  - "架構約束勝過文案：工具使用提供比 prompt 指令更強的行為約束力，提升可靠性"
tags: [claude-agent, prompt-engineering, testing, tool-use, onboarding]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 2
insight_quality: 5
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Onboarding Agent from Scratch. Part 4: Prompts You Can Test, Not Just Tweak

該文為「從零開始的 Onboarding Agent」系列第 4 部分，重點是讓 prompt 能被測試而非僅能手工調整。第 3 階段透過強制工具使用在 prompt 中建立結構化契約：保證每次都返回 {answer, source, confidence} 的結構。這個方法利用工具使用的確定性強制 agent 遵守輸出格式，使 prompt 工程從試錯轉向可驗證的測試驅動開發。通過架構約束而非 prompt 措辭提升輸出一致性，是構建可靠 AI 系統的關鍵原則。

### 重點
- 強制工具使用作為契約機制：透過工具定義確保 agent 輸出結構（answer、source、confidence）一致
- 從調整轉向測試：prompt 工程轉向測試驅動開發，可驗證輸出品質而非反覆調整文案
- 架構約束勝過文案：工具使用提供比 prompt 指令更強的行為約束力，提升可靠性

**原文：** [medium-tag-claude](https://medium.com/@spodsky/onboarding-agent-from-scratch-part-4-prompts-you-can-test-not-just-tweak-81059de2783e?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---claude-5"
author: "Serge"
published_at: 2026-07-19T18:42:27+00:00
fetched_at: 2026-07-19T22:00:45.557384+00:00
content_hash: "cc1541ba7e5ccfcfbd4d0bcb1231b56d3208e16add91486b2c34a0c657564b44"
lang: en
caption_quality: None
raw: true
topics: []
---

# Onboarding Agent from Scratch. Part 4: Prompts You Can Test, Not Just Tweak

Stage 3 put the shape of the answer under contract: forced tool use guarantees {answer, source, confidence} comes back every time. The&#x2026; Continue reading on Medium »

</details>