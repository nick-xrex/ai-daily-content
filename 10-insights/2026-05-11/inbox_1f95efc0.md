---
id: inbox_1f95efc0
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/0113-simon-willison-thoughts-on-gitlab-s-workforce-reduction-9424]]"
title: "Thoughts on GitLab&#39;s workforce reduction\&#34; and \&#34;structural and strategic decisions\&#34;"
url: https://simonwillison.net/2026/May/11/gitlab-act-2/#atom-everything
source: simon-willison
published_at: 2026-05-11T23:58:55+00:00
fetched_at: 2026-05-12T01:17:36.621260+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitLab 宣布組織重構計畫「Act 2」，計劃減少員工駐紮國家最多 30%、扁平化移除最多 3 層管理、將 R&D 重組成約 60 個獨立團隊（幾乎加倍）。GitLab 明確闡述代理時代如何改變軟體經濟：開發者平台市場從每月數十美元/用戶增長到數百美元/用戶，預期朝向每月數千美元。新價值觀框架由 CREDIT 轉為 Speed with Quality、Ownership Mindset、Customer Outcomes，Diversity 改以 Interpersonal excellence 子項承載。Simon Willison 指出 GitLab 股價從一年前 $52 跌至 $26，該論點需謹慎，但反映行業對代理時代的適應趨勢。"
key_points:
  - "減少員工國家 30%、扁平化 3 層管理、R&D 重組成約 60 個獨立團隊，完全反映代理時代對組織結構的重新設計"
  - "開發者平台市場從 $10-50/user/month → $100-300/user/month → $1000+/user/month，代理時代改變軟體經濟基本面"
  - "新組織模式（independent teams with end-to-end ownership）使小團隊能繞過跨隊依賴，與 agentic 工程的團隊倍增效應對應"
tags: [gitlab, organizational-restructuring, agentic-engineering, market-economics]
topics: []
importance: 4
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Thoughts on GitLab's workforce reduction\" and \"structural and strategic decisions\"

GitLab 宣布組織重構計畫「Act 2」，計劃減少員工駐紮國家最多 30%、扁平化移除最多 3 層管理、將 R&D 重組成約 60 個獨立團隊（幾乎加倍）。GitLab 明確闡述代理時代如何改變軟體經濟：開發者平台市場從每月數十美元/用戶增長到數百美元/用戶，預期朝向每月數千美元。新價值觀框架由 CREDIT 轉為 Speed with Quality、Ownership Mindset、Customer Outcomes，Diversity 改以 Interpersonal excellence 子項承載。Simon Willison 指出 GitLab 股價從一年前 $52 跌至 $26，該論點需謹慎，但反映行業對代理時代的適應趨勢。

### 重點
- 減少員工國家 30%、扁平化 3 層管理、R&D 重組成約 60 個獨立團隊，完全反映代理時代對組織結構的重新設計
- 開發者平台市場從 $10-50/user/month → $100-300/user/month → $1000+/user/month，代理時代改變軟體經濟基本面
- 新組織模式（independent teams with end-to-end ownership）使小團隊能繞過跨隊依賴，與 agentic 工程的團隊倍增效應對應

**原文：** [simon-willison](https://simonwillison.net/2026/May/11/gitlab-act-2/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

GitLab Act 2 
There's a lot going on in this announcement from GitLab about the "workforce reduction" and "structural and strategic decisions" they are making with respect to the agentic era. 
 
 They're "planning to reduce the number of countries by up to 30% where we have small teams". One of the most interesting things about GitLab is that they have employees spread across a large number of countries - 18 are listed in their public employee handbook but this post says they are "operating in nearly 60 countries". That handbook used to document their payroll workflows for those countries too - they stopped publishing that in 2023 but the last public version (hooray for version control) remains a fascinating read. Since we don't know which of those 60 countries have small teams, we can't calculate how many countries that 30% applies to. 
 "We're planning to flatten the organization, removing up to three layers of management in some functions so leaders are closer to the work." - this isn't the first announcement of this type I've seen that's trimming management. Coinbase recently announced a much more aggressive version of this: they were "flattening our org structure to 5 layers max below" and "No pure managers: Every leader at Coinbase must also be a strong and active individual contributor. Managers should be like player-coaches". 
 In terms of team structure: "We're re-organizing R&amp;D to create roughly 60 smaller, more empowered teams with end-to-end ownership, nearly doubling the number of independent teams." I've always loved the idea of individual teams that can ship features unblocked by other teams, and it makes sense to me that agentic engineering can increase the capability of such teams. The 37signals public employee handbook used to have a section on working In self-sufficient, independent teams which perfectly captured this for me, I'm sad to see they removed that detail in January 2024! 
 Tucked away towards the bottom: " We will be retiring CREDIT as our values framework " - that's the values framework described on this page : "Collaboration, Results for Customers, Efficiency, Diversity, Inclusion &amp; Belonging, Iteration, and Transparency". The new values are "Speed with Quality, Ownership Mindset, Customer Outcomes". The fact that "Diversity" is no longer in there is likely to attract a whole lot of attention, so it's worth noting that a sub-bullet under Customer Outcomes reads "Interpersonal excellence: individuals who are good humans, embrace diversity, inclusion and belonging, assume good intent and treat everyone with respect". 
 
 Here's the part of their new strategy that most resonated with me: 
 
 The agentic era multiplies demand for software . Software has been the force multiplier behind nearly every business transformation of the last two decades. The constraint was the cost and time of producing and managing it. That constraint is collapsing. As the cost of producing software collapses, demand for it will expand. Last year, the developer platform market used to be measured in tens of dollars per user per month, this year it is hundreds/user/month and headed to thousands. Not only is the value of software for builders increasing, but we believe there will be more software and builders than ever, and we will serve an increasing volume of both . 
 
 That very much encapsulates my own optimistic, Jevons-paradox -inspired hope for how this will all work out. 
 Their opinion on this does need to be taken with a big grain of salt though. GitLab's stock price was ~$52 a year ago and is ~$26 today, and it's plausible that the drop corresponds to uncertainty about GitLab's continued growth as agentic engineering eats its way through their core market. 
 If your entire business depends on software engineering growing as a field and producing larger volumes of more lucrative seats, you have a strong incentive to believe that agents will have that effect!

 Via Hacker News 

 Tags: 37signals , careers , ai , gitlab , coding-agents , jevons-paradox , agentic-engineering

</details>