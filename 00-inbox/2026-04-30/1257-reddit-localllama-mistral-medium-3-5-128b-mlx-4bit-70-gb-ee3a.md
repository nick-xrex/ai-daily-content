---
id: inbox_961f1c9d
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t09anw/mistral_medium_35_128b_mlx_4bit_70_gb/"
author: "/u/ex-arman68"
published_at: 2026-04-30T21:15:54+00:00
fetched_at: 2026-05-01T12:57:17.662233+00:00
content_hash: "ee3a646712e0300eab222a7e294e0a5afaac73ae364c2813343573af8c540763"
lang: en
caption_quality: None
raw: true
topics: []
---

# Mistral medium 3.5 128B, MLX 4bit, ~70 GB

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t09anw/mistral_medium_35_128b_mlx_4bit_70_gb/"> <img alt="Mistral medium 3.5 128B, MLX 4bit, ~70 GB" src="https://external-preview.redd.it/s66l-6BlBjHQa3FfpvWdfNprX1CbsTPe5-J06qg7rnI.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=51db278921d9c711f6c893c348b04c54c8371fff" title="Mistral medium 3.5 128B, MLX 4bit, ~70 GB" /> </a> </td><td> <!-- SC_OFF --><div class="md"><blockquote> <p>This model seems utterly broken for now. I do not recommend downloading or using it, unless you are planning to help troubleshoot it. This is not a problem with the conversion, but with the model itself.</p> </blockquote> <p>I converted Mistral medium 3.5 128B to MLX 4bit. Eagle model for speculative decoding is not yet supported by MLX.</p> <p>Vision encoder included (full BF16 unquantized. Thinking mode works (reasoning_effort=&quot;high&quot; gives you the [THINK]...[/THINK] chain), tool calling works, 256K context.</p> <p>There was a bug in mlx-vlm's mistral3 sanitize function: it wasn't stripping the model. prefix from vision tower and projector keys. This caused 438 parameters to be skipped. I patched it locally before converting. Details in the HF readme.</p> <p>I am getting ~5 tok/s on a 96 GB M2 Max. For sampling I recommend using temp 0.7 / top_p 0.95 / top_k 20 in reasoning mode, or temp 0.0–0.7 / top_p 0.8 for quick replies. Mistral recommends leaving repeat penalty disabled, but I am getting too many loops; I am not sure what the best value should be.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/ex-arman68"> /u/ex-arman68 </a> <br /> <span><a href="https://huggingface.co/froggeric/Mistral-Medium-3.5-128B-MLX-4bit">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t09anw/mistral_medium_35_128b_mlx_4bit_70_gb/">[comments]</a></span> </td></tr></table>