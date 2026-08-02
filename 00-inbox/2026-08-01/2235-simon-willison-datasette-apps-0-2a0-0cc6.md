---
id: inbox_09cfa65d
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Aug/1/datasette-apps/#atom-everything"
author: ""
published_at: 2026-08-01T21:23:56+00:00
fetched_at: 2026-08-01T22:35:58.875208+00:00
content_hash: "0cc66b90b24d7cda0d55f115c7b72bd30a8f08f2fcc07789ed9ac037162e3708"
lang: en
caption_quality: None
raw: true
topics: []
---

# datasette-apps 0.2a0

Release: datasette-apps 0.2a0 
 
 Changes that improve Datasette Apps when created and edited using Datasette Agent : 
 
 New app_debug() tool allowing agent to open an app (invisibly) and test it using JavaScript. #33 
 New app_list() tool for listing apps the user has permission to edit, so the agent can edit them. #36 
 
 
 The app_debug() tool is pretty neat: it works by displaying the app in a opacity: 0 iframe with pointer-events: none (so it can't be seen or interacted with) and then executing agent-provided JavaScript inside that sandboxed iframe. This means the agent can smoke test that the app is working and even do things like measure the dimensions of different elements. 
 This uses the new context.browser_task() mechanism added in datasette-agent 0.4a0 . 
 
 
 Tags: iframes , datasette , datasette-apps