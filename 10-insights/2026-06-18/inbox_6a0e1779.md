---
id: inbox_6a0e1779
date: 2026-06-18
source_ref: "[[00-inbox/2026-06-18/2200-infoq-main-vs-code-1-123-adds-two-hour-extension-up-88c1]]"
title: "VS Code 1.123 Adds Two-Hour Extension Update Delay to Limit Supply Chain Attacks"
url: https://www.infoq.com/news/2026/06/vscode-extension-update-delay/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-18T10:15:00+00:00
fetched_at: 2026-06-18T22:09:40.546125+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "VS Code 1.123 引入擴展更新延遲機制：自動更新到新版本前等待 2 小時，創建撤銷窗口以對抗供應鏈攻擊。此舉不適用於 Microsoft、GitHub、OpenAI 等受信任發布者。相同冷卻機制已擴展到 pip、RubyGems、npm、pnpm、Yarn、Bun，反映跨 ecosystems 對軟體供應鏈安全的共識。"
key_points:
  - "2 小時延遲提供惡意擴展被發現並撤銷的時間窗口"
  - "受信任發布者豁免，避免影響常見工具鏈更新速度"
  - "此模式已成為包管理器標準做法，跨 npm、pip、Ruby 等生態"
tags: [security, supply-chain, extension-management, vscode]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## VS Code 1.123 Adds Two-Hour Extension Update Delay to Limit Supply Chain Attacks

VS Code 1.123 引入擴展更新延遲機制：自動更新到新版本前等待 2 小時，創建撤銷窗口以對抗供應鏈攻擊。此舉不適用於 Microsoft、GitHub、OpenAI 等受信任發布者。相同冷卻機制已擴展到 pip、RubyGems、npm、pnpm、Yarn、Bun，反映跨 ecosystems 對軟體供應鏈安全的共識。

### 重點
- 2 小時延遲提供惡意擴展被發現並撤銷的時間窗口
- 受信任發布者豁免，避免影響常見工具鏈更新速度
- 此模式已成為包管理器標準做法，跨 npm、pip、Ruby 等生態

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/vscode-extension-update-delay/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

VS Code 1.123 adds a two-hour delay before auto-updating extensions to newly published versions, creating a revocation window against supply chain attacks. The delay does not apply to trusted publishers like Microsoft, GitHub, and OpenAI. Similar cooldown mechanisms have now spread across pip, RubyGems, npm, pnpm, Yarn, and Bun. By Steef-Jan Wiggers

</details>