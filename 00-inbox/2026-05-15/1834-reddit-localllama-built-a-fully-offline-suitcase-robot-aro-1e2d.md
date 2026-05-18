---
id: inbox_cef06f38
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tdz5gr/built_a_fully_offline_suitcase_robot_around_a/"
author: "/u/CreativelyBankrupt"
published_at: 2026-05-15T15:09:18+00:00
fetched_at: 2026-05-15T18:34:22.418895+00:00
content_hash: "1e2dcee5c763add4a5a54642611af0266075b8af424294f78bcfbc20942be61c"
lang: en
caption_quality: None
raw: true
topics: []
---

# Built a fully offline suitcase robot around a Jetson Orin NX SUPER 16GB. Gemma 4 E4B, ~200ms cached TTFT, 30+ sensors, no WiFi/BT/cellular. He has opinions.

Sparky runs entirely on the Jetson. Gemma 4 E4B at Q4_K_M via llama.cpp with q8_0 KV cache and flash attention. 12K context, native system role, sampler defaults from the model card. Cached TTFT around 200ms, sustained 14-15 tok/s. SenseVoiceSmall for STT, Piper for TTS with 43Hz mouth sync, PixiJS face on the lid display. Vision and OCR are native to Gemma 4 now so the BLIP subprocess is gone. 30+ sensors fold into the prompt as natural language every turn. One of the biggest wins was prompt structure for cache stability. Persona and tools at the top, history in the middle, volatile sensor and vision data at the end of the latest user turn. Moving dynamic context out of the system block dropped cached TTFT from multi-second to ~200ms. Configurable entirely on-device via a button row, a joystick, and an analog encoder knob. No network interface at all. Curious if anyone else is running E4B on Orin-class hardware. I'd love to compare tok/s and how you're handling sensor or tool context without blowing your prefix cache. &#32; submitted by &#32; /u/CreativelyBankrupt [link] &#32; [comments]