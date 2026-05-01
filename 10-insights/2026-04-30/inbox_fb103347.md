---
id: inbox_fb103347
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-simon-willison-codex-cli-0-128-0-adds-goal-bd83]]"
title: "Codex CLI 0.128.0 adds /goal"
url: https://simonwillison.net/2026/Apr/30/codex-goals/#atom-everything
source: simon-willison
published_at: 2026-04-30T23:23:17+00:00
fetched_at: 2026-05-01T13:03:04.415907+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 的 Codex CLI 版本 0.128.0 新增 `/goal` 功能，實現類似 Ralph loop 的自動循環機制。使用者可設定一個目標，CLI 會自動重複執行直到評估目標完成或 token 預算耗盡。該功能主要透過自動注入 goals/continuation.md 和 goals/budget_limit.md 提示實現。這個設計將使用者的高階意圖與代理執行分離，讓開發者能定義長期目標並交由代理自動推進。"
key_points:
  - "Codex CLI 0.128.0 實現目標驅動的自動循環執行"
  - "透過提示工程（continuation.md 與 budget_limit.md）在每輪末端自動注入決策邏輯"
  - "支援自訂 token 預算限制，避免無限執行"
tags: [codex-cli, agentic-engineering, prompt-engineering, goal-driven, openai]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Codex CLI 0.128.0 adds /goal

OpenAI 的 Codex CLI 版本 0.128.0 新增 `/goal` 功能，實現類似 Ralph loop 的自動循環機制。使用者可設定一個目標，CLI 會自動重複執行直到評估目標完成或 token 預算耗盡。該功能主要透過自動注入 goals/continuation.md 和 goals/budget_limit.md 提示實現。這個設計將使用者的高階意圖與代理執行分離，讓開發者能定義長期目標並交由代理自動推進。

### 重點
- Codex CLI 0.128.0 實現目標驅動的自動循環執行
- 透過提示工程（continuation.md 與 budget_limit.md）在每輪末端自動注入決策邏輯
- 支援自訂 token 預算限制，避免無限執行

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/30/codex-goals/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://github.com/openai/codex/releases/tag/rust-v0.128.0">Codex CLI 0.128.0 adds /goal</a></strong></p>
The latest version of OpenAI's Codex CLI coding agent adds their own version of the <a href="https://ghuntley.com/ralph/">Ralph loop</a>: you can now set a <code>/goal</code> and Codex will keep on looping until it evaluates that the goal has been completed... or the configured token budget has been exhausted.</p>
<p>It looks like the feature is mainly implemented though the <a href="https://github.com/openai/codex/blob/6014b6679ffbd92eeddffa3ad7b4402be6a7fefe/codex-rs/core/templates/goals/continuation.md">goals/continuation.md</a> and <a href="https://github.com/openai/codex/blob/6014b6679ffbd92eeddffa3ad7b4402be6a7fefe/codex-rs/core/templates/goals/budget_limit.md">goals/budget_limit.md</a> prompts, which are automatically injected at the end of a turn.

    <p><small></small>Via <a href="https://twitter.com/fcoury/status/2049917871799636201">@fcoury</a></small></p>


    <p>Tags: <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/openai">openai</a>, <a href="https://simonwillison.net/tags/prompt-engineering">prompt-engineering</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/coding-agents">coding-agents</a>, <a href="https://simonwillison.net/tags/system-prompts">system-prompts</a>, <a href="https://simonwillison.net/tags/codex-cli">codex-cli</a>, <a href="https://simonwillison.net/tags/agentic-engineering">agentic-engineering</a></p>

</details>