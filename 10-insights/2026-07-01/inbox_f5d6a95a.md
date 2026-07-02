---
id: inbox_f5d6a95a
date: 2026-07-01
source_ref: "[[00-inbox/.../inbox_f5d6a95a]]"
title: "v13.9.2"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.9.2
source: claude-mem-releases
published_at: 2026-07-01T04:52:30+00:00
fetched_at: 2026-07-02T01:14:54.744818+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.9.2 修正 OpenAICompatibleProvider 中的客户端上下文截断漏洞。该 bug 對對話历史施加硬編碼的 20 條訊息和 100k 令牌上限，但實際在約 12k 令牌時就誤觸發，導致悄無聲息地破壞會話歷史，卻被誤標為「成本控制」。本次更新完全移除了客户端截断邏輯（truncateHistory()、相關常數定義及三個环境变量），改由模型自身負責管理上下文窗口。驗證結果：TypeScript 編譯完全無誤，2248 項測試全數通過，構建流程正常。"
key_points:
  - "硬編碼截斷 bug：20 訊息 + 100k token 上限，實際 ~12k tokens 時就誤觸（遠低於模型容量），導致無聲式歷史破壞"
  - "完全移除客户端截断：刪除 truncateHistory() 及 CLAUDE_MEM_{GEMINI,OPENROUTER}_MAX_* 設定，改由 provider 自管上下文"
  - "驗證無誤：tsc clean，2248 tests passing，build-and-sync clean"
tags: [claude-mem, bug-fix, context-window, provider]
topics: [foundation_models.claude]
importance: 4
novelty: 2
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.9.2

claude-mem v13.9.2 修正 OpenAICompatibleProvider 中的客户端上下文截断漏洞。该 bug 對對話历史施加硬編碼的 20 條訊息和 100k 令牌上限，但實際在約 12k 令牌時就誤觸發，導致悄無聲息地破壞會話歷史，卻被誤標為「成本控制」。本次更新完全移除了客户端截断邏輯（truncateHistory()、相關常數定義及三個环境变量），改由模型自身負責管理上下文窗口。驗證結果：TypeScript 編譯完全無誤，2248 項測試全數通過，構建流程正常。

### 重點
- 硬編碼截斷 bug：20 訊息 + 100k token 上限，實際 ~12k tokens 時就誤觸（遠低於模型容量），導致無聲式歷史破壞
- 完全移除客户端截断：刪除 truncateHistory() 及 CLAUDE_MEM_{GEMINI,OPENROUTER}_MAX_* 設定，改由 provider 自管上下文
- 驗證無誤：tsc clean，2248 tests passing，build-and-sync clean

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.9.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.9.2

Bug Fix 
 Removed client-side context truncation from the provider layer. 
 The OpenAICompatibleProvider applied a sliding-window truncation to conversation history — a hardcoded 20-message cap and a 100k-token "safety" limit layered on top of the model's own context window. In practice it fired on message count alone, dropping conversation messages at ~12k tokens (nowhere near the token limit) and silently corrupting history, mislabeled as "runaway cost" prevention. This broke setups whose real model context window bore no relation to those hardcoded assumptions. 
 The full conversation history is now sent to the provider, which owns its own context window. 
 Removed 
 
 OpenAICompatibleProvider.truncateHistory() and the requireNonEmptyToTruncate flag 
 truncateHistoryForOpenRouter / truncateHistoryForGemini wrappers and their message/token constants 
 CLAUDE_MEM_{GEMINI,OPENROUTER}_MAX_CONTEXT_MESSAGES / _MAX_TOKENS settings, defaults, and validation 
 Related tests, docs, and installer references 
 
 Merged in #3096 . Verified: tsc clean, 2248 tests passing, build-and-sync clean.

</details>