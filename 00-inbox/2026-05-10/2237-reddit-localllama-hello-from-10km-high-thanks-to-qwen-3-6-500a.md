---
id: inbox_f77d4f33
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t92hff/hello_from_10km_high_thanks_to_qwen_36_35b_a3b/"
author: "/u/Qwen30bEnjoyer"
published_at: 2026-05-10T09:43:47+00:00
fetched_at: 2026-05-10T22:37:14.049735+00:00
content_hash: "500a29ba94ba80033c6a540e7c4139b8d46c2be5909507a148e9bc595a59108e"
lang: en
caption_quality: None
raw: true
topics: []
---

# Hello from 10KM high! - Thanks to Qwen 3.6 35b a3b!

Typing this on a cramped flight, but I was having issues connecting to the plane's wifi on my ubuntu laptop, when it was effortless on my phone. The issue I was having was the Laptop WiFi connected to the plane wifi network, but captive portal wouldn't load. Turns out systemd-resolved was using Docker's DNS instead of the network gateway. Luckily I brought Qwen with me, the agent found a nmcli fix in seconds, and the portal loaded soon after! Could this have been avoided by me somehow not fucking it up in the first place? Probably, but ignore my incompetence for now, I'm not a super technical linux guy. Anyways I'm quite thankful, this would have been a bit of a boring 5 hr flight otherwise. Cheers to the Qwen team from up high! :) EDIT: I forget you nerds like specs! Framework 16 7840hs with 96gb RAM and a 780m iGPU. Model used was qwen/Qwen-3.6-35b-a3b-Q6_k. I think I was running about 20TPS TG, but I'll report back on battery vs. plugged in TPS TG and PP with llama-bench when I land. Running vulkan llama.cpp runtime in LMStudio since I'm a baby that likes GUIs, and bear in mind the iGPU can get a max of 50% RAM allocated to it, and I don't think there is a stable ROCM path at the moment. &#32; submitted by &#32; /u/Qwen30bEnjoyer [link] &#32; [comments]