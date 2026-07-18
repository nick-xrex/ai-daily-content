---
id: inbox_5d5dd15b
date: 2026-07-17
source_ref: "[[00-inbox/.../inbox_5d5dd15b]]"
title: "Ruflo v3.32.4 — Meta Proxy v0.4 default install"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.4
source: ruflo-releases
published_at: 2026-07-17T19:22:15+00:00
fetched_at: 2026-07-18T01:46:16.499405+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.4 穩定版釋出。整合 Meta Proxy v0.4 作為預設安裝選項（透過 ruflo proxy install --yes）。修復 @claude-flow/cli 編譯成品發布流程，防止遺失端點問題。明確解析 @claude-flow/cli@^3.32.4 版本依賴。已在隔離 Windows 環境驗證簽署的 v0.4.0 二進制檔案。"
key_points:
  - "Meta Proxy v0.4.0 成為預設安裝選項（ruflo proxy install --yes）"
  - "@claude-flow/cli 修復編譯成品發布流程，防止遺失端點"
  - "簽署二進制驗證於隔離 Windows 環境測試"
tags: [ruflo, meta-proxy, cli-fix, windows-validation]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Ruflo v3.32.4 — Meta Proxy v0.4 default install

Ruflo v3.32.4 穩定版釋出。整合 Meta Proxy v0.4 作為預設安裝選項（透過 ruflo proxy install --yes）。修復 @claude-flow/cli 編譯成品發布流程，防止遺失端點問題。明確解析 @claude-flow/cli@^3.32.4 版本依賴。已在隔離 Windows 環境驗證簽署的 v0.4.0 二進制檔案。

### 重點
- Meta Proxy v0.4.0 成為預設安裝選項（ruflo proxy install --yes）
- @claude-flow/cli 修復編譯成品發布流程，防止遺失端點
- 簽署二進制驗證於隔離 Windows 環境測試

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Ruflo v3.32.4 — Meta Proxy v0.4 default install

Meta Proxy v0.4 integration\n\n- 
 uflo proxy install --yes now installs the signed Meta Proxy v0.4.0 release by default.\n- @claude-flow/cli now builds its required emitted artifacts before publishing, preventing a missing-entrypoint package.\n- 
uflo@3.32.4 explicitly resolves @claude-flow/cli@^3.32.4.\n\nValidated from the public registry in an isolated Windows profile: the default installer fetched and verified the signed v0.4.0 binary.

</details>