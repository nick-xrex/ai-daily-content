---
id: inbox_be4f5a81
date: 2026-04-18
source_ref: "[[00-inbox/.../inbox_be4f5a81]]"
title: "Claude system prompts as a git timeline"
url: https://simonwillison.net/2026/Apr/18/extract-system-prompts/#atom-everything
source: (resumed)
published_at: 2026-04-18T12:25:00+00:00
fetched_at: 2026-04-21T02:36:17.456381+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 創建 Claude 系統提示的 Git 時間線工具，將 Anthropic 發布的 Markdown 系統提示轉換為按時間排列的個別檔案，並用偽造的 git commit dates 重現版本歷史。資源托管於 GitHub（simonw/research/extract-system-prompts），便於透過 GitHub 提交檢視追蹤模型設計演變，涵蓋 Claude 3（2024/7）至最新版本。Simon 並以此資源撰寫詳細版本比較分析，為研究者與開發者提供追蹤 Claude 架構決策與行為變更的便利途徑。"
key_points:
  - "系統提示時間線工具轉換 Markdown 為按日期排序檔案，支援 Git 歷史檢視比較"
  - "涵蓋 Claude 3 以來完整演變記錄，便於追蹤版本間安全、行為、架構變更"
  - "便利研究者與開發者理解模型設計決策的演變邏輯"
tags: [claude, system-prompts, research-tool, git, versioning]
topics: [foundation_models.claude]
importance: 2
novelty: 3
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude system prompts as a git timeline

Simon Willison 創建 Claude 系統提示的 Git 時間線工具，將 Anthropic 發布的 Markdown 系統提示轉換為按時間排列的個別檔案，並用偽造的 git commit dates 重現版本歷史。資源托管於 GitHub（simonw/research/extract-system-prompts），便於透過 GitHub 提交檢視追蹤模型設計演變，涵蓋 Claude 3（2024/7）至最新版本。Simon 並以此資源撰寫詳細版本比較分析，為研究者與開發者提供追蹤 Claude 架構決策與行為變更的便利途徑。

### 重點
- 系統提示時間線工具轉換 Markdown 為按日期排序檔案，支援 Git 歷史檢視比較
- 涵蓋 Claude 3 以來完整演變記錄，便於追蹤版本間安全、行為、架構變更
- 便利研究者與開發者理解模型設計決策的演變邏輯

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/18/extract-system-prompts/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong>Research:</strong> <a href="https://github.com/simonw/research/tree/main/extract-system-prompts#readme">Claude system prompts as a git timeline</a></p>
    <p>Anthropic <a href="https://platform.claude.com/docs/en/release-notes/system-prompts">publish the system prompts</a> for Claude chat and make that page <a href="https://platform.claude.com/docs/en/release-notes/system-prompts.md">available as Markdown</a>. I had Claude Code turn that page into separate files for each model and model family with fake git commit dates to enable browsing the changes via the GitHub commit view.</p>
<p>I used this to write my own <a href="https://simonwillison.net/2026/Apr/18/opus-system-prompt/">detailed notes on the changes between Opus 4.6 and 4.7</a>.</p>
    
        <p>Tags: <a href="https://simonwillison.net/tags/system-prompts">system-prompts</a>, <a href="https://simonwillison.net/tags/anthropic">anthropic</a>, <a href="https://simonwillison.net/tags/claude">claude</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a></p>

</details>
