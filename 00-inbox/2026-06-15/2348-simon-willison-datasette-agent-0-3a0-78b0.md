---
id: inbox_d9bb05e4
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jun/15/datasette-agent/#atom-everything"
author: ""
published_at: 2026-06-15T17:19:27+00:00
fetched_at: 2026-06-15T23:48:25.550817+00:00
content_hash: "78b0ffa9a1a2c8225ba574608653f08c0f498123c057bf44e29ba3ebdd3a6a13"
lang: en
caption_quality: None
raw: true
topics: []
---

# datasette-agent 0.3a0

Release: datasette-agent 0.3a0 
 
 
 New tool, execute_write_sql , which requests user approval and then writes to a database - taking user permissions into account. #27 
 
 
 I added a mechanism for asking user approval in datasette agent 0.2a0 . The new execute_write_sql tool can now prompt the user for all kinds of useful operations. Here's an example where I add some pelican sightings to my pelican_sightings table: 
 
 The new version also enhances the datasette agent chat terminal mode to support approvals, and adds several new options including --unsafe mode for auto-approving them: 
 
 
 datasette agent chat can execute tools that require user approval. #30 
 Three new options for datasette agent chat - --root to run as root, --yes to approve all ask user questions, and --unsafe for both. 
 Tools can now provide plain text alternatives to HTML, for display in the datasette agent chat CLI. #31 
 
 
 The datasette agent chat content.db -m gpt-5.5 --unsafe command can now be used to chat directly with a specific database and directly modify it through prompts like "create a notes table", "add a note about X" etc. 
 
 
 Tags: projects , ai , datasette , annotated-release-notes , generative-ai , llms , llm-tool-use , datasette-agent