---
id: inbox_71433ef5
date: 2026-04-16
source_ref: "[[00-inbox/.../inbox_71433ef5]]"
title: "datasette.io news preview"
url: https://simonwillison.net/2026/Apr/16/datasette-io-preview/#atom-everything
source: simon-willison
published_at: 2026-04-16T00:18:03+00:00
fetched_at: 2026-04-21T03:13:26.229134+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 使用 Claude 和 Claude Artifacts 快速構建了 datasette.io 新聞預覽工具，用於簡化 news.yaml 文件的編輯和驗證流程。該工具允許用戶貼上 YAML 內容，實時預覽渲染效果並檢測 Markdown 和 YAML 語法錯誤。目前 datasette.io 新聞部分已有 115 條新聞條目。實現方法充分利用 Claude 的能力直接複製 GitHub 儲存庫並分析內容，通過單一聊天命令快速生成功能完整的預覽界面。這個案例展示了 Claude 在快速開發特定工具方面的優勢。"
key_points:
  - "使用 Claude 和 Claude Artifacts 構建新聞預覽工具"
  - "支援實時 YAML 驗證和 Markdown 錯誤檢測，包含 115 條新聞條目"
  - "展示 Claude 在 GitHub 內容分析和快速工具原型開發中的應用"
tags: [vibe-coding, claude-artifacts, tools, datasette]
topics: [foundation_models.claude]
importance: 2
novelty: 2
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette.io news preview

Simon Willison 使用 Claude 和 Claude Artifacts 快速構建了 datasette.io 新聞預覽工具，用於簡化 news.yaml 文件的編輯和驗證流程。該工具允許用戶貼上 YAML 內容，實時預覽渲染效果並檢測 Markdown 和 YAML 語法錯誤。目前 datasette.io 新聞部分已有 115 條新聞條目。實現方法充分利用 Claude 的能力直接複製 GitHub 儲存庫並分析內容，通過單一聊天命令快速生成功能完整的預覽界面。這個案例展示了 Claude 在快速開發特定工具方面的優勢。

### 重點
- 使用 Claude 和 Claude Artifacts 構建新聞預覽工具
- 支援實時 YAML 驗證和 Markdown 錯誤檢測，包含 115 條新聞條目
- 展示 Claude 在 GitHub 內容分析和快速工具原型開發中的應用

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/16/datasette-io-preview/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# datasette.io news preview

<p><strong>Tool:</strong> <a href="https://tools.simonwillison.net/datasette-io-preview">datasette.io news preview</a></p>
    <p>The <a href="https://datasette.io/">datasette.io</a> website has a news section built from this <a href="https://github.com/simonw/datasette.io/blob/main/news.yaml">news.yaml</a> file in the underlying GitHub repository. The YAML format looks like this:</p>
<pre><code>- date: 2026-04-15
  body: |-
    [Datasette 1.0a27](https://docs.datasette.io/en/latest/changelog.html#a27-2026-04-15) changes how CSRF protection works in a way that simplifies form and API integration, and introduces a new `RenameTableEvent` for when a table is renamed by a SQL query.
- date: 2026-03-18
  body: |-
    ...
</code></pre>
<p>This format is a little hard to edit, so I finally <a href="https://claude.ai/share/c96129b9-bcb0-4eba-aee9-4a7ad236dfb7">had Claude build a custom preview UI</a> to make checking for errors have slightly less friction.</p>
<p>I built it using standard <a href="https://claude.ai/">claude.ai</a> and Claude Artifacts, taking advantage of Claude's ability to clone GitHub repos and look at their content as part of a regular chat:</p>
<blockquote>
<p><code>Clone https://github.com/simonw/datasette.io and look at the news.yaml file and how it is rendered on the homepage. Build an artifact I can paste that YAML into which previews what it will look like, and highlights any markdown errors or YAML errors</code></p>
</blockquote>
<p><img alt="Screenshot showing two side-by-side views of a datasette.io news preview tool. The left panel shows a dark-themed YAML editor with news entries containing date and body fields in Markdown format, with a red validation error at the bottom indicating the date field has an invalid format. The right panel shows the rendered preview output with formatted headings by date (April 2026, 18th March 2026), displaying 115 news entries with linked release names, inline code snippets, and changelog descriptions. A red badge with &quot;1&quot; appears on the left panel header indicating one validation error." src="https://static.simonwillison.net/static/2026/datasette-io-preview.jpg" /></p>
    
        <p>Tags: <a href="https://simonwillison.net/tags/vibe-coding">vibe-coding</a>, <a href="https://simonwillison.net/tags/claude">claude</a>, <a href="https://simonwillison.net/tags/tools">tools</a>, <a href="https://simonwillison.net/tags/datasette">datasette</a></p>

</details>