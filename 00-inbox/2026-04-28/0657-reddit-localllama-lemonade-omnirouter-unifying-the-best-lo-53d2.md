---
id: inbox_1bb29855
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1sy54d1/lemonade_omnirouter_unifying_the_best_local_ai/"
author: "/u/jfowers_amd"
published_at: 2026-04-28T15:43:25+00:00
fetched_at: 2026-04-29T06:57:59.407791+00:00
content_hash: "53d27a044d671c535fc6ff189795fb385cf35a6bba45d858e7487997cb526abd"
lang: en
caption_quality: None
raw: true
topics: []
---

# Lemonade OmniRouter: unifying the best local AI engines for omni-modality

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1sy54d1/lemonade_omnirouter_unifying_the_best_local_ai/"> <img alt="Lemonade OmniRouter: unifying the best local AI engines for omni-modality" src="https://external-preview.redd.it/bWM1Ymc2Y3NieXhnMYt8C7mo9BjJCz9oL63TvAKEUMjlwi1zV3PUzTslmebL.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=967725cd8238002572b6f37d26d48d615a79a721" title="Lemonade OmniRouter: unifying the best local AI engines for omni-modality" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>I’ve always liked how if I ask ChatGPT to make or edit an image, it just does it. Local AI should be this convenient! One install, one endpoint. Ask for an image of a cat and it appears. Ask for a hat on the cat, with a narrated story. Now we can easily build immersive experiences.</p> <p>Lemonade's OmniRouter brings that same pattern to local through built-in tools:</p> <ul> <li>Image generation/ editing through sd.cpp</li> <li>Text-to-speech through kokoros</li> <li>Transcription through whisper.cpp</li> <li>Vision through llama.cpp</li> </ul> <p>Your workflow talks to Lemonade running on your own NPU/GPU through OpenAI-compatible tool calling.</p> <p>How it works:</p> <ol> <li>Lemonade sets up all these local AI engines for your system.</li> <li>Add Lemonade’s tool definitions to your workflows.</li> <li>When your LLM triggers a tool call it gets routed to the corresponding engine (sd.cpp, whisper.cpp, kokoros).</li> <li>Feed the result back into your loop.</li> </ol> <p>That’s it. No custom orchestration layer, no new abstractions to learn. Check it out in <a href="https://github.com/lemonade-sdk/lemonade/blob/main/examples/lemonade_tools.py">this 181-line e2e Python example</a>.</p> <p>We’ve added support for OmniRouter in our reference web ui (also available as a Tauri app), which is what you’re seeing in the video. But I’m much more excited to see what people build on top.</p> <p>I know my next project is going to be some kind of TTRPG-style adventure game. It’s already surprisingly fun to ask OmniRouter to be a dungeon master who illustrates and narrates the story, and I think it can be enhanced quite a bit if I build an app/harness around it.</p> <p>If you find this interesting, please drop us a star and say hi! * GitHub: <a href="https://github.com/lemonade-sdk/lemonade">https://github.com/lemonade-sdk/lemonade</a> * Discord: <a href="https://discord.gg/5xXzkMu8Zk">https://discord.gg/5xXzkMu8Zk</a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/jfowers_amd"> /u/jfowers_amd </a> <br /> <span><a href="https://v.redd.it/se6dt0csbyxg1">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1sy54d1/lemonade_omnirouter_unifying_the_best_local_ai/">[comments]</a></span> </td></tr></table>