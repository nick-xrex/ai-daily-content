---
id: inbox_627f804e
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1szy8y8/my_calculator_is_a_transformer/"
author: "/u/radarsat1"
published_at: 2026-04-30T14:49:18+00:00
fetched_at: 2026-05-01T12:57:17.664879+00:00
content_hash: "a25d44241611bad2180363af4b55a6d2de416f67103c1a2b1de31050e1c09dfd"
lang: en
caption_quality: None
raw: true
topics: []
---

# My calculator is a transformer

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1szy8y8/my_calculator_is_a_transformer/"> <img alt="My calculator is a transformer" src="https://external-preview.redd.it/cz-g2UIhppSCNNKYkic1dzzT9FSuWIa85Ac7PKfwOh0.png?width=320&amp;crop=smart&amp;auto=webp&amp;s=a1c6d814e70eb89928a34029920e24db4a0bae4b" title="My calculator is a transformer" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>I got interested in seeing whether I could &quot;compile&quot; a program into transformer weights, instead of training. I've been working on it for a couple of months now but finally decided to just stop and write it up, so this is a bit of a long post but maybe some of you will find it interesting.</p> <p>Basically I define the residual stream as a set of &quot;registers&quot; and generate the attention weights and MLP functions that execute an RPN interpreter (e.g. <code>2 3 + 2 *</code> should produce <code>10</code>.)</p> <p>For now I settled on distilling the non-linear logic into the MLPs by training, but the attention weights are fully calculated by the compiler. I think it could be possible to calculate the MLP weights eventually too but it probably needs more of an AST behind it.</p> <p>In a way it's a sort of useless exercise (who really needs an RPN interpreter that clocks in at 1.1 GB) but see the last bit for some thoughts about how this might have some application. I did learn to think of transformers and attention a bit differently after working on this, so I hope it's interesting to some people out there.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/radarsat1"> /u/radarsat1 </a> <br /> <span><a href="https://sinclairs.gitlab.io/blog/my-calculator-is-a-transformer/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1szy8y8/my_calculator_is_a_transformer/">[comments]</a></span> </td></tr></table>