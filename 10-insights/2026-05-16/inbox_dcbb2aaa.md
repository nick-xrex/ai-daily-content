---
id: inbox_dcbb2aaa
date: 2026-05-16
source_ref: "[[00-inbox/.../inbox_dcbb2aaa]]"
title: "GitHub - richardr1126/openreader: An open-source read-along document reader server with high-quality TTS options, synchronized highlighting, and audiobook export for EPUB, PDF, DOCX, TXT, and MD."
url: https://www.reddit.com/r/LocalLLaMA/comments/1tf15eh/github_richardr1126openreader_an_opensource/
source: reddit-localllama
published_at: 2026-05-16T18:12:10+00:00
fetched_at: 2026-05-18T04:11:13.955919+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenReader v3.0.0（開源文件 TTS 讀取與有聲書匯出工具）發布。支援 EPUB、PDF、TXT、Markdown、DOCX，整合 OpenAI / Replicate / Deepinfra / 自託管 API（Kokoro-FastAPI、KittenTTS-FastAPI）。v3.0.0 新增音訊跨頁預加載、持久快取、管理員面板（執行時管理多個 TTS 提供者及 API 金鑰）、網站功能旗標管理（無需重新部署）。支援 SQLite / Postgres 後端與嵌入 SeaweedFS 或外部 S3，可匯出 m4b/mp3 有聲書含章節詮釋資料。已上線 1 年多，累積 300+ 星。"
key_points:
  - "v3.0.0 功能：音訊預加載機制、伺服器端持久快取、執行時可管理的 Admin 面板與功能旗標（無須重新部署）"
  - "多 TTS 提供者支援與自託管相容 API（Kokoro-FastAPI、KittenTTS-FastAPI）"
  - "文件格式支援完整（EPUB、PDF、TXT、Markdown、DOCX）且支援 m4b/mp3 有聲書匯出含章節詮釋資料"
tags: [tts, openreader, document-reader, audiobook, self-hosted]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## GitHub - richardr1126/openreader: An open-source read-along document reader server with high-quality TTS options, synchronized highlighting, and audiobook export for EPUB, PDF, DOCX, TXT, and MD.

OpenReader v3.0.0（開源文件 TTS 讀取與有聲書匯出工具）發布。支援 EPUB、PDF、TXT、Markdown、DOCX，整合 OpenAI / Replicate / Deepinfra / 自託管 API（Kokoro-FastAPI、KittenTTS-FastAPI）。v3.0.0 新增音訊跨頁預加載、持久快取、管理員面板（執行時管理多個 TTS 提供者及 API 金鑰）、網站功能旗標管理（無需重新部署）。支援 SQLite / Postgres 後端與嵌入 SeaweedFS 或外部 S3，可匯出 m4b/mp3 有聲書含章節詮釋資料。已上線 1 年多，累積 300+ 星。

### 重點
- v3.0.0 功能：音訊預加載機制、伺服器端持久快取、執行時可管理的 Admin 面板與功能旗標（無須重新部署）
- 多 TTS 提供者支援與自託管相容 API（Kokoro-FastAPI、KittenTTS-FastAPI）
- 文件格式支援完整（EPUB、PDF、TXT、Markdown、DOCX）且支援 m4b/mp3 有聲書匯出含章節詮釋資料

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tf15eh/github_richardr1126openreader_an_opensource/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# GitHub - richardr1126/openreader: An open-source read-along document reader server with high-quality TTS options, synchronized highlighting, and audiobook export for EPUB, PDF, DOCX, TXT, and MD.

Sharing my latest release of OpenReader v3.0.0, an open-source text-to-speech document reader and audiobook exporter. It has been live for over a year now, and slowly has gained 300+ GitHub stars. What is OpenReader? A Next.js web app for reading and listening to EPUB, PDF, TXT, Markdown, and DOCX files. Supports multiple TTS providers: OpenAI, Replicate, Deepinfra, and self-hosted OpenAI-compatible APIs (like Kokoro-FastAPI , KittenTTS-FastAPI ). Self-hosted: your documents, TTS audio, and settings all live on your own server in SQLite or Postgres and Embedded SeaweedFS or External S3. Audiobook export: generate and download m4b/mp3 audiobooks with chapter metadata via ffmpeg. What's new in v3.0.0? TTS now preloads audio across multiple pages ahead of where you are. Audio is cached persistently on the server's embedded or external object storage. New Admin panel (set ADMIN_EMAILS in your env) for managing multiple named TTS providers with separate API keys. Site-wide feature flags (user signups, provider restrictions, etc.) are now manageable from the Admin panel at runtime without redeploying. Get Started: https://github.com/richardr1126/openreader Docker quick start: https://docs.openreader.richardr.dev Would love your feedback, feature requests, or contributions! &#32; submitted by &#32; /u/richardr1126 [link] &#32; [comments]

</details>