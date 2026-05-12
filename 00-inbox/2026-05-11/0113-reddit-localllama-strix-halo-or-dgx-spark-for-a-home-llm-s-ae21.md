---
id: inbox_fff814bb
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1ta7ce9/strix_halo_or_dgx_spark_for_a_home_llm_server/"
author: "/u/Reactor-Licker"
published_at: 2026-05-11T15:51:50+00:00
fetched_at: 2026-05-12T01:13:59.608982+00:00
content_hash: "ae214c2fbe52b533b6c192588f38ed84395812f38c73114580dc836630617536"
lang: en
caption_quality: None
raw: true
topics: []
---

# Strix Halo or DGX Spark for a home LLM server?

I’m currently stuck deciding between AMD Strix Halo (128 GB AMD Ryzen AI Max+ 395 Framework Desktop) and an Nvidia DGX Spark (Asus Ascent GX10) for a home LLM server that can be accessed over the local network with a ChatGPT like interface in a web browser. Keep in mind I’m a noob at this, my only previous experience with local LLMs is using LM Studio on one machine, with no network hosting. The Framework Desktop costs $3,388, while the Asus Ascent GX10 costs $3,500. I’m willing to pay this difference if the GX10 is faster in real world inference speeds. I’m planning to use Q4_K_M or Q6_K quantization to preserve quality without wasting speed and RAM, because I heard those 2 are the sweet spots. I want to run the following models ideally as fast as possible and with long context lengths (128K and above): Gemma 4 31B Gemma 4 26B A4B Qwen 3.6 27B Qwen 3.6 35B A3B GPT OSS 120B I have watched a bunch of DGX Spark reviews but oddly none of them seem to compare its inference speed to Strix Halo. What is the real world performance difference between the two? Does it change when more context is used? My planned use cases are the following: Web researching and fact finding Document / file summarization and fact finding Logical reasoning and problem solving General chat Image recognition Essentially, like a private and controllable version of ChatGPT. A “ChatGPT Lite” so to speak. I understand that these models don’t have the same level of intelligence or capabilities as GPT 5.5, but I want to get as close as I can with this level of hardware without waiting a year for a response from the model. In terms of interface, I’m thinking of using Open WebUI because of its ChatGPT like interface and multi user support to keep the different household members chats separated, but I am open to alternatives. I’m not super sure how to get quality web searching and file reading working. For the engine running the LLM that will hook into Open WebUI, I’m thinking of using LM Studio or llama.cpp. I want to have a GUI to configure model settings like context length, GPU offload, temperature, seed, and things like that without having to mess around with the command line to test a settings change. Finally, I plan to use Ubuntu as the OS. Please let me know any suggestions, improvements, or ideas you have. I’m by no means an expert, this is just what I have come up with on my own. Thanks! &#32; submitted by &#32; /u/Reactor-Licker [link] &#32; [comments]