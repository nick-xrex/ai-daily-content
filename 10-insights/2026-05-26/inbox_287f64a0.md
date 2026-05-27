---
id: inbox_287f64a0
date: 2026-05-26
source_ref: "[[00-inbox/2026-05-26/0023-simon-willison-the-pressure-4c49]]"
title: "The pressure"
url: https://simonwillison.net/2026/May/26/the-pressure/#atom-everything
source: simon-willison
published_at: 2026-05-26T23:48:45+00:00
fetched_at: 2026-05-27T00:27:37.186651+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "curl 項目面臨前所未有的工作壓力，源於 AI 輔助的高品質安全報告大幅激增。2026 年年初的安全報告率達 2024 年的 4-5 倍、2025 年的 2 倍，平均每天超過 1 份報告。報告通常詳細篇幅長，品質遠高於往年，反映 AI 輔助安全研究的成熟度。項目負責人 Daniel Stenberg 首次因工作時數失衡受妻子表達關切。儘管報告激增，curl 本身穩固，近年發現的漏洞多為 LOW 或 MEDIUM 嚴重性。最近的 HIGH 級 CVE 發布於 2023 年 10 月。"
key_points:
  - "安全報告率激增至 2024 年 4-5 倍、2025 年 2 倍，平均每天超 1 份，品質遠優於往年"
  - "AI 輔助安全研究帶來的工作量與組織壓力：團隊成員工作時數創新高，維護者首次面臨家庭與工作衝突"
  - "漏洞等級保持低位：近年均為 LOW/MEDIUM，最近 HIGH 級出現於 2023 年 10 月，軟件質量依然穩固"
tags: [security-research, ai-assisted-vulnerability-detection, curl, open-source-maintenance]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## The pressure

curl 項目面臨前所未有的工作壓力，源於 AI 輔助的高品質安全報告大幅激增。2026 年年初的安全報告率達 2024 年的 4-5 倍、2025 年的 2 倍，平均每天超過 1 份報告。報告通常詳細篇幅長，品質遠高於往年，反映 AI 輔助安全研究的成熟度。項目負責人 Daniel Stenberg 首次因工作時數失衡受妻子表達關切。儘管報告激增，curl 本身穩固，近年發現的漏洞多為 LOW 或 MEDIUM 嚴重性。最近的 HIGH 級 CVE 發布於 2023 年 10 月。

### 重點
- 安全報告率激增至 2024 年 4-5 倍、2025 年 2 倍，平均每天超 1 份，品質遠優於往年
- AI 輔助安全研究帶來的工作量與組織壓力：團隊成員工作時數創新高，維護者首次面臨家庭與工作衝突
- 漏洞等級保持低位：近年均為 LOW/MEDIUM，最近 HIGH 級出現於 2023 年 10 月，軟件質量依然穩固

**原文：** [simon-willison](https://simonwillison.net/2026/May/26/the-pressure/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The pressure 
Daniel Stenberg on the unprecedented level of pressure the curl team are facing right now thanks to the deluge of (credible) AI-assisted security issues being reported. 
 
 The rate of incoming security reports is 4-5 times higher than it was in 2024 and double the speed of 2025 -- meaning that on average we now get more than one report per day . The quality is way higher than ever before. The reports are typically very detailed and long. [...] 
 For the first time in my life, my wife voiced concerns about my work hours and my imbalanced work/life situation. I work more than I’ve done before, but the flood keeps coming. [...] 
 This is a never-before seen or experienced pressure on the curl project and its security team members. An avalanche of high priority work that trumps all other things in the project that is primarily mental because we certainly could ignore them all if we wanted, but we feel a responsibility, we have a conscience and we are proud about our work. 
 
 The good news is that curl is a very solid piece of software, so the vulnerabilities people are finding tend not to be of high severity: 
 
 What is also a good trend: almost no one finds terrible vulnerabilities. All vulnerabilities found the last few years in curl have all been deemed severity LOW or MEDIUM. I'm not saying there won't be any more HIGH ever, but at least they are rare. The most recent severity high curl CVE was published in October 2023. 
 

 Via Lobste.rs 

 Tags: curl , security , ai , generative-ai , llms , daniel-stenberg , ai-ethics , ai-security-research

</details>