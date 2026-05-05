---
id: inbox_fe4c20ed
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t3hokh/llmsearchindex_an_open_source_local_web_search/"
author: "/u/zakerytclarke"
published_at: 2026-05-04T13:26:10+00:00
fetched_at: 2026-05-05T08:19:21.018064+00:00
content_hash: "d1bc608c51ddfef45bd4f00a07e6dbc6439506191f18942a872a92577d0b8895"
lang: en
caption_quality: None
raw: true
topics: []
---

# LLMSearchIndex- an Open Source Local Web Search Library with over 200 million indexed Web Pages for RAG applications

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3hokh/llmsearchindex_an_open_source_local_web_search/"> <img alt="LLMSearchIndex- an Open Source Local Web Search Library with over 200 million indexed Web Pages for RAG applications" src="https://external-preview.redd.it/H1--m0XR8P8B7sdTmFTSumHNkEgu-f8x9F1A9Y7SKH0.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=19154e5ca7928bde5906ad7dc27e4b8bddf7a178" title="LLMSearchIndex- an Open Source Local Web Search Library with over 200 million indexed Web Pages for RAG applications" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>I've been pretty unsatisfied with web search options for local LLM/RAG systems. Most setups either rely on paid APIs like Brave, or meta search scrapers like SearXNG.</p> <p>So I built LLMSearchIndex- a Python library for fully local internet-scale search. It uses a custom trained, highly compressed search index that contains most of the webpages from FineWeb + Wikipedia. The full index is only ~2GB and runs locally on most hardware with pretty fast retrieval speeds.</p> <p>I've built a <a href="https://pypi.org/project/llmsearchindex/">python library</a> to make it easy to retrieve these results for RAG context.</p> <pre><code>from llmsearchindex import LLMIndex index = LLMIndex() results = index.search(&quot;who invented sliced bread?&quot;, top_k=5) </code></pre> <p>You can also check out a demo here: <a href="https://zakerytclarke-llmsearchindex.hf.space/">https://zakerytclarke-llmsearchindex.hf.space/</a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/zakerytclarke"> /u/zakerytclarke </a> <br /> <span><a href="https://github.com/zakerytclarke/llmsearchindex">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3hokh/llmsearchindex_an_open_source_local_web_search/">[comments]</a></span> </td></tr></table>