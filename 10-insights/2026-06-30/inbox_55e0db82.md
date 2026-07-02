---
id: inbox_55e0db82
date: 2026-06-30
source_ref: "[[00-inbox/2026-06-30/2331-simon-willison-have-your-agent-record-video-demos-of-it-7f89]]"
title: "Have your agent record video demos of its work with shot-scraper video"
url: https://simonwillison.net/2026/Jun/30/shot-scraper-video/#atom-everything
source: simon-willison
published_at: 2026-06-30T16:54:26+00:00
fetched_at: 2026-07-02T00:19:29.717479+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "shot-scraper 1.10 推出 `shot-scraper video` 命令，可透過 YAML storyboard 檔案使用 Playwright 自動錄製 web 應用演示影片。該工具解決了 Playwright 1.61.0 之前影片品質問題（如白框和寬度固定），整個功能設計與程式碼由 GPT-5.5 xhigh 在 Codex Desktop 環境完整實現。核心創新在於 CLI 工具的 --help 輸出提供足夠細節讓 AI 代理自行理解用法，相當於將 SKILL.md 嵌入工具本身。此設計模式對 AI 編碼代理自動生成工作演示特別重要，Simon Willison 用此工具錄製了 Datasette 新 CSV 匯入功能的完整演示。"
key_points:
  - "shot-scraper video 1.10：YAML storyboard 格式定義多場景演示，支援點擊、填表、等待元素等細微控制"
  - "CLI 設計模式：--help 輸出詳細到足以讓 AI 代理理解、自行生成 YAML（類似內嵌 SKILL.md），降低代理學習曲線"
  - "技術突破：Playwright 1.61.0 screencast 機制提供可變寬度影片錄製，消除先前 800px 限制與開錄時白框問題"
tags: [shot-scraper, video-automation, playwright, ai-agents, agentic-engineering]
topics: [foundation_models.gpt]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: true
deep_dive_approved: false
---

## Have your agent record video demos of its work with shot-scraper video

shot-scraper 1.10 推出 `shot-scraper video` 命令，可透過 YAML storyboard 檔案使用 Playwright 自動錄製 web 應用演示影片。該工具解決了 Playwright 1.61.0 之前影片品質問題（如白框和寬度固定），整個功能設計與程式碼由 GPT-5.5 xhigh 在 Codex Desktop 環境完整實現。核心創新在於 CLI 工具的 --help 輸出提供足夠細節讓 AI 代理自行理解用法，相當於將 SKILL.md 嵌入工具本身。此設計模式對 AI 編碼代理自動生成工作演示特別重要，Simon Willison 用此工具錄製了 Datasette 新 CSV 匯入功能的完整演示。

### 重點
- shot-scraper video 1.10：YAML storyboard 格式定義多場景演示，支援點擊、填表、等待元素等細微控制
- CLI 設計模式：--help 輸出詳細到足以讓 AI 代理理解、自行生成 YAML（類似內嵌 SKILL.md），降低代理學習曲線
- 技術突破：Playwright 1.61.0 screencast 機制提供可變寬度影片錄製，消除先前 800px 限制與開錄時白框問題

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/30/shot-scraper-video/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

shot-scraper video is a new command introduced in today's shot-scraper 1.10 release which accepts a storyboard.yml file defining a routine to run against a web application and uses Playwright to record a video of that routine. I've written before about the importance of having coding agents produce demos of their work; this is my latest attempt at enabling them to do that. 
 Here's an example video created using shot-scraper video , exercising a still in development feature adding the ability to create new tables in Datasette from pasted CSV, TSV or JSON data: 
 
 
 
 
 
 That video was created by running this command : 
 shot-scraper video datasette-bulk-insert-storyboard.yml \
 --auth datasette-demo-auth.json --mp4 
 (That --auth JSON file contains a cookie , as described here in the documentation.) 
 Here's the datasette-bulk-insert-storyboard.yml file: 
 output : /tmp/datasette-bulk-insert-demo.webm 
 server :
 - uv 
 - --directory 
 - /Users/simon/Dropbox/dev/datasette 
 - run 
 - datasette 
 - -p 
 - 6419 
 - --root 
 - --secret 
 - " 1 " 
 - /tmp/demo.db 
 url : http://127.0.0.1:6419/demo/tasks 
 viewport :
 width : 1280 
 height : 720 
 cursor : true 
 wait_for : ' button[data-table-action="insert-row"] ' 
 javascript : | 
 (() =&gt; { 
 let clipboardText = ""; 
 Object.defineProperty(navigator, "clipboard", { 
 configurable: true, 
 get: () =&gt; ({ 
 writeText: async (text) =&gt; { 
 clipboardText = String(text); 
 }, 
 readText: async () =&gt; clipboardText, 
 }), 
 }); 
 })(); 
 scenes :
 - name : Bulk insert existing table rows 
 do :
 - pause : 0.8 
 - click : ' button[data-table-action="insert-row"] ' 
 - wait_for : " #row-edit-dialog[open] " 
 - pause : 0.5 
 - click : " .row-edit-bulk-insert " 
 - wait_for : " .row-edit-bulk-textarea " 
 - pause : 0.5 
 - click : " .row-edit-copy-template " 
 - wait_for : " text=Copied " 
 - pause : 0.8 
 - fill :
 into : " .row-edit-bulk-textarea " 
 text : | 
 title,owner,status,priority,notes 
 Prepare release video,Ana,doing,1,Recorded with shot-scraper 
 Check pasted CSV import,Ben,review,3,Previewed before inserting 
 Share the branch demo,Chen,queued,2,Bulk insert creates three rows 
 - pause : 0.8 
 - click : " .row-edit-save " 
 - wait_for : " text=Previewing 3 rows. " 
 - pause : 1.2 
 - click : " .row-edit-save " 
 - wait_for : " text=3 rows inserted. " 
 - pause : 1.0 
 - click : " .row-edit-cancel " 
 - wait_for : " text=Prepare release video " 
 - pause : 1.0 
 - name : Create a table from pasted CSV 
 open : http://127.0.0.1:6419/demo 
 wait_for : ' details.actions-menu-links summary ' 
 do :
 - pause : 0.8 
 - click : ' details.actions-menu-links summary ' 
 - click : ' button[data-database-action="create-table"] ' 
 - wait_for : " #table-create-dialog[open] " 
 - pause : 0.5 
 - fill :
 into : " .table-create-table-name " 
 text : " launch_metrics " 
 - click : " .table-create-from-data " 
 - wait_for : " .table-create-data-textarea " 
 - pause : 0.5 
 - fill :
 into : " .table-create-data-textarea " 
 text : | 
 metric_id,name,score,recorded_on 
 m001,Activation rate,87.5,2026-06-29 
 m002,Retention check,72.25,2026-06-30 
 m003,CSV import health,95,2026-07-01 
 - pause : 0.8 
 - click : " .table-create-save " 
 - wait_for : " text=Previewing 3 rows. " 
 - pause : 1.2 
 - click : " .table-create-save " 
 - wait_for_url : " **/demo/launch_metrics " 
 - wait_for : " text=Activation rate " 
 - pause : 1.2 
 The video command documentation includes simpler examples, but for the purpose of this post I thought I'd go with something more comprehensive. 
 That demo YAML storyboard was constructed entirely by GPT-5.5 xhigh running in Codex Desktop, using the following prompt run inside my ~/dev/datasette checkout of this branch : 
 
 Review the changes on this branch. 
 cd to ~/dev/shot-scraper and run the command "uv run shot-scraper video --help" 
 Now use that new video command to record a video demo of the new features from this branch, including running a "uv run datasette -p 6419 --root --secret 1 /tmp/demo.db" development server so you can record the video against a demo DB that you first create. 
 
 Now that I've released the feature the prompt could say " run uvx shot-scraper video --help " instead and it should achieve the same result. 
 I really like this pattern where the --help output for a command provides enough detail that a coding agent can use it - it works kind of like bundling a SKILL.md file directly inside the tool. I used the same pattern for showboat and rodney . 
 How I built this 
 shot-scraper video started as an experimental prototype. shot-scraper is built on top of Playwright , and the key feature it needed was for Playwright to be able to record video of browser sessions with enough control to create the desired demo. 
 I first tried this a few years ago and found that the Playwright-produced videos included additional chrome that was useful for debugging a test failure but unwanted for a product demo. 
 They fixed that a while ago, but there were still some minor blockers. In particular I was getting a few white frames at the start of the videos , since the recording mechanism kicked in before the first URL was loaded by the browser. 
 Playwright 1.59 added a new screencast mechanism providing much more finely grained control over video recording. This was very nearly what I needed, but the resulting videos were fixed at 800px wide. 
 I found a landed PR fixing that but it wasn't yet in a release. Then yesterday they shipped it in playwright-python 1.61.0 and I was finally unblocked to finish implementing the feature! 
 The code itself was all written by GPT-5.5 xhigh in Codex Desktop. I had it write the documentation as well which gave me a very useful frame for reviewing the design - much of the iteration on the feature came from reviewing that documentation, spotting things that were redundant, inconsistent or confusing, and requesting (or dictating) a better design. 
 The YAML format itself was mostly defined by the coding agent. I had it use Pydantic to both define and validate the format, partly to make the design easier to review. 
 This is a great example of the kind of feature that I almost certainly wouldn't have taken on without coding agent support. I filed the original issue in February 2024, and had difficulty finding the necessary time to solve this in amongst all of my other projects. 
 
 Tags: projects , python , yaml , ai , datasette , playwright , shot-scraper , generative-ai , llms , pydantic , coding-agents , agentic-engineering

</details>