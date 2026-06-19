---
id: inbox_404911cc
date: 2026-06-18
source_ref: "[[00-inbox/2026-06-18/2200-infoq-architecture-vs-code-1-123-adds-two-hour-extension-up-890f]]"
title: "VS Code 1.123 Adds Two-Hour Extension Update Delay to Limit Supply Chain Attacks"
url: https://www.infoq.com/news/2026/06/vscode-extension-update-delay/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-18T10:15:00+00:00
fetched_at: 2026-06-18T22:12:31.531686+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "VS Code 1.123 版本引入安全防護機制，對擴展程式的自動更新增加 2 小時的延迟窗口，作為防禦供應鏈攻擊的冷卻期。在此延迟期間內若發現惡意擴展，用戶有機會撤銷更新。此防護對微軟、GitHub、OpenAI 等受信任發布者無效。類似的冷卻延迟機制已推廣至整個開源生態，包括 pip、RubyGems、npm、pnpm、Yarn 和 Bun 等主要套件管理平臺，成為業界防禦供應鏈威脅的標準做法。"
key_points:
  - "VS Code 1.123 引入 2 小時擴展自動更新延迟窗口，防止惡意更新立即生效"
  - "受信任發布者（Microsoft、GitHub、OpenAI）跳過此延迟限制"
  - "冷卻機制已跨越 pip、RubyGems、npm、pnpm、Yarn、Bun 等多個包管理器，形成行業共識"
tags: [vscode, supply-chain-security, package-managers, extension-security, malware-prevention]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## VS Code 1.123 Adds Two-Hour Extension Update Delay to Limit Supply Chain Attacks

VS Code 1.123 版本引入安全防護機制，對擴展程式的自動更新增加 2 小時的延迟窗口，作為防禦供應鏈攻擊的冷卻期。在此延迟期間內若發現惡意擴展，用戶有機會撤銷更新。此防護對微軟、GitHub、OpenAI 等受信任發布者無效。類似的冷卻延迟機制已推廣至整個開源生態，包括 pip、RubyGems、npm、pnpm、Yarn 和 Bun 等主要套件管理平臺，成為業界防禦供應鏈威脅的標準做法。

### 重點
- VS Code 1.123 引入 2 小時擴展自動更新延迟窗口，防止惡意更新立即生效
- 受信任發布者（Microsoft、GitHub、OpenAI）跳過此延迟限制
- 冷卻機制已跨越 pip、RubyGems、npm、pnpm、Yarn、Bun 等多個包管理器，形成行業共識

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/06/vscode-extension-update-delay/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

VS Code 1.123 adds a two-hour delay before auto-updating extensions to newly published versions, creating a revocation window against supply chain attacks. The delay does not apply to trusted publishers like Microsoft, GitHub, and OpenAI. Similar cooldown mechanisms have now spread across pip, RubyGems, npm, pnpm, Yarn, and Bun. By Steef-Jan Wiggers

</details>