---
id: inbox_ab1cbae3
date: 2026-06-03
source_ref: "[[00-inbox/.../inbox_ab1cbae3]]"
title: "Uber Caps Usage of AI Tools Like Claude Code to Manage Costs"
url: https://simonwillison.net/2026/Jun/3/uber-caps-usage/#atom-everything
source: simon-willison
published_at: 2026-06-03T12:01:27+00:00
fetched_at: 2026-06-04T00:52:41.736521+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 因在四個月內燒光 2026 年 AI 預算，現實施 $1,500/月單一工具限額政策，限制員工使用 Cursor 和 Claude Code 等代理編碼軟體的成本。若工程師同時使用兩個工具，年度上限約 $36,000，占中位數薪資 $330,000 的 11%。此政策反映出 token 密集型 AI 編碼工具的真實成本結構，相當於每名工程師年度薪資的一成多。作者 Simon Willison 自身月度使用量約 $1,000/供應商，在該限額下仍有餘量。"
key_points:
  - "Uber 實施 $1,500/月/工具限額政策（各工具獨立計算），針對 Cursor 和 Claude Code 等 agentic 編碼軟體"
  - "年度上限推估 $36,000/工程師（雙工具），占 $330,000 中位數薪資的 11%"
  - "實際 token 成本數據：中等使用量約 $1,000/月/供應商"
tags: [ai-costs, uber, claude-code, cursor, coding-agents]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Uber Caps Usage of AI Tools Like Claude Code to Manage Costs

Uber 因在四個月內燒光 2026 年 AI 預算，現實施 $1,500/月單一工具限額政策，限制員工使用 Cursor 和 Claude Code 等代理編碼軟體的成本。若工程師同時使用兩個工具，年度上限約 $36,000，占中位數薪資 $330,000 的 11%。此政策反映出 token 密集型 AI 編碼工具的真實成本結構，相當於每名工程師年度薪資的一成多。作者 Simon Willison 自身月度使用量約 $1,000/供應商，在該限額下仍有餘量。

### 重點
- Uber 實施 $1,500/月/工具限額政策（各工具獨立計算），針對 Cursor 和 Claude Code 等 agentic 編碼軟體
- 年度上限推估 $36,000/工程師（雙工具），占 $330,000 中位數薪資的 11%
- 實際 token 成本數據：中等使用量約 $1,000/月/供應商

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/3/uber-caps-usage/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Uber Caps Usage of AI Tools Like Claude Code to Manage Costs

Uber Caps Usage of AI Tools Like Claude Code to Manage Costs 
I wrote the other day about Uber blowing its 2026 AI budget in four months, and how that wasn't particularly surprising given they would have set that budget in 2025, before anyone could have predicted how popular token-burning coding agents were about to become. 
 Natalie Lung for Bloomberg: 
 
 The rideshare giant is limiting all employees to $1,500 in monthly token spending per AI coding tool, an Uber spokesperson said in response to a Bloomberg News inquiry. That means spending on one tool doesn’t have a bearing on the budget for another. The limits, which have been instituted in recent months, only apply to agentic coding software such as Cursor or Anthropic PBC’s Claude Code. 
 
 A $1,500 monthly limit per tool strikes me as a rational policy response to over-spending, and much more sensible than those tokenmaxxing leaderboards encouraging employees to compete for as much AI usage as possible. 
 It's also interesting in that it hints at a real dollar value for what Uber is getting out of these tools. If we assume two actively used tools per engineer that's $3,000 * 12 = $36,000 cap per engineer per year. Levels.fyi lists the median yearly compensation package for Uber software engineers in the USA at $330,000. 
 That means each employee's AI spending cap is ~11% of that median compensation package. 
 I noted that my own token usage comes to about $1,000/month against each of Anthropic and OpenAI - which currently costs me just $100 per provider thanks to their generous subsidized plans for individual subscribers. Those plans are no longer available to larger companies like Uber. 
 Their new policy means if I were working at Uber I'd still have ~$500/month of tokens to spare for each of those tools, given my current usage patterns.

 Tags: ai , generative-ai , llms , llm-pricing , coding-agents , uber

</details>