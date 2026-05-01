---
id: inbox_e49924b1
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/1257-medium-tag-claude-we-told-claude-code-to-deny-access-to-ou-e8f0]]"
title: "We Told Claude Code to Deny Access to Our Secrets. It Read Them Anyway."
url: https://medium.com/@pankaj_pandey/we-told-claude-code-to-deny-access-to-our-secrets-it-read-them-anyway-e59940c73eb9?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-01T10:11:01+00:00
fetched_at: 2026-05-01T13:26:19.827329+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章披露 Claude Code 的 permissions.deny 功能存在已知安全漏洞，無法可靠地阻止模型存取受限敏感資訊。作者實測發現即使在 permissions.deny 中明確列出禁止項目，Claude Code 仍能讀取被標記為禁止的秘密。根本原因是該功能含有靜默失效的 bug。替代方案是使用 .claudeignore 檔案搭配專業 secrets manager，設置時間僅需 10 分鐘但安全性更可靠。此發現對使用 Claude Code 處理機密資訊（API 金鑰、資料庫認證等）的團隊具有重大安全意涵。"
key_points:
  - "Claude Code permissions.deny 存在已知漏洞：靜默失效，無法可靠阻止秘密讀取"
  - "實測驗證：即使禁止項目仍被成功讀取，信任該功能為危險行為"
  - "推薦替代方案：.claudeignore + secrets manager（10 分鐘設置），安全性更高"
tags: [security, claude-code, permissions, secrets-management, vulnerability]
topics: [foundation_models.claude]
importance: 4
novelty: 5
insight_quality: 5
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## We Told Claude Code to Deny Access to Our Secrets. It Read Them Anyway.

文章披露 Claude Code 的 permissions.deny 功能存在已知安全漏洞，無法可靠地阻止模型存取受限敏感資訊。作者實測發現即使在 permissions.deny 中明確列出禁止項目，Claude Code 仍能讀取被標記為禁止的秘密。根本原因是該功能含有靜默失效的 bug。替代方案是使用 .claudeignore 檔案搭配專業 secrets manager，設置時間僅需 10 分鐘但安全性更可靠。此發現對使用 Claude Code 處理機密資訊（API 金鑰、資料庫認證等）的團隊具有重大安全意涵。

### 重點
- Claude Code permissions.deny 存在已知漏洞：靜默失效，無法可靠阻止秘密讀取
- 實測驗證：即使禁止項目仍被成功讀取，信任該功能為危險行為
- 推薦替代方案：.claudeignore + secrets manager（10 分鐘設置），安全性更高

**原文：** [medium-tag-claude](https://medium.com/@pankaj_pandey/we-told-claude-code-to-deny-access-to-our-secrets-it-read-them-anyway-e59940c73eb9?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@pankaj_pandey/we-told-claude-code-to-deny-access-to-our-secrets-it-read-them-anyway-e59940c73eb9?source=rss------claude-5"><img src="https://cdn-images-1.medium.com/max/1672/1*3e3LuU48bszLGRY0eU4AWw.png" width="1672" /></a></p><p class="medium-feed-snippet">permissions.deny has documented bugs that fail silently. A 10-minute setup with .claudeignore and a secrets manager does what the&#x2026;</p><p class="medium-feed-link"><a href="https://medium.com/@pankaj_pandey/we-told-claude-code-to-deny-access-to-our-secrets-it-read-them-anyway-e59940c73eb9?source=rss------claude-5">Continue reading on Medium »</a></p></div>

</details>