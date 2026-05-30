---
id: inbox_7ea00382
date: 2026-05-29
source_ref: "[[00-inbox/2026-05-29/0216-ruflo-releases-v3-10-10-hermes-agent-tier-1-adoptions-p-03e3]]"
title: "v3.10.10 — Hermes-Agent Tier-1 adoptions (prompt caching, reasoning scrub, tool-loop breaker)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.10
source: ruflo-releases
published_at: 2026-05-29T18:59:04+00:00
fetched_at: 2026-05-30T02:24:09.162894+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.10 從 NousResearch/Hermes-Agent 採納 3 個高信度、可直接使用的模式。Prompt caching 在 agent_execute 直接 Anthropic 呼叫中標記系統提示為臨時快取斷點，快取輸入 token 約 90% 折扣（5分鐘 TTL），同策略應用於 @claude-flow/providers；Reasoning-tag scrub 在 DISTILL 前移除 think/thinking/reasoning/REASONING_SCRATCHPAD 區塊，防止延伸思考 token 污染模式嵌入；Tool-loop circuit breaker 在同一命令失敗 3 次時預警、5 次時阻止，提供恢復提示。CI 29/29 綠燈。"
key_points:
  - "Prompt caching 在快取層級實現 ~90% 折扣（TTL 5 分鐘），system prompt 標記為臨時斷點"
  - "Reasoning-tag scrub 移除 <think>/<thinking> 等標籤避免污染嵌入梯度"
  - "Tool-loop circuit breaker 3 warning / 5 block 機制阻止命令失敗迴圈"
tags: [prompt-caching, extended-thinking, tool-safety]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.10 — Hermes-Agent Tier-1 adoptions (prompt caching, reasoning scrub, tool-loop breaker)

Ruflo v3.10.10 從 NousResearch/Hermes-Agent 採納 3 個高信度、可直接使用的模式。Prompt caching 在 agent_execute 直接 Anthropic 呼叫中標記系統提示為臨時快取斷點，快取輸入 token 約 90% 折扣（5分鐘 TTL），同策略應用於 @claude-flow/providers；Reasoning-tag scrub 在 DISTILL 前移除 think/thinking/reasoning/REASONING_SCRATCHPAD 區塊，防止延伸思考 token 污染模式嵌入；Tool-loop circuit breaker 在同一命令失敗 3 次時預警、5 次時阻止，提供恢復提示。CI 29/29 綠燈。

### 重點
- Prompt caching 在快取層級實現 ~90% 折扣（TTL 5 分鐘），system prompt 標記為臨時斷點
- Reasoning-tag scrub 移除 <think>/<thinking> 等標籤避免污染嵌入梯度
- Tool-loop circuit breaker 3 warning / 5 block 機制阻止命令失敗迴圈

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.10)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ruflo v3.10.10 — Hermes-Agent Tier-1 adoptions 
 The 3 small, high-confidence, in-repo patterns worth borrowing from NousResearch/Hermes-Agent , from a deep-research capability map (the rest were SKIP or ADR-gated; the map also produced 5 corrections to ADR-113/ #1907 ). 
 
 Prompt caching — agent_execute 's direct Anthropic call now marks the system prompt as an ephemeral cache breakpoint (~90% discount on cached input tokens, 5-min TTL). Same strategy applied to @claude-flow/providers (gated by config.promptCache , default on). 
 Reasoning-tag scrub — trajectory action/result are stripped of &lt;think&gt; / &lt;thinking&gt; / &lt;reasoning&gt; / &lt;REASONING_SCRATCHPAD&gt; blocks before DISTILL, so extended-thinking tokens don't contaminate the pattern embeddings the learning loop relies on. Boundary-gated. 
 Tool-loop circuit breaker — pre-command warns at 3 / blocks at 5 consecutive failures of the same command (with a recovery hint), fed by post-command . Orthogonal to the injection-focused security guardrail; advisory by default. 
 
 Honest note: @claude-flow/providers is not consumed by the cli, so the cli-effective prompt-caching fix is in agent-execute-core.ts ; the providers change ships on its own cadence. 
 CI 29/29 green; all three packages at 3.10.10 (latest/alpha/v3alpha lockstep). 
 🤖 Generated with RuFlo

</details>