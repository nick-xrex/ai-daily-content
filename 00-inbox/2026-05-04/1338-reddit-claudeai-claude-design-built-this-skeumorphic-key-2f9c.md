---
id: inbox_c5ce3aba
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t3crw7/claude_design_built_this_skeumorphic_keyboard/"
author: "/u/invocation02"
published_at: 2026-05-04T09:34:56+00:00
fetched_at: 2026-05-04T13:38:39.520194+00:00
content_hash: "2f9cb902612d71458596b4602ca15d2271b137ddeaf8537c491deb9952c791aa"
lang: en
caption_quality: None
raw: true
topics: []
---

# Claude Design built this skeumorphic keyboard simulator website in one session - whatever you type and enter is visible to the public

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1t3crw7/claude_design_built_this_skeumorphic_keyboard/"> <img alt="Claude Design built this skeumorphic keyboard simulator website in one session - whatever you type and enter is visible to the public" src="https://preview.redd.it/juj74ld803zg1.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=857372a2baddecd9634ebf2b8fa6414a3edc2e1f" title="Claude Design built this skeumorphic keyboard simulator website in one session - whatever you type and enter is visible to the public" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>It's a skeuomorphic typing app. What you press on your real keyboard lights up on the rendered one, and pressing enter broadcasts your line into a public transcript everyone can see.</p> <p>Started with a one line prompt: &quot;keyboard recorder with a calculator tape history scrolling above, skeuomorphic. Claude shipped v1 in one pass, but generic.&quot;</p> <p>Next I uploaded a Figma file of the keys I actually wanted. Claude installed fig kiwi (community parser for Figma's binary format), walked all 98 nodes, pulled exact gradients and blurs. CSS recreations kept coming out &quot;ringed&quot; and too sharp. The fix was to port all SVG layers from Figma one by one.</p> <p>For typing logic, the first version used a custom div as input, so Cmd+ArrowLeft and Cmd+Backspace did nothing. The fix was to use a hidden `&lt;input&gt;` underneath the orange display, mirroring its value into the visible text and letting the OS handle every shortcut natively.</p> <p>Backgrounds are real Unsplash photos (marble, walnut, barnwood, slate) fetched through a CORS proxy and served back as cached WebP.</p> <p>Live here: <a href="http://asdf.app.teenyapp.com">asdf.app.teenyapp.com</a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/invocation02"> /u/invocation02 </a> <br /> <span><a href="https://i.redd.it/juj74ld803zg1.png">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3crw7/claude_design_built_this_skeumorphic_keyboard/">[comments]</a></span> </td></tr></table>