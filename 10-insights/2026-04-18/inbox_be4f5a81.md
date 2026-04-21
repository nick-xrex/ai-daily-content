---
id: inbox_be4f5a81
date: 2026-04-18
source_ref: "[[00-inbox/.../inbox_be4f5a81]]"
title: "Claude system prompts as a git timeline"
url: https://simonwillison.net/2026/Apr/18/extract-system-prompts/#atom-everything
source: simon-willison
published_at: 2026-04-18T12:25:00+00:00
fetched_at: 2026-04-21T03:11:17.670049+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 使用 Claude Code 將 Anthropic 公開發布的 Claude 系統提示轉換為 git 倉庫，每個模型、每個版本時間點為獨立檔案，帶偽 commit 時間戳，支持用 GitHub commit 歷史查看系統提示演變。Anthropic 官方在 platform.claude.com 以 Markdown 格式發布系統提示，歷史跨度從 2024 年 7 月 Claude 3 至今。此研究方法被用於撰寫 Opus 4.6 與 4.7 詳細變化分析。"
key_points:
  - "Claude 系統提示公開 git 倉庫化方案：各模型歷史版本轉為分離檔案，偽 commit 時間戳對應發布時間，支持按歷史瀏覽演變"
  - "研究方法論：克隆系統提示、轉為 git 歷史時間線，便於 diff 對比跨版本變化，更直觀理解 Claude 行為演變"
tags: [claude-system-prompt, git-timeline, research-methodology, version-tracking]
topics: [foundation_models.claude]
importance: 3
novelty: 4
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude system prompts as a git timeline

Simon Willison 使用 Claude Code 將 Anthropic 公開發布的 Claude 系統提示轉換為 git 倉庫，每個模型、每個版本時間點為獨立檔案，帶偽 commit 時間戳，支持用 GitHub commit 歷史查看系統提示演變。Anthropic 官方在 platform.claude.com 以 Markdown 格式發布系統提示，歷史跨度從 2024 年 7 月 Claude 3 至今。此研究方法被用於撰寫 Opus 4.6 與 4.7 詳細變化分析。

### 重點
- Claude 系統提示公開 git 倉庫化方案：各模型歷史版本轉為分離檔案，偽 commit 時間戳對應發布時間，支持按歷史瀏覽演變
- 研究方法論：克隆系統提示、轉為 git 歷史時間線，便於 diff 對比跨版本變化，更直觀理解 Claude 行為演變

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/18/extract-system-prompts/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Claude system prompts as a git timeline

<p><strong>Research:</strong> <a href="https://github.com/simonw/research/tree/main/extract-system-prompts#readme">Claude system prompts as a git timeline</a></p>
    <p>Anthropic <a href="https://platform.claude.com/docs/en/release-notes/system-prompts">publish the system prompts</a> for Claude chat and make that page <a href="https://platform.claude.com/docs/en/release-notes/system-prompts.md">available as Markdown</a>. I had Claude Code turn that page into separate files for each model and model family with fake git commit dates to enable browsing the changes via the GitHub commit view.</p>
<p>I used this to write my own <a href="https://simonwillison.net/2026/Apr/18/opus-system-prompt/">detailed notes on the changes between Opus 4.6 and 4.7</a>.</p>
    
        <p>Tags: <a href="https://simonwillison.net/tags/system-prompts">system-prompts</a>, <a href="https://simonwillison.net/tags/anthropic">anthropic</a>, <a href="https://simonwillison.net/tags/claude">claude</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a></p>

</details>