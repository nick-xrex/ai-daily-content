---
id: inbox_de713b1c
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_de713b1c]]"
title: "GitHub Introduces Default \&#34;Cooldown\&#34; Policy for Dependabot Version Updates"
url: https://www.infoq.com/news/2026/07/github-dependabot-cooldown/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-28T19:00:00+00:00
fetched_at: 2026-07-29T03:41:28.043800+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitHub Dependabot 現在預設採用「冷卻期」政策，在新版本發布後等待 3 天才建議升級依賴。此改變旨在提高惡意版本在整合前被社群識別和移除的概率，大幅降低供應鏈安全風險。該政策適用於所有使用 Dependabot 自動版本管理的開發團隊，無需手動設定即可獲得保護。冷卻期機制利用時間延遲讓廣泛的社群貢獻者有機會檢驗新版本的可靠性和安全性。此舉反映了業界對供應鏈風險的日益重視，是務實的防禦性設計。"
key_points:
  - "Dependabot 預設冷卻期改為 3 天，晚於版本發布才建議升級"
  - "提高惡意版本被社群識別並移除的機會，減少盲目整合風險"
  - "對所有使用 GitHub 依賴管理的開發團隊自動生效，無需設定"
tags: [dependabot, supply-chain-security, dependency-management, github]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## GitHub Introduces Default \"Cooldown\" Policy for Dependabot Version Updates

GitHub Dependabot 現在預設採用「冷卻期」政策，在新版本發布後等待 3 天才建議升級依賴。此改變旨在提高惡意版本在整合前被社群識別和移除的概率，大幅降低供應鏈安全風險。該政策適用於所有使用 Dependabot 自動版本管理的開發團隊，無需手動設定即可獲得保護。冷卻期機制利用時間延遲讓廣泛的社群貢獻者有機會檢驗新版本的可靠性和安全性。此舉反映了業界對供應鏈風險的日益重視，是務實的防禦性設計。

### 重點
- Dependabot 預設冷卻期改為 3 天，晚於版本發布才建議升級
- 提高惡意版本被社群識別並移除的機會，減少盲目整合風險
- 對所有使用 GitHub 依賴管理的開發團隊自動生效，無需設定

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/github-dependabot-cooldown/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# GitHub Introduces Default "Cooldown" Policy for Dependabot Version Updates

Instead of immediately opening pull requests when newer dependency versions are released, Dependabot now waits three days before suggesting upgrades, thus increasing the likelihood that malicious releases are identified and removed before they can be integrated. By Sergio De Simone

</details>