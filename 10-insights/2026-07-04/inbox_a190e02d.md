---
id: inbox_a190e02d
date: 2026-07-04
source_ref: "[[00-inbox/2026-07-04/2200-medium-tag-claude-i-handed-b2b-lead-gen-to-a-claude-skill-0a5b]]"
title: "I Handed B2B Lead-Gen to a Claude Skill. It Refuses to Search for What I Sell."
url: https://medium.com/write-a-catalyst/i-handed-b2b-lead-gen-to-a-claude-skill-it-refuses-to-search-for-what-i-sell-05de6a836677?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-07-04T18:47:58+00:00
fetched_at: 2026-07-04T22:11:35.831050+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者為 B2B 線索開發構建一個 Claude Skill，刻意拒絕搜索與產品名稱匹配的職位名稱，因為實際決策者不使用產品相關頭銜。以鉻礦採購為例，與其搜「Chrome 相關」職位，該 Skill 改為針對：產業（鋼鐵、冶金）、實際職位（採購經理、採購長）、地域（最大消費地中國）、行為信號（最近活動）。核心洞察是「交易知識是你的，介面應該傻」──領域專知駕馭搜索邏輯，工具只負責執行，避免浪費時間在演算法友善但無關的關鍵字上。該三元素模式（產業 → 實際買家職位 → 行為信號）可泛用於消費電子、IT 硬體等 B2B 場景。"
key_points:
  - "逆向思考：不搜「Chrome 買家」職位，改搜「採購經理」+「鋼鐵產業」+「中國」，避免跟演算法競爭"
  - "職位名稱悖論：產品相關職銜（如 Chrome Buyer）在真實業界不存在；決策者用通用採購頭銜"
  - "可重用架構：行為邏輯與配置分離（JSON 存儲），無需每次重新解釋行業知識，適用電子產品、硬體等多類"
tags: [lead-gen, claude-skill, b2b-strategy, search-refinement]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## I Handed B2B Lead-Gen to a Claude Skill. It Refuses to Search for What I Sell.

作者為 B2B 線索開發構建一個 Claude Skill，刻意拒絕搜索與產品名稱匹配的職位名稱，因為實際決策者不使用產品相關頭銜。以鉻礦採購為例，與其搜「Chrome 相關」職位，該 Skill 改為針對：產業（鋼鐵、冶金）、實際職位（採購經理、採購長）、地域（最大消費地中國）、行為信號（最近活動）。核心洞察是「交易知識是你的，介面應該傻」──領域專知駕馭搜索邏輯，工具只負責執行，避免浪費時間在演算法友善但無關的關鍵字上。該三元素模式（產業 → 實際買家職位 → 行為信號）可泛用於消費電子、IT 硬體等 B2B 場景。

### 重點
- 逆向思考：不搜「Chrome 買家」職位，改搜「採購經理」+「鋼鐵產業」+「中國」，避免跟演算法競爭
- 職位名稱悖論：產品相關職銜（如 Chrome Buyer）在真實業界不存在；決策者用通用採購頭銜
- 可重用架構：行為邏輯與配置分離（JSON 存儲），無需每次重新解釋行業知識，適用電子產品、硬體等多類

**原文：** [medium-tag-claude](https://medium.com/write-a-catalyst/i-handed-b2b-lead-gen-to-a-claude-skill-it-refuses-to-search-for-what-i-sell-05de6a836677?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The workflow that runs when you separate the search you know how to build from the interface that runs it. Continue reading on Write A Catalyst »

</details>