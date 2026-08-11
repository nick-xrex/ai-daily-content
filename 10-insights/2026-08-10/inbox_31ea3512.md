---
id: inbox_31ea3512
date: 2026-08-10
source_ref: "[[00-inbox/2026-08-10/2208-medium-tag-claude-examples-fix-the-format-and-break-the-re-e4ab]]"
title: "Examples Fix The Format And Break The Reasoning"
url: https://learn-ai-prompting.medium.com/examples-fix-the-format-and-break-the-reasoning-42f932a9e960?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-08-10T19:21:07+00:00
fetched_at: 2026-08-11T00:57:13.903947+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章深入探討在 prompt 中加入範例（in-context examples）的雙面效果。增加範例確實能快速修正輸出格式（正確標籤、預期長度等），但同時會削弱模型的推理能力與邏輯嚴謹性。作者指出這是經典的 trade-off：為了格式一致而犧牲推理深度。文章提示開發者在設計 prompt 時需明確權衡格式約束與推理質量之間的衝突，而非盲目追求格式完美。對於需要複雜邏輯的任務，格式範例可能適得其反。"
key_points:
  - "In-context examples 能快速修正輸出格式，但會削弱推理能力——增加範例數量與推理質量呈反向關係"
  - "格式 vs 推理是 prompt 設計的核心 trade-off，需根據任務特性做出明確選擇"
  - "複雜推理任務應謹慎使用範例，以保護邏輯嚴謹性"
tags: [prompt-engineering, in-context-examples, format-vs-reasoning, llm-behavior, trade-off]
topics: []
importance: 4
novelty: 2
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Examples Fix The Format And Break The Reasoning

文章深入探討在 prompt 中加入範例（in-context examples）的雙面效果。增加範例確實能快速修正輸出格式（正確標籤、預期長度等），但同時會削弱模型的推理能力與邏輯嚴謹性。作者指出這是經典的 trade-off：為了格式一致而犧牲推理深度。文章提示開發者在設計 prompt 時需明確權衡格式約束與推理質量之間的衝突，而非盲目追求格式完美。對於需要複雜邏輯的任務，格式範例可能適得其反。

### 重點
- In-context examples 能快速修正輸出格式，但會削弱推理能力——增加範例數量與推理質量呈反向關係
- 格式 vs 推理是 prompt 設計的核心 trade-off，需根據任務特性做出明確選擇
- 複雜推理任務應謹慎使用範例，以保護邏輯嚴謹性

**原文：** [medium-tag-claude](https://learn-ai-prompting.medium.com/examples-fix-the-format-and-break-the-reasoning-42f932a9e960?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

You added a couple of examples to your prompt and the output started coming back in the right shape. Correct labels, right length, no&#x2026; Continue reading on Medium »

</details>