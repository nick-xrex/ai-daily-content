---
id: inbox_0336fa96
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/7/github-code-component/#atom-everything"
author: ""
published_at: 2026-07-07T16:18:16+00:00
fetched_at: 2026-07-07T23:08:51.578003+00:00
content_hash: "2943e96bca6d506213e8d1b8d01dd0b3df3429a6a00f2ec2aea0307a562ed34a"
lang: en
caption_quality: None
raw: true
topics: []
---

# github-code Web Component

Tool: github-code Web Component 
 An experimental Web Component built using GPT-5.5 and the following prompt : 
 
 let's build a Web Component for embedding code from GitHub 
 &lt;github-code href="https://github.com/simonw/sqlite-ast/blob/437c759129154f05296324a7f82aa1246340dd14/sqlite_ast/parser.py#L9-L18"&gt;&lt;/github-code&gt; 
 It takes URLs like that, converts them to https://raw.githubusercontent.com/simonw/sqlite-ast/437c759129154f05296324a7f82aa1246340dd14/sqlite_ast/parser.py, then uses fetch() to fetch them and displays the specified range of lines - with line numbers, no syntax highlighting though 
 Show me a preview web browser so I can see your work 
 
 Here's what it looks like embedded on this page: 
 
 
 
 Tags: github , web-components , gpt