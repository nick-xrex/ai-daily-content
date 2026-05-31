---
id: inbox_14be2339
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/May/30/pyodide-asgi-browser/#atom-everything"
author: ""
published_at: 2026-05-30T21:02:16+00:00
fetched_at: 2026-05-31T00:39:18.283423+00:00
content_hash: "fb9a2a7a64dd171c6a65c4371093a1990172356293393caae0c54fa057f51e0f"
lang: en
caption_quality: None
raw: true
topics: []
---

# Running Python ASGI apps in the browser via Pyodide + a service worker

Research: Running Python ASGI apps in the browser via Pyodide + a service worker 
 Datasette Lite is my version of Datasette that runs entirely in the browser using Pyodide in WebAssembly. 
 When I first built it four years ago I used Web Workers and code that intercepts navigation operations and fetches the generated HTML by running the Python app. 
 This worked, but had the disadvantage that any JavaScript in &lt;script&gt; tags would not be executed - breaking some Datasette functionality and a whole lot of Datasette plugins. 
 This morning I set Claude Opus 4.8 the task (in Claude Code for web) of figuring out how to run Python ASGI apps in Pyodide using Service Workers instead, and it seems to work! Here's a basic ASGI FastCGI demo and here's a demo that runs Datasette 1.0a31 . 
 I'm still getting my head around exactly how it works, but once I've done that I plan to upgrade Datasette Lite itself. 
 
 
 Tags: javascript , python , datasette , asgi , service-workers , pyodide , datasette-lite , claude-code