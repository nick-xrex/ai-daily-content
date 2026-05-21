---
id: inbox_b72521f3
date: 2026-05-20
source_ref: "[[00-inbox/2026-05-20/0917-infoq-main-pip-26-1-ships-dependency-cooldowns-and-43f0]]"
title: "Pip 26.1 Ships Dependency Cooldowns and Experimental Lockfile Support to Combat Supply Chain Attacks"
url: https://www.infoq.com/news/2026/05/pip-261-dependency-cooldowns/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-20T10:04:00+00:00
fetched_at: 2026-05-21T09:24:53.204410+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Pip 26.1 推出「依賴冷卻期」機制強化供應鏈安全——新發布的套件需等待 7 天才能被 pip 安裝。同時發布實驗性 pylock.toml 鎖檔支持（PEP 751），提供更強的依賴版本控制。根據供應鏈安全研究，7 天冷卻期可阻止分析樣本中 80%（10 個案例中 8 個）的攻擊成功。該措施標誌著 Python 生態在面對快速演進的供應鏈威脅時的主動防禦升級。"
key_points:
  - "依賴冷卻期機制：新套件發布 7 天後才能自動安裝，供應鏈攻擊常利用發布直後的窗口 → 直接對抗已知攻擊模式"
  - "量化安全收益：實證研究表明 7 天冷卻期阻止 80% 分析供應鏈攻擊——基於數據的防禦設計"
  - "鎖檔標準化（PEP 751）：pylock.toml 版本控制 → 減少隱藏的間接依賴引入漏洞的風險"
tags: [pip-26.1, supply-chain-security, dependency-cooldown, pep-751, pylock]
topics: []
importance: 5
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## Pip 26.1 Ships Dependency Cooldowns and Experimental Lockfile Support to Combat Supply Chain Attacks

Pip 26.1 推出「依賴冷卻期」機制強化供應鏈安全——新發布的套件需等待 7 天才能被 pip 安裝。同時發布實驗性 pylock.toml 鎖檔支持（PEP 751），提供更強的依賴版本控制。根據供應鏈安全研究，7 天冷卻期可阻止分析樣本中 80%（10 個案例中 8 個）的攻擊成功。該措施標誌著 Python 生態在面對快速演進的供應鏈威脅時的主動防禦升級。

### 重點
- 依賴冷卻期機制：新套件發布 7 天後才能自動安裝，供應鏈攻擊常利用發布直後的窗口 → 直接對抗已知攻擊模式
- 量化安全收益：實證研究表明 7 天冷卻期阻止 80% 分析供應鏈攻擊——基於數據的防禦設計
- 鎖檔標準化（PEP 751）：pylock.toml 版本控制 → 減少隱藏的間接依賴引入漏洞的風險

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/pip-261-dependency-cooldowns/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Pip 26.1 ships dependency cooldowns that enforce a waiting period before newly published packages can be installed, and experimental pylock.toml lockfile support from PEP 751. Research shows a 7-day cooldown would have prevented 8 out of 10 analyzed supply chain attacks from reaching end users. By Steef-Jan Wiggers

</details>