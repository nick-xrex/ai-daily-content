---
id: inbox_8e64b793
date: 2026-05-01
source_ref: "[[00-inbox/.../inbox_8e64b793]]"
title: "Claude Code usage spike from long-context cache writes?"
url: https://www.reddit.com/r/ClaudeAI/comments/1t0fuwj/claude_code_usage_spike_from_longcontext_cache/
source: reddit-claudeai
published_at: 2026-05-01T01:56:53+00:00
fetched_at: 2026-05-01T14:06:33.037007+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code Pro 使用者超出 5 小時額度後檢查用量日誌，發現長上下文會話（>150k token）與 1 小時 prompt cache 的成本權重異常。約 140M cache-read tokens 中，多個最終請求各建立 475k token 的 1 小時 cache。按公開 API 定價，此類 cache write 成本應有限，但在 Claude Code 中該單一請求消耗了用量額度的極大比例。使用者懷疑 Claude Code 對長上下文/1 小時 cache 的定價權重高於 API，或會計系統存在 bug。"
key_points:
  - "Claude Code 長上下文會話（>150k token）用量暴增，不符公開 API 定價邏輯"
  - "單次 475k token 1 小時 cache write 消耗比例遠超 API 等價成本"
  - "懷疑定價權重不匹配或會計歸因系統存在 bug"
tags: [claude-code-pricing, cache-cost, usage-accounting, billing-anomaly]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude Code usage spike from long-context cache writes?

Claude Code Pro 使用者超出 5 小時額度後檢查用量日誌，發現長上下文會話（>150k token）與 1 小時 prompt cache 的成本權重異常。約 140M cache-read tokens 中，多個最終請求各建立 475k token 的 1 小時 cache。按公開 API 定價，此類 cache write 成本應有限，但在 Claude Code 中該單一請求消耗了用量額度的極大比例。使用者懷疑 Claude Code 對長上下文/1 小時 cache 的定價權重高於 API，或會計系統存在 bug。

### 重點
- Claude Code 長上下文會話（>150k token）用量暴增，不符公開 API 定價邏輯
- 單次 475k token 1 小時 cache write 消耗比例遠超 API 等價成本
- 懷疑定價權重不匹配或會計歸因系統存在 bug

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t0fuwj/claude_code_usage_spike_from_longcontext_cache/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Claude Code usage spike from long-context cache writes?

<!-- SC_OFF --><div class="md"><p>I hit my Claude Code 5-hour limit unexpectedly and checked the local session JSONL.</p> <p>The `/usage` screen said most usage came from:</p> <p>- “subagent-heavy sessions”</p> <p>- sessions active for 8+ hours</p> <p>- `&gt;150k context`</p> <p>But the subagent table only showed `codebase-explorer: 1%`, so subagents don’t seem to explain</p> <p>the spike.</p> <p>After deduplicating local records by `requestId`, the main session had about 140M cache-read</p> <p>tokens. The surprising part is that some of the final requests recreated a huge 1-hour prompt</p> <p>cache of around 475k tokens each.</p> <p>Using public API pricing, a 475k 1-hour cache write should be only a few dollars API-</p> <p>equivalent. But in Claude Code, one of these final requests seemed to consume a very large</p> <p>fraction of my 5-hour limit.</p> <p>I use a pro subscription and only use sonnet-4.6 model.</p> <p>So I’m wondering:</p> <p>Is Claude Code intentionally weighting long-context / 1-hour cache writes much more heavily</p> <p>than API pricing, or could this be a usage accounting / attribution bug?</p> <p>Has anyone else seen a large Claude Code usage jump after a long-running session with `&gt;150k`</p> <p>context?</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Different_Try_1269"> /u/Different_Try_1269 </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t0fuwj/claude_code_usage_spike_from_longcontext_cache/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t0fuwj/claude_code_usage_spike_from_longcontext_cache/">[comments]</a></span>

</details>