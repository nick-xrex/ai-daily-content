---
id: inbox_9ba714c9
date: 2026-04-18
source_ref: "[[00-inbox/.../inbox_9ba714c9]]"
title: "Changes in the system prompt between Claude Opus 4.6 and 4.7"
url: https://simonwillison.net/2026/Apr/18/opus-system-prompt/#atom-everything
source: (resumed)
published_at: 2026-04-18T23:59:40+00:00
fetched_at: 2026-04-21T02:36:17.455466+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 詳細分析 Claude Opus 4.7（4/16 發布）相比 4.6（2/5 發布）的系統提示變更。核心改動：新增 Claude in PowerPoint agent；兒童安全指示大幅擴展並用 `<critical_child_safety_instructions>` 標籤；強化主動性—鼓勵在資訊不完整時先嘗試而非先問，並在下「無存取」結論前先用 tool_search 檢查可用工具；強調簡潔回應；移除舊版行為限制（emotes、「genuinely」等）；新增 disordered eating 特定指引；防守「強制 yes/no」截圖攻擊。知識截點更新至 2026/1，移除 Trump 總統說明。系統可用工具逾 20 項，包括 tool_search、bash_tool、create_file、image_search 等。"
key_points:
  - "tool_search 機制：Claude 必在聲稱「無法存取」前檢查是否有可用工具解決問題"
  - "行為調整：減少主動要求延續、強調主動嘗試解決、簡化冗長回應、強化安全防守"
  - "安全加固：disordered eating 防守、截圖攻擊防衛、兒童安全擴展"
tags: [claude, system-prompts, opus-4.7, behavior-changes, safety]
topics: [foundation_models.claude]
importance: 5
novelty: 5
deep_dive_candidate: true
deep_dive_approved: false
---

## Changes in the system prompt between Claude Opus 4.6 and 4.7

Simon Willison 詳細分析 Claude Opus 4.7（4/16 發布）相比 4.6（2/5 發布）的系統提示變更。核心改動：新增 Claude in PowerPoint agent；兒童安全指示大幅擴展並用 `<critical_child_safety_instructions>` 標籤；強化主動性—鼓勵在資訊不完整時先嘗試而非先問，並在下「無存取」結論前先用 tool_search 檢查可用工具；強調簡潔回應；移除舊版行為限制（emotes、「genuinely」等）；新增 disordered eating 特定指引；防守「強制 yes/no」截圖攻擊。知識截點更新至 2026/1，移除 Trump 總統說明。系統可用工具逾 20 項，包括 tool_search、bash_tool、create_file、image_search 等。

### 重點
- tool_search 機制：Claude 必在聲稱「無法存取」前檢查是否有可用工具解決問題
- 行為調整：減少主動要求延續、強調主動嘗試解決、簡化冗長回應、強化安全防守
- 安全加固：disordered eating 防守、截圖攻擊防衛、兒童安全擴展

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/18/opus-system-prompt/#atom-everything)