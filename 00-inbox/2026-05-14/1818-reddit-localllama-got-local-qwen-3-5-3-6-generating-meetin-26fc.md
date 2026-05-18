---
id: inbox_51094b28
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tcyiid/got_local_qwen_3536_generating_meeting_summaries/"
author: "/u/julp"
published_at: 2026-05-14T13:39:24+00:00
fetched_at: 2026-05-14T18:18:30.440054+00:00
content_hash: "26fc64b68a94ac7da43e7c0375a07747cb6545e447bf31bb66a0d4e7a9c5d82e"
lang: en
caption_quality: None
raw: true
topics: []
---

# Got local Qwen 3.5/3.6 generating meeting summaries entirely offline on an M4 Max. Demo with Wi-Fi off. This is the future.

I'm the founder behind Hedy, an AI meeting app. I'm a huge supporter of Local AI, and we've been working on making it &quot;consumer friendly&quot;. Speech recognition in Hedy has always run on-device (whisper.cpp and now also parakeet). What just shipped is that the rest of the AI pipeline (summaries, detailed notes, chat with the meeting, live coaching) can now run on-device too using llama.cpp. Wi-Fi off, nothing leaves the laptop. Video above shows the full flow. A few technical specifics: Models supported out of the box. Qwen 3.6, Qwen 3.5, and Gemma 4 families. Range goes from 2B at the low end (works on newer iPhones) through 9B Qwen 3.5 as the sweet spot for most laptops, up to the newest Qwen 3.6 at 27B and 35B for users with more VRAM. Multiple quantization levels per model. On the 9B Qwen for example, you can pick between Q4 and Q8 depending on memory headroom. Bring your own model. You can download any compatible GGUF model from Hugging Face and load it into Hedy. Not restricted to the curated list. This was a deliberate call. The local AI space moves fast and we don't want users stuck waiting for us to update the bundled options. Acceleration. Metal on Apple Silicon, Vulkan on Windows GPUs, CPU fallback when needed. Mac unified memory means total system RAM is the constraint. Windows is VRAM-bound and the picker tells you when layers will spill to CPU. The app surfaces fit. Before you download a model, the picker tells you whether it'll be a great fit, a tight fit, or won't fit your hardware. It also shows current memory footprint so you know what headroom you have. No silent OOMs. Honest tradeoffs: Cloud is still faster and higher quality for many use cases. Local is opt-in. The 27B+ parameter models roughly match the quality of our cloud models. No silent cloud fallback. If local fails, you see an error. That was a deliberate call. Mobile is restricted to the smallest models (iPhone 15 Pro and later, plus M-series iPads). Older devices don't see the toggle. Android and Web are on the roadmap but not ready. Hardware variation on Android is too much to deliver a consistent experience today. Automatic Suggestions are heavy (since it runs inference very frequently during the meeting). The app prompts you to disable them during local sessions. On the demo specifically: That was an M4 Max running Qwen 3.5 4B (needed to prioritize speed for the demo). The summary in the video took about 15 seconds for a ~10-minute meeting transcript. Your mileage will vary by model size and hardware. Happy to answer questions about model selection, the BYO setup, integration challenges, or anything else technical. Staying in the thread for a few hours. &#32; submitted by &#32; /u/julp [link] &#32; [comments]