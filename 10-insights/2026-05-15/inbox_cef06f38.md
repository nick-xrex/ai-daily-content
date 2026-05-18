---
id: inbox_cef06f38
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_cef06f38]]"
title: "Built a fully offline suitcase robot around a Jetson Orin NX SUPER 16GB. Gemma 4 E4B, ~200ms cached TTFT, 30+ sensors, no WiFi/BT/cellular. He has opinions."
url: https://www.reddit.com/r/LocalLLaMA/comments/1tdz5gr/built_a_fully_offline_suitcase_robot_around_a/
source: reddit-localllama
published_at: 2026-05-15T15:09:18+00:00
fetched_at: 2026-05-18T03:54:50.839878+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者在 NVIDIA Jetson Orin NX SUPER 16GB 邊緣設備上構建了一個名為 Sparky 的完全離線智能機器人。該機器人運行量化版本的 Gemma 4 E4B（使用 Q4_K_M 量化、q8_0 KV 快取和 flash attention），實現了約 200ms 的快取加載時間和 14-15 token/秒的持續吞吐量。系統集成了 SenseVoiceSmall 語音識別、Piper 語音合成（43Hz 同步率）、PixiJS 蓋子顯示、30+ 感測器和 Gemma 4 原生的視覺與 OCR 能力。最核心的優化洞察是提示結構設計：將動態資料（感測器讀數、視覺輸入）放在提示的末尾而非系統提示區塊，使得快取加載時間從多秒大幅下降至 200ms。該機器人完全離線運行，無任何網絡、藍牙或蜂窩連接，所有配置均透過物理按鈕、搖桿和旋轉編碼器完成。"
key_points:
  - "Gemma 4 E4B 邊緣推理：Jetson Orin NX SUPER 上 200ms 快取 TTFT、14-15 tok/s 吞吐、12K context"
  - "提示結構優化技巧：動態內容（感測器、視覺）置於末尾而非系統塊，KV 快取穩定性提升 10 倍（多秒 → 200ms）"
  - "完整離線智能體：無網絡連接、30+ 感測器、原生 OCR/Vision、物理按鈕配置"
tags: [edge-ai, gemma, jetson, llm-optimization, prompt-engineering]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Built a fully offline suitcase robot around a Jetson Orin NX SUPER 16GB. Gemma 4 E4B, ~200ms cached TTFT, 30+ sensors, no WiFi/BT/cellular. He has opinions.

開發者在 NVIDIA Jetson Orin NX SUPER 16GB 邊緣設備上構建了一個名為 Sparky 的完全離線智能機器人。該機器人運行量化版本的 Gemma 4 E4B（使用 Q4_K_M 量化、q8_0 KV 快取和 flash attention），實現了約 200ms 的快取加載時間和 14-15 token/秒的持續吞吐量。系統集成了 SenseVoiceSmall 語音識別、Piper 語音合成（43Hz 同步率）、PixiJS 蓋子顯示、30+ 感測器和 Gemma 4 原生的視覺與 OCR 能力。最核心的優化洞察是提示結構設計：將動態資料（感測器讀數、視覺輸入）放在提示的末尾而非系統提示區塊，使得快取加載時間從多秒大幅下降至 200ms。該機器人完全離線運行，無任何網絡、藍牙或蜂窩連接，所有配置均透過物理按鈕、搖桿和旋轉編碼器完成。

### 重點
- Gemma 4 E4B 邊緣推理：Jetson Orin NX SUPER 上 200ms 快取 TTFT、14-15 tok/s 吞吐、12K context
- 提示結構優化技巧：動態內容（感測器、視覺）置於末尾而非系統塊，KV 快取穩定性提升 10 倍（多秒 → 200ms）
- 完整離線智能體：無網絡連接、30+ 感測器、原生 OCR/Vision、物理按鈕配置

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tdz5gr/built_a_fully_offline_suitcase_robot_around_a/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Built a fully offline suitcase robot around a Jetson Orin NX SUPER 16GB. Gemma 4 E4B, ~200ms cached TTFT, 30+ sensors, no WiFi/BT/cellular. He has opinions.

Sparky runs entirely on the Jetson. Gemma 4 E4B at Q4_K_M via llama.cpp with q8_0 KV cache and flash attention. 12K context, native system role, sampler defaults from the model card. Cached TTFT around 200ms, sustained 14-15 tok/s. SenseVoiceSmall for STT, Piper for TTS with 43Hz mouth sync, PixiJS face on the lid display. Vision and OCR are native to Gemma 4 now so the BLIP subprocess is gone. 30+ sensors fold into the prompt as natural language every turn. One of the biggest wins was prompt structure for cache stability. Persona and tools at the top, history in the middle, volatile sensor and vision data at the end of the latest user turn. Moving dynamic context out of the system block dropped cached TTFT from multi-second to ~200ms. Configurable entirely on-device via a button row, a joystick, and an analog encoder knob. No network interface at all. Curious if anyone else is running E4B on Orin-class hardware. I'd love to compare tok/s and how you're handling sensor or tool context without blowing your prefix cache. &#32; submitted by &#32; /u/CreativelyBankrupt [link] &#32; [comments]

</details>