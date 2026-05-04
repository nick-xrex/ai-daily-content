---
id: inbox_5f1315dc
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t33mlw/second_thoughts_been_playing_with_adding_a_small/"
author: "/u/bigattichouse"
published_at: 2026-05-04T01:26:59+00:00
fetched_at: 2026-05-04T13:38:38.105553+00:00
content_hash: "99ddd64d65b2fa56f8cd368fb65c1c7d7924070c49c7a690853436869d7daf03"
lang: en
caption_quality: None
raw: true
topics: []
---

# "Second Thoughts" Been playing with adding a small transformer that reads output near the end of generation, and feeds it back near the top as a refinement loop. A quick test of 1.7B model showed drastic improvement in focused tasks (like coding)

<!-- SC_OFF --><div class="md"><p>A 1.7B model can actually turn out some code, so I'm running the training for a 9B model, then will re-run HumanEval (a full one this time). I've shown most of my homework in the article, but will be posting to github after I clean things up.</p> <p>It was inspired by Repeat Yourself's <a href="https://dnhkng.github.io/posts/rys/"><strong>dnhkng.github.io/posts/rys/</strong></a> neuroanatomy findings... this gave me a start and end point to attach my &quot;reverse LLM&quot; side car model (so it reads from the end, and then injects its output back at the top - in a loop), in this case focusing on syntax - drastically improving a very tiny model.</p> <p>I'll also go back and run the full HumanEval dataset on both, instead of just the first 20.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/bigattichouse"> /u/bigattichouse </a> <br /> <span><a href="https://bigattichouse.medium.com/second-thoughts-improving-small-llms-with-bidirectional-refinement-loops-part-1-fa5ab51af656?sk=907cce272a3aed0eb3f1e3a0669a3964">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t33mlw/second_thoughts_been_playing_with_adding_a_small/">[comments]</a></span>