---
id: inbox_ba8db7c8
date: 2026-05-07
source_ref: "[[00-inbox/.../inbox_ba8db7c8]]"
title: "Agents need control flow, not more prompts"
url: https://bsuh.bearblog.dev/agents-need-control-flow/
source: hackernews
published_at: 2026-05-07T16:43:35+00:00
fetched_at: 2026-05-08T08:38:04.299403+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AI agent 的可靠性瓶頸不在 prompt 工程，而在於**確定性控制流的軟體架構**。文章指出單純複雜化 prompt（例如加上 MANDATORY 或 DO NOT SKIP）無法確保行為的可預測性；傳統軟體透過可組合的模組與函式達到可驗證的行為，LLM 應被視為更大系統內的組件而非決策核心。作者提出三種錯誤管理策略：維持人工監督、執行完成後驗證、或無驗證接受（已被排除）。核心洞察是將語言模型納入確定性系統框架，才能避免「快速達到錯誤結論」的陷阱。"
key_points:
  - "Prompt 複雜度天花板：當需要加上 MANDATORY/DO NOT SKIP 標籤時表示已超越 prompt 工程的極限"
  - "軟體優於提示工程：傳統代碼透過可組合模組實現可預測行為；agent 應由確定性控制流而非 prompt 鏈驅動"
  - "三層錯誤防線：人工監督全程 OR 事後完整驗證 OR 無驗證接受（最危險），無法只靠 prompt 避免沉默失敗"
tags: [agent-architecture, control-flow, prompt-engineering, system-design]
topics: [agents.mcp]
importance: 5
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Agents need control flow, not more prompts

AI agent 的可靠性瓶頸不在 prompt 工程，而在於**確定性控制流的軟體架構**。文章指出單純複雜化 prompt（例如加上 MANDATORY 或 DO NOT SKIP）無法確保行為的可預測性；傳統軟體透過可組合的模組與函式達到可驗證的行為，LLM 應被視為更大系統內的組件而非決策核心。作者提出三種錯誤管理策略：維持人工監督、執行完成後驗證、或無驗證接受（已被排除）。核心洞察是將語言模型納入確定性系統框架，才能避免「快速達到錯誤結論」的陷阱。

### 重點
- Prompt 複雜度天花板：當需要加上 MANDATORY/DO NOT SKIP 標籤時表示已超越 prompt 工程的極限
- 軟體優於提示工程：傳統代碼透過可組合模組實現可預測行為；agent 應由確定性控制流而非 prompt 鏈驅動
- 三層錯誤防線：人工監督全程 OR 事後完整驗證 OR 無驗證接受（最危險），無法只靠 prompt 避免沉默失敗

**原文：** [hackernews](https://bsuh.bearblog.dev/agents-need-control-flow/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Agents need control flow, not more prompts

</details>