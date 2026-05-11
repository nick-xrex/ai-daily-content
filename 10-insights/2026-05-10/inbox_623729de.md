---
id: inbox_623729de
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_623729de]]"
title: "Building out my tool library, any recommendations? I just added email capability and im starting to get hyped!"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t97163/building_out_my_tool_library_any_recommendations/
source: reddit-localllama
published_at: 2026-05-10T13:31:10+00:00
fetched_at: 2026-05-11T02:24:43.314149+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者以 OpenWebUI + Qwen 3.6 35B（256k context）建構本地 LLM 工具生態，已實現 10+ 工具包括文件生成（DOC/PDF/XLS/PPTX）、郵件發送附件、圖表視覺化、GitHub URL 轉換、天氣查詢、體育賽程、沙箱檔案管理、增強網頁爬蟲、Wayback Archive 備份取用、Microsoft Learn 知識查詢。通過 parallel tool calling 支持多工具併行執行，展示本地 LLM 能實現生產級自動化工作流（如郵件營銷自動化）。"
key_points:
  - "OpenWebUI parallel tool calling 啟用多個工具併行執行，提升 agent 效率"
  - "已實現 10+ 工具涵蓋文件、通訊、網路、檔案、知識查詢等多個領域"
  - "本地 LLM agent 可搭建生產級自動化工作流，如自動化郵件與市場營銷任務"
tags: [openwebui, qwen, tool-library, agent-orchestration, parallel-tools]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Building out my tool library, any recommendations? I just added email capability and im starting to get hyped!

使用者以 OpenWebUI + Qwen 3.6 35B（256k context）建構本地 LLM 工具生態，已實現 10+ 工具包括文件生成（DOC/PDF/XLS/PPTX）、郵件發送附件、圖表視覺化、GitHub URL 轉換、天氣查詢、體育賽程、沙箱檔案管理、增強網頁爬蟲、Wayback Archive 備份取用、Microsoft Learn 知識查詢。通過 parallel tool calling 支持多工具併行執行，展示本地 LLM 能實現生產級自動化工作流（如郵件營銷自動化）。

### 重點
- OpenWebUI parallel tool calling 啟用多個工具併行執行，提升 agent 效率
- 已實現 10+ 工具涵蓋文件、通訊、網路、檔案、知識查詢等多個領域
- 本地 LLM agent 可搭建生產級自動化工作流，如自動化郵件與市場營銷任務

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t97163/building_out_my_tool_library_any_recommendations/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Building out my tool library, any recommendations? I just added email capability and im starting to get hyped!

I'm using OpenWebUI and and making tools/skills to improve my models functionality. I am currently using Qwen 3.6 35B A3B Q8 (F16) 256k I grabbed `parallel tools` to be able to run multiple tool calls at once.. so far i have the following... -------------- Document Creator: (WIP started it yesterday, testing now, almost done, rest of list is fully working and done) creates DOC/PDF/XLS/PPTX files, using linux prereqs and helpers, allows model to create documents Send_Email: Allows the model to send an email from an smtp server, supports file attachments if the model wants to send an attachment Inline visualizer (I found this here on reddit): allows visualizations to be produced directly in chat, its pretty awesome Github Url converter: converts regular github links into raw links to make it viewable by the model Weather: gets current and/or historical weather information for any location, lookup time is reduced for us based locations based on zip database (reduces call time significantly) Sports: scores/schedules lookup Filesystem: Allows a sandboxed directory (path checking on every command, outside of the models control) to create/modify/delete files, read files, append files, ZIP files (password protected if asked) - The model is aware of all files it has possession of including any generated images, anything its made can be referenced and it will be able to get it and do whatever you want with it Browse_Page: enhanced web scraping leveraging different user agents, filters, this is paired with the default websearch included with OpenWebUI and works really well i hit 20-30 links usually during search where i used to only get 4-5 reliable ones Wayback_archive: this tool is called whenever a site is blocked through normal access to be able to get the data anyway from the latest archived version of it (found this idea here as well on reddit but i made a custom version/tool to save on tokens instead of using it as a prompt) read_microsoft_learn: a tool to enable to model to lookup anything on microsoft learn, to help itself C#/WPF/NET or anything else it's unsure of ----------------------- Im trying to figure out what to build out next after im done the document creator... Im going to try and add SMS, since emails are usually more of a &quot;silent&quot; alert, at least for me.. But right now I can literally tell this thing to create a flyer for my services then go find emails of local business owners and send it to them and it will... While i go do something else... This is crazy im going to make skynet ;P &#32; submitted by &#32; /u/Creative-Type9411 [link] &#32; [comments]

</details>