---
id: inbox_e4b01359
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_e4b01359]]"
title: "LM Studio / Windows / Vulkan possible to prioritize GPU order?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t975bx/lm_studio_windows_vulkan_possible_to_prioritize/
source: reddit-localllama
published_at: 2026-05-10T13:36:01+00:00
fetched_at: 2026-05-11T02:24:43.299591+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者詢問 LM Studio 在 Vulkan 模式下是否能優先選擇 GPU 使用順序。原本用 CUDA 可按速度優先使用 3090ti > 3060，但混用 NVIDIA 與 AMD GPU（R9700）後，LM Studio Vulkan 模式只能將層分散到各卡，導致整體性能下降，期望有更精細的 GPU 優先級控制機制。"
key_points:
  - "LM Studio Vulkan 模式下缺乏 GPU 優先級控制，僅支持層分散策略"
  - "CUDA 支持按速度優先級分配（3090ti > 3060），Vulkan 無此功能"
  - "混合 GPU 場景（NVIDIA 3090ti/3060 + AMD R9700）總 VRAM 68GB 仍受性能限制"
tags: [lm-studio, vulkan, multi-gpu, gpu-prioritization, cuda]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## LM Studio / Windows / Vulkan possible to prioritize GPU order?

使用者詢問 LM Studio 在 Vulkan 模式下是否能優先選擇 GPU 使用順序。原本用 CUDA 可按速度優先使用 3090ti > 3060，但混用 NVIDIA 與 AMD GPU（R9700）後，LM Studio Vulkan 模式只能將層分散到各卡，導致整體性能下降，期望有更精細的 GPU 優先級控制機制。

### 重點
- LM Studio Vulkan 模式下缺乏 GPU 優先級控制，僅支持層分散策略
- CUDA 支持按速度優先級分配（3090ti > 3060），Vulkan 無此功能
- 混合 GPU 場景（NVIDIA 3090ti/3060 + AMD R9700）總 VRAM 68GB 仍受性能限制

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t975bx/lm_studio_windows_vulkan_possible_to_prioritize/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# LM Studio / Windows / Vulkan possible to prioritize GPU order?

With CUDA you can prioritize GPU usage which worked well with a 3090ti and 3060 12GB. Under 24GB, fastest, under 36GB, slower, &gt;36GB moving some layers to CPU so slowest. I just added a R9700 so while my GPU VRAM has increased greatly to 68GB I need to use Vulkan as I’m mixing green and red. The only option showing is to distribute layers across cards so now everything is a bit slower. It does work, however. Aside from upgrading the 3060 to increase the GPU with slowest speed, is there a way to prioritize GPUs in Vulkan? &#32; submitted by &#32; /u/MarcusAurelius68 [link] &#32; [comments]

</details>