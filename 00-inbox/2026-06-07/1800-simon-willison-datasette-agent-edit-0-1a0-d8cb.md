---
id: inbox_47ccd51e
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jun/7/datasette-agent-edit/#atom-everything"
author: ""
published_at: 2026-06-07T23:56:38+00:00
fetched_at: 2026-06-08T18:00:55.694446+00:00
content_hash: "d8cb9164d0fc175d5734f82d7cf9e2aebcbf66d887c0dacab58fda2d8dca22a9"
lang: en
caption_quality: None
raw: true
topics: []
---

# datasette-agent-edit 0.1a0

Release: datasette-agent-edit 0.1a0 
 I'm planning several plugins for Datasette Agent which can make edits to existing pieces of text - things like collaborative Markdown editing, updating large SQL queries, and editing SVG files. 
 Agentic editing of text is a little tricky to get right. My favorite published design for this is for the Claude text editor , which implements the following tools: 
 
 view - view sections of a file, with line numbers added to every line. 
 str_replace - find an exact old_str and replace it with new_str - fail if the original string is not unique 
 insert - insert the specified text after the specified line number 
 
 Rather than recreate these patterns for every plugin that needs them I decided to create this base plugin, datasette-agent-edit , which implements the core tools in a way that allows them to be adapted for other plugins. 
 
 
 Tags: ai , datasette , generative-ai , llms , llm-tool-use , datasette-agent