---
id: inbox_59793496
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tg0me5/grafting_vision_onto_text_models_for_fun_and/"
author: "/u/a_beautiful_rhind"
published_at: 2026-05-17T20:19:56+00:00
fetched_at: 2026-05-18T18:51:02.692113+00:00
content_hash: "4567e329fe499d09f7f66e8e5c09eca3960586746bbd3bc9a40d7075a0a8437b"
lang: en
caption_quality: None
raw: true
topics: []
---

# Grafting vision onto text models for fun and profit.

So as we know.. llama.cpp separates the vision or other multimedia from the main weights. Conversely, trained model capabilities might be removed at release. What if there was a way to put them back? Mistral has now released both pixtral and medium vision encoders. The tokenizers of past models contain the relevant parts. &quot;10&quot;: { &quot;content&quot;: &quot;[IMG]&quot;, &quot;lstrip&quot;: false, &quot;normalized&quot;: false, &quot;rstrip&quot;: false, &quot;single_word&quot;: false, &quot;special&quot;: true }, Let's take Behemoth-X because I rather like that model. --mmproj Pixtral-Large-Instruct-2411-hf.mmproj-f16.gguf \ --no-mmproj-offload \ It clearly sees images.. but something is broken. https://i.ibb.co/3mTZX7Nr/bad-image.png https://i.ibb.co/V0qvvjvm/bad-image2.png The log tells you: [/INST]y'know what??? shut up&lt;/s&gt;[INST][IMG_END][/INST] Guess it wasn't trained on [IMG_END]. That's most unfortunate. But we have the source code and can edit mtmd.cpp } else if (proj == PROJECTOR_TYPE_PIXTRAL) { // https://github.com/huggingface/transformers/blob/1cd110c6cb6a6237614130c470e9a902dbc1a4bd/docs/source/en/model_doc/pixtral.md //img_end = &quot;[IMG_END]&quot;; img_end = &quot;\n&quot;; Alternatively the model can be reconverted to change the offending token to a different ID. Either way, it doesn't lose it's turn anymore. https://i.ibb.co/P7x6z31/good-image2.png https://i.ibb.co/Pn29ML2/good-image.png Is it perfect? No. Might it work better for devstral2 or some other model you want vision for? It's highly likely. 31b gemma contains the ASR parts in the tokenizer... &quot;audio_token&quot;: &quot;&lt;|audio|&gt;&quot;, &quot;backend&quot;: &quot;tokenizers&quot;, &quot;boa_token&quot;: &quot;&lt;|audio&gt;&quot;, &quot;boi_token&quot;: &quot;&lt;|image&gt;&quot;, &quot;bos_token&quot;: &quot;&lt;bos&gt;&quot;, &quot;eoa_token&quot;: &quot;&lt;audio|&gt;&quot;, &quot;eoc_token&quot;: &quot;&lt;channel|&gt;&quot;, &quot;eoi_token&quot;: &quot;&lt;image|&gt;&quot;, &quot;eos_token&quot;: &quot;&lt;eos&gt;&quot;, &quot;eot_token&quot;: &quot;&lt;turn|&gt;&quot;, &#32; submitted by &#32; /u/a_beautiful_rhind [link] &#32; [comments]