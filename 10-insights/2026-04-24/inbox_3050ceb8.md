---
id: inbox_3050ceb8
date: 2026-04-24
source_ref: "[[00-inbox/2026-04-24/0246-simon-willison-an-update-on-recent-claude-code-quality-4614]]"
title: "An update on recent Claude Code quality reports"
url: https://simonwillison.net/2026/Apr/24/recent-claude-code-quality-reports/#atom-everything
source: simon-willison
published_at: 2026-04-24T01:31:25+00:00
fetched_at: 2026-04-24T02:56:27.824695+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 品質下降問題根源於框架層面的三個 bug，而非模型本身。最關鍵的 bug 發生於 3 月 26 日：原意清除超過一小時未使用 session 的舊思考內容以降低延遲，卻因程式碼缺陷每轉都執行一次（而非僅一次），導致使用者感受到 Claude 健忘且重複。此問題特別影響有長期未使用 session（超過一小時）的開發者。Anthropic 的事後分析揭示了框架層面 bug 的隱蔽性：即使底層模型無誤，框架邏輯的複雜缺陷仍能顯著破壞使用體驗。對於構建 agentic 系統的開發者而言，此分析具有深刻啟發意義。"
key_points:
  - "3 月 26 日 idle session 思考清除 bug 每轉執行導致 session 連貫性破壞"
  - "問題源於框架層面而非模型能力，強調分離評估的重要性"
  - "長期 session（>1 小時未用）使用者受影響最大"
tags: [claude-code, session-management, debugging, postmortem]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## An update on recent Claude Code quality reports

Claude Code 品質下降問題根源於框架層面的三個 bug，而非模型本身。最關鍵的 bug 發生於 3 月 26 日：原意清除超過一小時未使用 session 的舊思考內容以降低延遲，卻因程式碼缺陷每轉都執行一次（而非僅一次），導致使用者感受到 Claude 健忘且重複。此問題特別影響有長期未使用 session（超過一小時）的開發者。Anthropic 的事後分析揭示了框架層面 bug 的隱蔽性：即使底層模型無誤，框架邏輯的複雜缺陷仍能顯著破壞使用體驗。對於構建 agentic 系統的開發者而言，此分析具有深刻啟發意義。

### 重點
- 3 月 26 日 idle session 思考清除 bug 每轉執行導致 session 連貫性破壞
- 問題源於框架層面而非模型能力，強調分離評估的重要性
- 長期 session（>1 小時未用）使用者受影響最大

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/24/recent-claude-code-quality-reports/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://www.anthropic.com/engineering/april-23-postmortem">An update on recent Claude Code quality reports</a></strong></p>
It turns out the high volume of complaints that Claude Code was providing worse quality results over the past two months was grounded in real problems.</p>
<p>The models themselves were not to blame, but three separate issues in the Claude Code harness caused complex but material problems which directly affected users.</p>
<p>Anthropic's postmortem describes these in detail. This one in particular stood out to me:</p>
<blockquote>
<p>On March 26, we shipped a change to clear Claude's older thinking from sessions that had been idle for over an hour, to reduce latency when users resumed those sessions. A bug caused this to keep happening every turn for the rest of the session instead of just once, which made Claude seem forgetful and repetitive.</p>
</blockquote>
<p>I <em>frequently</em> have Claude Code sessions which I leave for an hour (or often a day or longer) before returning to them. Right now I have 11 of those (according to <code>ps aux  | grep 'claude '</code>) and that's after closing down dozens more the other day.</p>
<p>I estimate I spend more time prompting in these "stale" sessions than sessions that I've recently started!</p>
<p>If you're building agentic systems it's worth reading this article in detail - the kinds of bugs that affect harnesses are deeply complicated, even if you put aside the inherent non-deterministic nature of the models themselves.

    <p><small></small>Via <a href="https://news.ycombinator.com/item?id=47878905">Hacker News</a></small></p>


    <p>Tags: <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/prompt-engineering">prompt-engineering</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/anthropic">anthropic</a>, <a href="https://simonwillison.net/tags/coding-agents">coding-agents</a>, <a href="https://simonwillison.net/tags/claude-code">claude-code</a></p>

</details>