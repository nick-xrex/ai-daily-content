---
id: inbox_f0012655
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/May/4/redis-array/#atom-everything"
author: ""
published_at: 2026-05-04T15:53:57+00:00
fetched_at: 2026-05-05T08:19:10.539201+00:00
content_hash: "4e5dc00e6485d17028364d5399396e33dd4cd0ccbc7c6ca16d088068716882fa"
lang: en
caption_quality: None
raw: true
topics: []
---

# Redis Array Playground

<p><strong>Tool:</strong> <a href="https://tools.simonwillison.net/redis-array">Redis Array Playground</a></p>
        <p>Salvatore Sanfilippo submitted <a href="https://github.com/redis/redis/pull/15162">a PR</a> adding a new data type - arrays - to Redis. </p>
<p>The new commands are <code>ARCOUNT</code>, <code>ARDEL</code>, <code>ARDELRANGE</code>, <code>ARGET</code>, <code>ARGETRANGE</code>, <code>ARGREP</code>, <code>ARINFO</code>, <code>ARINSERT</code>, <code>ARLASTITEMS</code>, <code>ARLEN</code>, <code>ARMGET</code>, <code>ARMSET</code>, <code>ARNEXT</code>, <code>AROP</code>, <code>ARRING</code>, <code>ARSCAN</code>, <code>ARSEEK</code>, <code>ARSET</code>.</p>
<p>The implementation is currently available in a branch, so I <a href="https://github.com/simonw/tools/pull/277">had Claude Code for web</a> 
build this interactive playground for trying out the new commands in a WASM-compiled build of a subset of Redis running in the browser.</p>
<p><img alt="Screenshot of a Redis command builder UI. Left sidebar shows commands ARSCAN, ARSEEK, ARSET. Main panel has a &quot;predicate oneof&quot; section with a MATCH dropdown and value CHERRY, plus a &quot;+ add another&quot; button. Below is &quot;options (optional) oneof&quot; with checkboxes: AND (checked), OR (unchecked), LIMIT (checked, value 10), WITHVALUES (checked), NOCASE (checked). COMMAND section shows: ARGREP myarr - + MATCH CHERRY AND LIMIT 10 WITHVALUES NOCASE. A red &quot;Run command&quot; button is below. REPLY section shows &quot;(no reply yet)&quot;." src="https://static.simonwillison.net/static/2026/redis-array-explorer-card.jpg" /></p>
<p>The most interesting new command is <code>ARGREP</code> which can run a server-side grep against a range of values in the array using the newly vendored <a href="https://github.com/laurikari/tre/">TRE regex library</a>.</p>
<p>Salvatore wrote more about the AI-assisted development process for the array type in <a href="https://antirez.com/news/164">Redis array type: short story of a long development</a>.</p>
    
    
        <p>Tags: <a href="https://simonwillison.net/tags/salvatore-sanfilippo">salvatore-sanfilippo</a>, <a href="https://simonwillison.net/tags/webassembly">webassembly</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/agentic-engineering">agentic-engineering</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/redis">redis</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/regular-expressions">regular-expressions</a>, <a href="https://simonwillison.net/tags/c">c</a></p>