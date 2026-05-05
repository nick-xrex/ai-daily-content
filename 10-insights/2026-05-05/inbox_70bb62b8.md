---
id: inbox_70bb62b8
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/0819-reddit-claudeai-i-replaced-a-5-step-lead-enrichment-work-a776]]"
title: "I replaced a 5-step lead enrichment workflow with Claude custom skills"
url: https://www.reddit.com/r/ClaudeAI/comments/1t47h53/i_replaced_a_5step_lead_enrichment_workflow_with/
source: reddit-claudeai
published_at: 2026-05-05T06:37:01+00:00
fetched_at: 2026-05-05T08:44:14.776139+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者用 Claude 搭配三個 MCP（Crustdata、FullEnrich、HubSpot）完全重構了銷售線索富集工作流，將耗時 1+ 小時且涉及 5 個步驟、3 個供應商的複雜流程簡化為單一 5 分鐘的 Claude 工作流。原流程：Apollo 建列 → PDL 富集（可用率 50-60%）→ 第二供應商補齊 → 分離的郵件驗證（退信率 15-20%）→ HubSpot 手動導入。新流程利用 Crustdata 提供即時人員/公司資料及社媒貼文、FullEnrich 進行郵件瀑布驗證（覆蓋 20+ 供應商）、HubSpot MCP 直接推送結果。Claude 基於完整檔案和自訂 ICP skill 進行評分，品質遠勝於純關鍵詞過濾，作者仍進行最終人工審查以確保準確性。"
key_points:
  - "5 步多工具流程（Apollo → PDL → 二供應商 → 郵件驗證 → HubSpot，耗時 1+ 小時）→ Claude + 3 MCP 單一流程（5 分鐘）"
  - "Crustdata（實時人/公司資料 + 社媒）+ FullEnrich（20+ 供應商郵件瀑布驗證）+ HubSpot MCP 直接推送，替代 3 個分散供應商"
  - "Claude 基於完整檔案與自訂 ICP skill 評分，品質優於關鍵詞過濾（減少垃圾配對），仍保留人工最終審查"
tags: [mcp-workflow, sales-automation, lead-enrichment, productivity-gain]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## I replaced a 5-step lead enrichment workflow with Claude custom skills

開發者用 Claude 搭配三個 MCP（Crustdata、FullEnrich、HubSpot）完全重構了銷售線索富集工作流，將耗時 1+ 小時且涉及 5 個步驟、3 個供應商的複雜流程簡化為單一 5 分鐘的 Claude 工作流。原流程：Apollo 建列 → PDL 富集（可用率 50-60%）→ 第二供應商補齊 → 分離的郵件驗證（退信率 15-20%）→ HubSpot 手動導入。新流程利用 Crustdata 提供即時人員/公司資料及社媒貼文、FullEnrich 進行郵件瀑布驗證（覆蓋 20+ 供應商）、HubSpot MCP 直接推送結果。Claude 基於完整檔案和自訂 ICP skill 進行評分，品質遠勝於純關鍵詞過濾，作者仍進行最終人工審查以確保準確性。

### 重點
- 5 步多工具流程（Apollo → PDL → 二供應商 → 郵件驗證 → HubSpot，耗時 1+ 小時）→ Claude + 3 MCP 單一流程（5 分鐘）
- Crustdata（實時人/公司資料 + 社媒）+ FullEnrich（20+ 供應商郵件瀑布驗證）+ HubSpot MCP 直接推送，替代 3 個分散供應商
- Claude 基於完整檔案與自訂 ICP skill 評分，品質優於關鍵詞過濾（減少垃圾配對），仍保留人工最終審查

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t47h53/i_replaced_a_5step_lead_enrichment_workflow_with/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Sharing this because i know a lot of people here are doing what i did.</p> <p>My old workflow was a long process. Build a list in Apollo, enrich through PDL (maybe 50-60% usable, rest is outdated or wrong), take the gaps and pass to a second provider, verify emails separately because enrichment data bounces 15-20% of the time, then manually load everything into HubSpot because none of these tools talk to each other cleanly. 5 steps, 3 vendors, took over an hour and the output was still mediocre.</p> <p>So i built a Claude workflow using MCPs that handles all of this in one pass.</p> <p>Tech stack (all connected as MCPs):</p> <p>Crustdata - people and company data. This replaced Apollo and PDL for me. The data is pulled in realtime so you're not getting outdated job titles. Search filters are granular enough that Claude can find the exact ICP match without me manually cleaning the list after. It also returns social media posts from prospects which I use for personalization.</p> <p>FullEnrich MCP - email waterfall and verification in one step. This replaced the separate enrichment + verification tools I was paying for. They run through 20+ providers so match rates are solid.</p> <p>HubSpot MCP - Claude pushes the final enriched list directly into the CRM. No more manual CSV imports.</p> <p>Example prompt I run: &quot;Find B2B SaaS companies in the US with 50-200 employees that raised Series A or B in the last 9 months and are hiring for sales roles. Find the VP Sales or Head of Growth at each. Get verified emails. Pull their recent social media posts and research their website. Score each prospect against our ICP and rank by fit.&quot;</p> <p>Claude builds the list, enriches everything, verifies emails, scores against my ICP criteria and pushes to HubSpot. Takes about 5 minutes for a list that used to take me over an hour manually across multiple tools.</p> <p>The list quality is also way better. When Claude reads someone's full profile and matches against your ICP instead of relying on keyword filters, you stop getting garbage matches. I wrote a skill describing our ICP in detail so it scores consistently across searches.</p> <p>I still review every list before anything goes out. But the data collection, enrichment and scoring part is basically handled. Happy to answer questions if anyone wants to set up something similar.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/lemnistatic"> /u/lemnistatic </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t47h53/i_replaced_a_5step_lead_enrichment_workflow_with/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t47h53/i_replaced_a_5step_lead_enrichment_workflow_with/">[comments]</a></span>

</details>