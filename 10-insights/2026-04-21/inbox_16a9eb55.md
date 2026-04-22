---
id: inbox_16a9eb55
date: 2026-04-21
source_ref: "[[00-inbox/.../inbox_16a9eb55]]"
title: "I got tired of walking back to my desk to check training runs"
url: https://blog.stackademic.com/i-got-tired-of-walking-back-to-my-desk-to-check-training-runs-6c0d21092196?source=rss----d1baaa8417a4---4
source: medium-stackademic
published_at: 2026-04-21T12:12:49+00:00
fetched_at: 2026-04-22T01:05:22.478456+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Fernsicht 是開源工具，用一行命令 `fernsicht run -- <command>` 解決開發者監控長時間執行任務的痛點（ML 訓練、構建、測試、資料傳輸）。核心設計透過 WebRTC 建立 P2P 連接（非雲端中轉），保護數據隱私（避免洩露訓練數據標籤）並降低延遲至 80–120ms。工具自動偵測常見進度格式（tqdm、pip、snakemake、make），支援 Python/R 單行 SDK 導入；使用者可從任何地點通過 URL 監控進度，支援手機離線檢查、Slack 貼文分享、多人即時觀看，無須帳號。AGPL-3.0 開源，Go 靜態二進制，零依賴。"
key_points:
  - "P2P WebRTC 架構避免雲端中轉：隱私 + 低延遲（80–120ms），比雲端中繼快"
  - "一行命令監控任何長時間任務（fernsicht run -- <command>），支援 tqdm/pip/snakemake 自動檢測，也可自訂 __fernsicht__ progress 消息"
  - "無帳號即可分享 URL，支援手機離線檢查、Slack 貼文分享、多人即時觀看"
tags: [peer-to-peer, webrtc, monitoring, ml-tools, developer-experience]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## I got tired of walking back to my desk to check training runs

Fernsicht 是開源工具，用一行命令 `fernsicht run -- <command>` 解決開發者監控長時間執行任務的痛點（ML 訓練、構建、測試、資料傳輸）。核心設計透過 WebRTC 建立 P2P 連接（非雲端中轉），保護數據隱私（避免洩露訓練數據標籤）並降低延遲至 80–120ms。工具自動偵測常見進度格式（tqdm、pip、snakemake、make），支援 Python/R 單行 SDK 導入；使用者可從任何地點通過 URL 監控進度，支援手機離線檢查、Slack 貼文分享、多人即時觀看，無須帳號。AGPL-3.0 開源，Go 靜態二進制，零依賴。

### 重點
- P2P WebRTC 架構避免雲端中轉：隱私 + 低延遲（80–120ms），比雲端中繼快
- 一行命令監控任何長時間任務（fernsicht run -- <command>），支援 tqdm/pip/snakemake 自動檢測，也可自訂 __fernsicht__ progress 消息
- 無帳號即可分享 URL，支援手機離線檢查、Slack 貼文分享、多人即時觀看

**原文：** [medium-stackademic](https://blog.stackademic.com/i-got-tired-of-walking-back-to-my-desk-to-check-training-runs-6c0d21092196?source=rss----d1baaa8417a4---4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

-d1baaa8417a4---4"
author: "Thomas Konstantinovsky"
published_at: 2026-04-21T12:12:49+00:00
fetched_at: 2026-04-21T21:46:30.886892+00:00
content_hash: "bbcbdd006db066ea3ff8498a69d126362d6dc7dc04b96174d2ac1506ae098614"
lang: en
caption_quality: None
raw: true
topics: []
---

# I got tired of walking back to my desk to check training runs

<figure><img alt="" src="https://cdn-images-1.medium.com/max/1024/1*uwH45gpqYw-Zo7gKeOOunw.png" /></figure><p>Last month I left a training run going overnight, drove to a coffee shop in the morning, opened my laptop and realized I’d forgotten to tail the logs over SSH. The run had crashed forty minutes in. I’d driven there for nothing.</p><p>This wasn’t the first time. Long-running anything an ML training loop, a snakemake pipeline, a data backfill, a build exists in this weird limbo where you can’t sit and watch it, but you also can’t really trust it to finish without checking. You hack together a Slack webhook. You tail a log over SSH from your phone, squinting. You write a while true that pings you at 25%, 50%, 75%. You never get it quite right.</p><p>So I built <a href="https://app.fernsicht.space/"><strong>Fernsicht</strong></a>.</p><h3>One line. Any command. A URL you can open from anywhere.</h3><pre>fernsicht run -- python train.py</pre><p>The same command works for anything that takes longer than you want to sit there:</p><pre>fernsicht run -- snakemake --cores 8           # bioinformatics pipeline<br />fernsicht run -- pytest tests/ -q              # a slow test suite<br />fernsicht run -- docker build -t myapp .       # a fat build<br />fernsicht run -- rsync -av src/ backup:/data/  # a long transfer<br />fernsicht run -- pip install -r requirements.txt</pre><p>No code change, no SDK, no “wrapper-friendly” version of your script required. fernsicht run -- eats any command, forwards its stdout to your terminal untouched, and publishes the progress it can detect to the URL in the background.</p><p>Once the URL is live you can:</p><ul><li>Check it on your phone while you’re at lunch.</li><li>Share it in Slack or in a PR comment so a teammate can watch too no account needed on their end.</li><li>Close your laptop, come back hours later, reopen the same URL, and pick up where you left off. The sender keeps the session alive; viewers drop in and out freely.</li><li>Run fernsicht url in a second terminal to reprint the URL if it scrolled out of your history.</li></ul><p>That’s it. That’s the whole product.</p><figure><img alt="" src="https://cdn-images-1.medium.com/max/1024/1*suSf8QO2NCPgmR1jtdASbg.png" /></figure><h3>The thing I actually care about: no server in the middle</h3><p>Most “watch your training from your phone” tools do it by sending your telemetry to their cloud. Fernsicht doesn’t. After a three-second handshake, the connection is fully peer-to-peer over WebRTC. Your progress bytes go from your machine directly to the viewer’s browser. The signalling server only helps them find each other it never sees your data, and it forgets you exist as soon as the handshake completes.</p><p>This matters for two reasons:</p><ol><li><strong>Privacy.</strong> Training data labels often leak through progress messages (“processed 1,247 / 50,000 patient records”). I’d rather not pipe that through someone else’s SaaS.</li><li><strong>Latency.</strong> P2P between two devices on decent internet is ~80–120ms. A cloud relay adds a round trip you don’t need.</li></ol><figure><img alt="" src="https://cdn-images-1.medium.com/max/1024/1*O1ETBd5hs58j64uwJaIsCw.png" /></figure><h3>Works with what you already have</h3><ul><li><strong>tqdm</strong> — detected automatically.</li><li><strong>pip / snakemake / make</strong> — detected automatically.</li><li><strong>Anything else</strong> — emit a single line like __fernsicht__ progress 42/100 from any language, any process. The CLI strips it before forwarding stdout to your terminal.</li></ul><p>If you’re in Python or R, there’s a one-import SDK:</p><pre>from fernsicht import blick<br /><br />for item in blick(items, desc=&quot;Training&quot;):<br />    process(item)</pre><pre>library(fernsicht)<br />results &lt;- blick(items, process)</pre><p>Or visit <a href="https://app.fernsicht.space">app.fernsicht.space</a> to see the install options.</p><p>It’s AGPL-3.0 (with a commercial opt-out), written in Go, zero-dep static binary, and I work on it in my spare time.</p><p>If you end up using it, I’d love to hear what you ran it on. Issues, PRs, and shouty feedback welcome on <a href="https://github.com/MuteJester/Fernsicht">GitHub</a>.</p><img alt="" height="1" src="https://medium.com/_/stat?event=post.clientViewed&amp;referrerSource=full_rss&amp;postId=6c0d21092196" width="1" /><hr /><p><a href="https://blog.stackademic.com/i-got-tired-of-walking-back-to-my-desk-to-check-training-runs-6c0d21092196">I got tired of walking back to my desk to check training runs</a> was originally published in <a href="https://blog.stackademic.com">Stackademic</a> on Medium, where people are continuing the conversation by highlighting and responding to this story.</p>

</details>