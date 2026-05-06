---
id: inbox_563dcaa2
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1001-claude-code-releases-v2-1-131-9a62]]"
title: "v2.1.131"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.131
source: claude-code-releases
published_at: 2026-05-06T07:47:56+00:00
fetched_at: 2026-05-06T10:06:04.933427+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.131 發布兩項重要修復：一是修正 VS Code extension 在 Windows 上因 bundled SDK 的 hardcoded build path 導致的啟動失敗（createRequire polyfill bug），二是修復 Mantle endpoint 認證時缺少 x-api-key header 的問題。這些修復直接影響 Windows 用戶和使用 Mantle 部署的企業用戶的日常使用體驗。"
key_points:
  - "VS Code 擴展在 Windows 啟動失敗：bundled SDK 內 hardcoded build path 導致 createRequire polyfill bug"
  - "Mantle endpoint 認證失敗：缺少 x-api-key header，影響企業部署"
  - "小版本維護更新，針對特定環境的關鍵 bug 修復"
tags: [claude-code, bug-fix, windows, authentication]
topics: [foundation_models.claude]
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.131

Claude Code v2.1.131 發布兩項重要修復：一是修正 VS Code extension 在 Windows 上因 bundled SDK 的 hardcoded build path 導致的啟動失敗（createRequire polyfill bug），二是修復 Mantle endpoint 認證時缺少 x-api-key header 的問題。這些修復直接影響 Windows 用戶和使用 Mantle 部署的企業用戶的日常使用體驗。

### 重點
- VS Code 擴展在 Windows 啟動失敗：bundled SDK 內 hardcoded build path 導致 createRequire polyfill bug
- Mantle endpoint 認證失敗：缺少 x-api-key header，影響企業部署
- 小版本維護更新，針對特定環境的關鍵 bug 修復

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.131)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<h2>What's changed</h2>
<ul>
<li>Fixed VS Code extension failing to activate on Windows due to a hardcoded build path in the bundled SDK (<code>createRequire</code> polyfill bug)</li>
<li>Fixed Mantle endpoint authentication failing with missing <code>x-api-key</code> header</li>
</ul>

</details>