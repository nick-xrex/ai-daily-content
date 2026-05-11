---
id: inbox_f77d4f33
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_f77d4f33]]"
title: "Hello from 10KM high! - Thanks to Qwen 3.6 35b a3b!"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t92hff/hello_from_10km_high_thanks_to_qwen_36_35b_a3b/
source: reddit-localllama
published_at: 2026-05-10T09:43:47+00:00
fetched_at: 2026-05-11T02:21:09.102399+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者在飛行中遭遇 Ubuntu 網路問題（systemd-resolved 誤用 Docker DNS），透過本地執行的 Qwen 3.6 35B a3b 模型（Framework 16，iGPU，~20 TPS）快速找到 nmcli 修復方案。該案例展示消費級筆電上的本地 LLM agent 在實際技術問題診斷中的實用價值，並驗證在隔離網路環境進行開發工作的可行性。"
key_points:
  - "Qwen 3.6 35B a3b 在 Framework 16 iGPU 上達 ~20 TPS (llama.cpp Vulkan 運行)"
  - "本地 agent 在無網際網路環境下成功診斷並解決 DNS 路由問題"
  - "消費級筆電（7840HS, 96GB RAM）可作為獨立開發環境運行大型量化模型"
tags: [qwen, local-agent, framework-16, gpu-inference]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hello from 10KM high! - Thanks to Qwen 3.6 35b a3b!

使用者在飛行中遭遇 Ubuntu 網路問題（systemd-resolved 誤用 Docker DNS），透過本地執行的 Qwen 3.6 35B a3b 模型（Framework 16，iGPU，~20 TPS）快速找到 nmcli 修復方案。該案例展示消費級筆電上的本地 LLM agent 在實際技術問題診斷中的實用價值，並驗證在隔離網路環境進行開發工作的可行性。

### 重點
- Qwen 3.6 35B a3b 在 Framework 16 iGPU 上達 ~20 TPS (llama.cpp Vulkan 運行)
- 本地 agent 在無網際網路環境下成功診斷並解決 DNS 路由問題
- 消費級筆電（7840HS, 96GB RAM）可作為獨立開發環境運行大型量化模型

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t92hff/hello_from_10km_high_thanks_to_qwen_36_35b_a3b/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Hello from 10KM high! - Thanks to Qwen 3.6 35b a3b!

Typing this on a cramped flight, but I was having issues connecting to the plane's wifi on my ubuntu laptop, when it was effortless on my phone. The issue I was having was the Laptop WiFi connected to the plane wifi network, but captive portal wouldn't load. Turns out systemd-resolved was using Docker's DNS instead of the network gateway. Luckily I brought Qwen with me, the agent found a nmcli fix in seconds, and the portal loaded soon after! Could this have been avoided by me somehow not fucking it up in the first place? Probably, but ignore my incompetence for now, I'm not a super technical linux guy. Anyways I'm quite thankful, this would have been a bit of a boring 5 hr flight otherwise. Cheers to the Qwen team from up high! :) EDIT: I forget you nerds like specs! Framework 16 7840hs with 96gb RAM and a 780m iGPU. Model used was qwen/Qwen-3.6-35b-a3b-Q6_k. I think I was running about 20TPS TG, but I'll report back on battery vs. plugged in TPS TG and PP with llama-bench when I land. Running vulkan llama.cpp runtime in LMStudio since I'm a baby that likes GUIs, and bear in mind the iGPU can get a max of 50% RAM allocated to it, and I don't think there is a stable ROCM path at the moment. &#32; submitted by &#32; /u/Qwen30bEnjoyer [link] &#32; [comments]

</details>