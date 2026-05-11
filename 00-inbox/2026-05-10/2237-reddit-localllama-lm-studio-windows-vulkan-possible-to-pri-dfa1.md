---
id: inbox_e4b01359
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t975bx/lm_studio_windows_vulkan_possible_to_prioritize/"
author: "/u/MarcusAurelius68"
published_at: 2026-05-10T13:36:01+00:00
fetched_at: 2026-05-10T22:37:14.694750+00:00
content_hash: "dfa100cae62011b424ae972f124c32e6aa11916f4b2a4716db746f5a12e1727a"
lang: en
caption_quality: None
raw: true
topics: []
---

# LM Studio / Windows / Vulkan possible to prioritize GPU order?

With CUDA you can prioritize GPU usage which worked well with a 3090ti and 3060 12GB. Under 24GB, fastest, under 36GB, slower, &gt;36GB moving some layers to CPU so slowest. I just added a R9700 so while my GPU VRAM has increased greatly to 68GB I need to use Vulkan as I’m mixing green and red. The only option showing is to distribute layers across cards so now everything is a bit slower. It does work, however. Aside from upgrading the 3060 to increase the GPU with slowest speed, is there a way to prioritize GPUs in Vulkan? &#32; submitted by &#32; /u/MarcusAurelius68 [link] &#32; [comments]