---
id: inbox_b995e982
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_b995e982]]"
title: "Sharing \&#34;cull\&#34; : my open-source dataset tool for image scraping &amp; classification &amp; captioning pipeline"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t9jub0/sharing_cull_my_opensource_dataset_tool_for_image/
source: reddit-localllama
published_at: 2026-05-10T21:42:02+00:00
fetched_at: 2026-05-11T02:23:38.624208+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶開源發佈資料集策展工具 Cull，用於 AI 影像訓練資料的端到端準備。支援從 Civitai、X/Twitter、Reddit、Discord 及 gallery-dl 支援的 340+ 網站爬取影像，每張隨附來源提示詞。使用 17 欄位 JSON schema 的視覺語言模型進行自動分類，可切換本地 LM Studio 或雲端 Groq。Flask + Alpine.js 前端提供整理介面、品質與關聯度評分、ZIP 匯出。已應用於 300 張影像的 LoRA 微調及 10 萬張影像的完整微調。開源 MIT，無資料庫與 Docker 依賴，內建 Claude Code 技能包及自動更新機制。"
key_points:
  - "工具名稱 Cull（https://github.com/tlennon-ie/cull），支援 Civitai、X/Twitter、Reddit、Discord 及 gallery-dl 的 340+ 影像來源"
  - "分類與標題：使用 VLM 進行 17 欄位 JSON 結構化分類，自動生成 SD prompt、booru tags、自然語言描述"
  - "實際應用案例：300 張影像 LoRA 微調與 100K 影像完整微調資料集準備"
tags: [dataset-curation, image-pipeline, vlm-classification, open-source-tool, fine-tuning]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Sharing \"cull\" : my open-source dataset tool for image scraping & classification & captioning pipeline

用戶開源發佈資料集策展工具 Cull，用於 AI 影像訓練資料的端到端準備。支援從 Civitai、X/Twitter、Reddit、Discord 及 gallery-dl 支援的 340+ 網站爬取影像，每張隨附來源提示詞。使用 17 欄位 JSON schema 的視覺語言模型進行自動分類，可切換本地 LM Studio 或雲端 Groq。Flask + Alpine.js 前端提供整理介面、品質與關聯度評分、ZIP 匯出。已應用於 300 張影像的 LoRA 微調及 10 萬張影像的完整微調。開源 MIT，無資料庫與 Docker 依賴，內建 Claude Code 技能包及自動更新機制。

### 重點
- 工具名稱 Cull（https://github.com/tlennon-ie/cull），支援 Civitai、X/Twitter、Reddit、Discord 及 gallery-dl 的 340+ 影像來源
- 分類與標題：使用 VLM 進行 17 欄位 JSON 結構化分類，自動生成 SD prompt、booru tags、自然語言描述
- 實際應用案例：300 張影像 LoRA 微調與 100K 影像完整微調資料集準備

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t9jub0/sharing_cull_my_opensource_dataset_tool_for_image/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Sharing "cull" : my open-source dataset tool for image scraping & classification & captioning pipeline

I open-sourced a tool I built and am maintaining called Cull . It’s a machine curation engine for AI image datasets, the kind of work that eats hours every time you want to train a LoRA, build a reference library, or just classify an archive that isn’t a 100,000-file mess. What it does, end to end Scrapes from Civitai (.com and .red), X/Twitter, Reddit, Discord, plus any URL gallery-dl supports (Pixiv, DeviantArt, the booru family, ArtStation, Tumblr, FurAffinity / e621, Imgur, Flickr, and ~340 others). Drops every image plus its source-side prompt into a local queue. Per-source dedup, no database. Classifies each image with a vision-language model, multiple LM Studio instances for local, Groq for cloud, anything OpenAI-compatible — using a strict 17-field JSON schema, so you don’t get free-text replies you have to regex into shape. Sorts the keepers into category folders next to their .txt prompt and a .vision.json audit record. Two score gates (overall quality + topic relevance) you tune in the UI. Surfaces everything through a Flask + Alpine dashboard: start/stop, source toggles, gallery, prompt editor, ZIP export, per-source stats. Two example use cases I actually used it for: LoRA (300 images) &amp; Finetune (100,000 images) dataset prep. Give it a topic such as Female Influencer or {artist} style art set AUTO_CAPTION_ENABLED=true if you want it to caption images or false if you want it to scrape images (and still store any found prompts from the posts it scraped from) and set whatever style prompting you want. Walk away. Come back to a folder of triaged images split by quality and category, each with a generated SD-prompt .txt next to it. ZIP-export the filtered view straight into your trainer. Ingesting a prompt-less archive. Point LOCAL_IMPORT_DIR at a folder of bare JPEGs (or paste a gallery-dl URL list) Toggle off the prompt requirement, turn on auto-captioning. Every image is classified and sorted, gets a SD-prompt / booru-tags / natural-language caption written by the same vision call that classifies it. So you can train on a years-old archive without curating prompts by hand. Links Repo: https://github.com/tlennon-ie/cull Screenshots: https://imgur.com/a/kSvsAW9 Roadmap is going to keep refining around what people actually use it for. On my list: - more vision-worker backends - Improved proper requeue UI - a small headless CLI, - Video scraping , classification etc A few things worth mentioning: - Vision worker is pluggable via a registry. Subclass BaseVisionWorker, register, done. Two LM Studio endpoints can run in parallel; there's a keepalive worker that pings every 15s if your local server has aggressive idle-unload, and an idle-unloader for when you want VRAM back. - It ships with a Claude Code skill bundle in .claude/skills/ (cull-helper, lmstudio-vision, metadata-schema) and three sub-agents in .claude/agents/. If you use Claude Code, Cursor, Aider, Codex, or anything that respects those files, your AI assistant knows cull's load-bearing seams (categories, queue Protocol, vision-worker base class, the strict-output schema) before it touches anything. - Self-updater is in: toast in the dashboard, click Update, pulls from origin/main and relaunches. Stack: Python 3.10+, Flask, Alpine.js, Pillow, Playwright (for the X scraper), gallery-dl. Single machine. No Redis, no DB, no Docker required. MIT licensed. &#32; submitted by &#32; /u/Compunerd3 [link] &#32; [comments]

</details>