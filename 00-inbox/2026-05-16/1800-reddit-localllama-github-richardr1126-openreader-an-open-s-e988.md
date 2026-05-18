---
id: inbox_dcbb2aaa
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tf15eh/github_richardr1126openreader_an_opensource/"
author: "/u/richardr1126"
published_at: 2026-05-16T18:12:10+00:00
fetched_at: 2026-05-17T18:00:47.158788+00:00
content_hash: "e988a184baeeb7525fbde69442fa3611f98912d609ca6395d8d93022e613b61b"
lang: en
caption_quality: None
raw: true
topics: []
---

# GitHub - richardr1126/openreader: An open-source read-along document reader server with high-quality TTS options, synchronized highlighting, and audiobook export for EPUB, PDF, DOCX, TXT, and MD.

Sharing my latest release of OpenReader v3.0.0, an open-source text-to-speech document reader and audiobook exporter. It has been live for over a year now, and slowly has gained 300+ GitHub stars. What is OpenReader? A Next.js web app for reading and listening to EPUB, PDF, TXT, Markdown, and DOCX files. Supports multiple TTS providers: OpenAI, Replicate, Deepinfra, and self-hosted OpenAI-compatible APIs (like Kokoro-FastAPI , KittenTTS-FastAPI ). Self-hosted: your documents, TTS audio, and settings all live on your own server in SQLite or Postgres and Embedded SeaweedFS or External S3. Audiobook export: generate and download m4b/mp3 audiobooks with chapter metadata via ffmpeg. What's new in v3.0.0? TTS now preloads audio across multiple pages ahead of where you are. Audio is cached persistently on the server's embedded or external object storage. New Admin panel (set ADMIN_EMAILS in your env) for managing multiple named TTS providers with separate API keys. Site-wide feature flags (user signups, provider restrictions, etc.) are now manageable from the Admin panel at runtime without redeploying. Get Started: https://github.com/richardr1126/openreader Docker quick start: https://docs.openreader.richardr.dev Would love your feedback, feature requests, or contributions! &#32; submitted by &#32; /u/richardr1126 [link] &#32; [comments]