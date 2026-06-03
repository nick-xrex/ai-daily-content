---
id: inbox_2bf622ad
date: 2026-06-02
source_ref: "[[00-inbox/2026-06-02/0030-simon-willison-pasted-file-editor-45c9]]"
title: "Pasted File Editor"
url: https://simonwillison.net/2026/Jun/2/pasted-file-editor/#atom-everything
source: simon-willison
published_at: 2026-06-02T04:13:36+00:00
fetched_at: 2026-06-03T00:38:27.612580+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 開發 Claude/Codex 文件編輯工具的原型實現。該工具自動偵測粘貼的大量文本並轉換為文件附件，提升用戶體驗；支持直接開啟檔案（含圖片縮圖預覽）和拖拽上傳。此功能源自 claude.ai 的原生貼文轉檔行為，現已移植到 Codex 桌面應用程序中進行驗證，展示 AI 輔助開發工具界面的實踐。"
key_points:
  - "自動偵測大量文本貼上並轉換為檔案附件，改善 Claude/Codex 的用戶輸入體驗"
  - "支持拖拽、圖片縮圖預覽和直接檔案開啟，提供更靈活的多模式輸入"
  - "原型由 Codex 桌面應用協助開發，展示 AI 輔助構建用戶界面工具的能力"
tags: [claude, codex, file-handling, ux-tool, ai-assisted-dev]
topics: [foundation_models.claude]
importance: 2
novelty: 3
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Pasted File Editor

Simon Willison 開發 Claude/Codex 文件編輯工具的原型實現。該工具自動偵測粘貼的大量文本並轉換為文件附件，提升用戶體驗；支持直接開啟檔案（含圖片縮圖預覽）和拖拽上傳。此功能源自 claude.ai 的原生貼文轉檔行為，現已移植到 Codex 桌面應用程序中進行驗證，展示 AI 輔助開發工具界面的實踐。

### 重點
- 自動偵測大量文本貼上並轉換為檔案附件，改善 Claude/Codex 的用戶輸入體驗
- 支持拖拽、圖片縮圖預覽和直接檔案開啟，提供更靈活的多模式輸入
- 原型由 Codex 桌面應用協助開發，展示 AI 輔助構建用戶界面工具的能力

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/2/pasted-file-editor/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tool: Pasted File Editor 
 I really like how you can paste a large volume of text into claude.ai (or the Claude desktop/mobile apps) and it will detect it as a large paste and turn it into a file attachment instead. 
 I decided to have Codex desktop build me a version of that as a prototype. 
 You can also open files directly - including images which will be shown as thumbnails - or drag files onto the textarea. 
 
 
 Tags: javascript , tools , ai-assisted-programming , claude , codex

</details>