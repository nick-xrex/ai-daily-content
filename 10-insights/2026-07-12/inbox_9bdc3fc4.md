---
id: inbox_9bdc3fc4
date: 2026-07-12
source_ref: "[[00-inbox/2026-07-12/0040-simon-willison-shot-scraper-1-11-149f]]"
title: "shot-scraper 1.11"
url: https://simonwillison.net/2026/Jul/12/shot-scraper/#atom-everything
source: simon-willison
published_at: 2026-07-12T23:46:52+00:00
fetched_at: 2026-07-13T00:45:06.379765+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 發布 shot-scraper 1.11，主要改進伺服器啟動容錯和命令選項一致性。伺服器連線等待時間從固定 1 秒延長至最多 30 秒（#197），polling 檢測埠可用性，避免在伺服器啟動緩慢時超時——影響 `shot-scraper multi` 和 `shot-scraper video` 兩個子命令。新增 `--js-file` 選項讓 pdf、html、accessibility、har 等命令可從本地檔案、stdin 或 GitHub (`gh:username/script`) 載入 JavaScript，作為字串型 `--javascript` 的替代（#192）。`javascript` 和 `html` 指令加入 `--timeout` 以保持選項一致性（#118）。"
key_points:
  - "伺服器連線等待時間改進：1 秒 → 30 秒 polling，改善慢啟動伺服器的可靠性"
  - "新增 `--js-file` 選項支援本地檔案 / stdin / `gh:` GitHub 載入 JavaScript，替代直傳字串"
  - "新增 `--timeout` 選項到 `javascript` 和 `html` 命令，強化命令行介面一致性"
tags: [shot-scraper, devtool-release, command-line-ux]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## shot-scraper 1.11

Simon Willison 發布 shot-scraper 1.11，主要改進伺服器啟動容錯和命令選項一致性。伺服器連線等待時間從固定 1 秒延長至最多 30 秒（#197），polling 檢測埠可用性，避免在伺服器啟動緩慢時超時——影響 `shot-scraper multi` 和 `shot-scraper video` 兩個子命令。新增 `--js-file` 選項讓 pdf、html、accessibility、har 等命令可從本地檔案、stdin 或 GitHub (`gh:username/script`) 載入 JavaScript，作為字串型 `--javascript` 的替代（#192）。`javascript` 和 `html` 指令加入 `--timeout` 以保持選項一致性（#118）。

### 重點
- 伺服器連線等待時間改進：1 秒 → 30 秒 polling，改善慢啟動伺服器的可靠性
- 新增 `--js-file` 選項支援本地檔案 / stdin / `gh:` GitHub 載入 JavaScript，替代直傳字串
- 新增 `--timeout` 選項到 `javascript` 和 `html` 命令，強化命令行介面一致性

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/12/shot-scraper/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: shot-scraper 1.11 
 Some minor improvements, mainly around command option consistency and making the server: mechanism used by both shot-scraper video and shot-scraper multi work if the server takes longer than a second to start serving traffic. 
 
 
 server: processes used by shot-scraper multi and shot-scraper video now wait up to 30 seconds for the target URL to accept connections, polling for port availability and replacing the previous fixed one-second delay. #197 
 The shot-scraper , pdf , html , accessibility and har commands now have a --js-file option for loading JavaScript from a local file, standard input or gh:username/script , as an alternative to --javascript which accepts the string of JavaScript directly as an argument. #192 
 shot-scraper multi supports the equivalent js_file: YAML key. 
 The shot-scraper javascript and shot-scraper html commands now have a --timeout option for consistency with other commands. #118 
 
 
 
 
 Tags: shot-scraper

</details>