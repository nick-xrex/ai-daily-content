---
id: inbox_1902da08
source: medium-towards-data-science
source_type: rss
url: "https://towardsdatascience.com/my-ai-couldnt-see-my-files-i-built-a-zero-dependency-mcp-server/"
author: "Emmimal P Alexander"
published_at: 2026-06-05T16:30:00+00:00
fetched_at: 2026-06-05T18:00:44.372465+00:00
content_hash: "e6ecc741287b12c79ad0774528745bd5fc95b3be1d9b666f249fdb3e1b65a308"
lang: en
caption_quality: None
raw: true
topics: []
---

# My AI Couldn’t See My Files — I Built a Zero-Dependency MCP Server

I got tired of copying files into an AI chat just to get feedback. So I built a pure Python MCP server that gives AI tools direct access to my local project—no frameworks, no dependencies. It runs over stdio for local use and switches to HTTP/SSE for concurrent clients with a single flag. The result: 5 clients, under 50ms, and a design that stays simple without sacrificing capability. 
 The post My AI Couldn’t See My Files — I Built a Zero-Dependency MCP Server appeared first on Towards Data Science .