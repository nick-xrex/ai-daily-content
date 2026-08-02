---
id: inbox_af915b2b
date: 2026-08-01
source_ref: "[[00-inbox/.../inbox_af915b2b]]"
title: "Coding Agents Don’t Need Bigger Context Windows — They Need a Context Compiler"
url: https://towardsdatascience.com/coding-agents-dont-need-bigger-context-windows-they-need-a-context-compiler/
source: medium-towards-data-science
published_at: 2026-08-01T15:00:00+00:00
fetched_at: 2026-08-02T03:41:20.216704+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章主張 coding agents 的瓶頸不在 context window 大小，而在 prompt 構造策略。傳統做法是盲目聚合代碼，導致無關信息與相關代碼搶奪模型注意力，最終 window 填滿時 agent 被迫壓縮自身記憶。新思路是將 prompt 構造視為編譯器：不是「加入所有代碼」，而是「決定保留什麼、縮小什麼、丟棄什麼」。這一框架從質量而非數量優化 context，避免了傳統「堆 token」方案的遞減收益。應用此原則可顯著改善 agent 在複雜任務中的穩定性和準確性。

```mermaid
graph LR
    A[\"傳統做法<br/>Gather All Files\"] --> B[\"希望模型自己理解\"]
    B --> C[\"Context 質量下降<br/>遺忘中途任務\"]
    
    D[\"Context Compiler\"] --> E[\"分析代碼相關性\"]
    E --> F[\"保留/縮小/丟棄<br/>決策\"]
    F --> G[\"精準 Prompt\"]
    G --> H[\"Agent 穩定性提升\"]
```"
key_points:
  - "Context compiler 框架：用編譯器邏輯決定 prompt 內容（保留/縮小/丟棄），而非堆疊所有代碼"
  - "問題根因：window 填滿時 agent 自我壓縮記憶，導致『遺忘』"
  - "質量優化 > 數量堆積：關鍵是內容選擇策略，不是更大的 window"
tags: [coding-agents, prompt-optimization, context-management, agent-architecture]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Coding Agents Don’t Need Bigger Context Windows — They Need a Context Compiler

文章主張 coding agents 的瓶頸不在 context window 大小，而在 prompt 構造策略。傳統做法是盲目聚合代碼，導致無關信息與相關代碼搶奪模型注意力，最終 window 填滿時 agent 被迫壓縮自身記憶。新思路是將 prompt 構造視為編譯器：不是「加入所有代碼」，而是「決定保留什麼、縮小什麼、丟棄什麼」。這一框架從質量而非數量優化 context，避免了傳統「堆 token」方案的遞減收益。應用此原則可顯著改善 agent 在複雜任務中的穩定性和準確性。

```mermaid
graph LR
    A["傳統做法<br/>Gather All Files"] --> B["希望模型自己理解"]
    B --> C["Context 質量下降<br/>遺忘中途任務"]
    
    D["Context Compiler"] --> E["分析代碼相關性"]
    E --> F["保留/縮小/丟棄<br/>決策"]
    F --> G["精準 Prompt"]
    G --> H["Agent 穩定性提升"]
```

### 重點
- Context compiler 框架：用編譯器邏輯決定 prompt 內容（保留/縮小/丟棄），而非堆疊所有代碼
- 問題根因：window 填滿時 agent 自我壓縮記憶，導致『遺忘』
- 質量優化 > 數量堆積：關鍵是內容選擇策略，不是更大的 window

**原文：** [medium-towards-data-science](https://towardsdatascience.com/coding-agents-dont-need-bigger-context-windows-they-need-a-context-compiler/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Coding Agents Don’t Need Bigger Context Windows — They Need a Context Compiler

Most coding agents treat prompt construction like retrieval: gather more files, add more context, hope the model figures it out. But that approach breaks down fast. As context grows, irrelevant code competes for attention, and when the window fills, agents start compressing their own memory—often mid-task. What looks like “forgetting” is usually just degraded context. This article explores a different approach: treating prompt construction like a compiler that decides what to keep, what to reduce, and what to discard entirely. 
 The post Coding Agents Don’t Need Bigger Context Windows — They Need a Context Compiler appeared first on Towards Data Science .

</details>