---
id: inbox_df16c538
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tdefy6/llamastudio_webui_for_llamaserver_management/"
author: "/u/m94301"
published_at: 2026-05-14T23:09:05+00:00
fetched_at: 2026-05-15T18:34:22.464534+00:00
content_hash: "d671cd8d08e91427a4473a7a8488baf81deced298626bc3b6991972b43052ff1"
lang: en
caption_quality: None
raw: true
topics: []
---

# Llama-Studio, WebUI for llama-server Management

Hey all, I have built myself a WebUI for configuring and managing llama-server sessions, and want to share the code and concept. Python and a bit of JS. Hack away! Local only. https://github.com/m94301/llama-studio The major use case is running various instances of llama-server on fixed ports to act as infrastructure for home development (and entertainment) frameworks. Read: Fiddling with settings, comparing experimental builds to mainline, and optimizing. Also good for everyday fooling around. Configs are saved per model in a json, consisting of all launch args and optional paths for custom llama-server. I have a launch arg browser with search using the current llama-server's actual -help output. I hate forgetting a launch arg format and having to open a new terminal to do -help. Spec MTP what? Draft type who? Launch to choice of GPU, monitor VRAM, load, and temp. And a somewhat rudimentary VRAM calculator to help estimate what fits where when using what quant. Last, a reasonable mobile interface to run tests and fool with config on phone when in a basement or IT closet. Show and hide logs, start, stop, change config. Less keystrokes on tiny phone keyboards. Sanity +100. &#32; submitted by &#32; /u/m94301 [link] &#32; [comments]