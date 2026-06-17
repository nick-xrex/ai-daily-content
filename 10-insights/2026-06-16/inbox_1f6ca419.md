---
id: inbox_1f6ca419
date: 2026-06-16
source_ref: "[[00-inbox/2026-06-16/2200-simon-willison-datasette-tailscale-0-1a0-808b]]"
title: "datasette-tailscale 0.1a0"
url: https://simonwillison.net/2026/Jun/16/datasette-tailscale/#atom-everything
source: simon-willison
published_at: 2026-06-16T16:18:20+00:00
fetched_at: 2026-06-17T22:05:50.519023+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "`datasette-tailscale` 是 Datasette 的一個新實驗性 alpha 插件（版本 0.1a0），由 Simon Willison 開發。使用者可以通過簡單的命令行命令將本機 Datasette 服務器發佈到 Tailscale 虛擬網路（Tailnet）上，實現安全的遠程訪問。命令格式為 `datasette tailscale mydata.db --ts-authkey tskey-auth-xxxx --ts-hostname datasette-preview`，啟動後即可通過 `http://datasette-preview/` 訪問。插件的底層使用 tailscale-rs 庫的 Python 綁定來實現代理機制。作者已向 tailscale-rs 官方提交 issue，詢問是否有更簡潔的代理設置方式。"
key_points:
  - "datasette-tailscale 0.1a0 提供一行命令發佈到 Tailnet：`datasette tailscale [db] --ts-authkey [key] --ts-hostname [hostname]`"
  - "底層實現：使用 tailscale-rs Python 綁定和 sidecar 代理機制"
  - "當前狀態：實驗性 alpha，作者尋求代理機制的簡化方案"
tags: [datasette, tailscale, deployment, plugin, networking]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-tailscale 0.1a0

`datasette-tailscale` 是 Datasette 的一個新實驗性 alpha 插件（版本 0.1a0），由 Simon Willison 開發。使用者可以通過簡單的命令行命令將本機 Datasette 服務器發佈到 Tailscale 虛擬網路（Tailnet）上，實現安全的遠程訪問。命令格式為 `datasette tailscale mydata.db --ts-authkey tskey-auth-xxxx --ts-hostname datasette-preview`，啟動後即可通過 `http://datasette-preview/` 訪問。插件的底層使用 tailscale-rs 庫的 Python 綁定來實現代理機制。作者已向 tailscale-rs 官方提交 issue，詢問是否有更簡潔的代理設置方式。

### 重點
- datasette-tailscale 0.1a0 提供一行命令發佈到 Tailnet：`datasette tailscale [db] --ts-authkey [key] --ts-hostname [hostname]`
- 底層實現：使用 tailscale-rs Python 綁定和 sidecar 代理機制
- 當前狀態：實驗性 alpha，作者尋求代理機制的簡化方案

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/16/datasette-tailscale/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-tailscale 0.1a0 
 A very experimental alpha plugin which lets you do this: 
 datasette tailscale mydata.db \
 --ts-authkey tskey-auth-xxxx --ts-hostname datasette-preview
 
 This starts a localhost Datasette server with a Tailscale sidecar that connects it to your Tailnet, such that http://datasette-preview/ serves Datasette. 
 It's using the Python bindings for the experimental tailscale-rs library. I filed an issue asking if there's a cleaner way of setting up the proxy mechanism. 
 
 
 Tags: datasette , tailscale

</details>