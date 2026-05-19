---
id: inbox_e478eeb0
date: 2026-05-18
source_ref: "[[00-inbox/.../inbox_e478eeb0]]"
title: "Benchmarked Kokoro 82M vs Supertonic 3 TTS on CPU"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tgnxnm/benchmarked_kokoro_82m_vs_supertonic_3_tts_on_cpu/
source: reddit-localllama
published_at: 2026-05-18T14:14:04+00:00
fetched_at: 2026-05-19T02:36:18.276913+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "CPU 上兩款 TTS 模型深度對比（120 次運行）：Supertonic 3 流匹配式、Kokoro 82M 擴散式。Supertonic 2-step 最快（6.1x realtime, RTF 0.165）但音質粗糙；5-step 達平衡（3.2x realtime）；Kokoro PyTorch 2.1x realtime、質量最佳（TTS Arena #1）但固定開銷大。實務建議：追求人類感音質選 Kokoro，低延遲助手選 Supertonic 5-step，演示選 2-step。"
key_points:
  - "Supertonic 2-step: 6.1x realtime 但音質粗糙；5-step: 3.2x realtime 質量可用"
  - "Kokoro 82M PyTorch: 2.1x realtime，質量最佳（TTS Arena #1），固定開銷大"
  - "固定開銷差異：Supertonic 短文本 RTF 0.30 → 中等 0.13；Kokoro 較平穩"
tags: [tts, kokoro, supertonic, cpu-inference, benchmarking]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Benchmarked Kokoro 82M vs Supertonic 3 TTS on CPU

CPU 上兩款 TTS 模型深度對比（120 次運行）：Supertonic 3 流匹配式、Kokoro 82M 擴散式。Supertonic 2-step 最快（6.1x realtime, RTF 0.165）但音質粗糙；5-step 達平衡（3.2x realtime）；Kokoro PyTorch 2.1x realtime、質量最佳（TTS Arena #1）但固定開銷大。實務建議：追求人類感音質選 Kokoro，低延遲助手選 Supertonic 5-step，演示選 2-step。

### 重點
- Supertonic 2-step: 6.1x realtime 但音質粗糙；5-step: 3.2x realtime 質量可用
- Kokoro 82M PyTorch: 2.1x realtime，質量最佳（TTS Arena #1），固定開銷大
- 固定開銷差異：Supertonic 短文本 RTF 0.30 → 中等 0.13；Kokoro 較平穩

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tgnxnm/benchmarked_kokoro_82m_vs_supertonic_3_tts_on_cpu/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Benchmarked Kokoro 82M vs Supertonic 3 TTS on CPU

Wanted a real head to head on the two TTS models that actually run well on CPU. Couldn't find one with proper numbers, so I ran one. Posting because the result was not what I expected going in. Quick context for anyone who hasn't seen Supertonic 3 yet: it's a flow-matching TTS where you can dial down inference steps to trade quality for speed. Default is 5 steps, &quot;speed mode&quot; is 2. Kokoro 82M everyone here knows by now. Hardware: AMD EPYC 7763, 4 vCPUs, 16GB RAM, no GPU. Roughly comparable to a Ryzen 5600 or a decent N100 box. Setup: 6 text lengths from 12 chars to 1712 chars, 5 runs each, 120 timed runs total. CUDA explicitly disabled. Warmup run discarded. Mean RTF (lower is faster): Supertonic 3, 2 steps: 0.165 (6.1x realtime) Supertonic 3, 5 steps: 0.313 (3.2x realtime) Kokoro 82M PyTorch: 0.469 (2.1x realtime) Kokoro 82M ONNX: 0.509 (2.0x realtime) Wall-clock latency on the medium text (196 chars, about 13 seconds of audio): Supertonic 2-step: 1.82s Supertonic 5-step: 3.67s Kokoro PyTorch: 5.62s Kokoro ONNX: 5.51s Long and Extended text details in the Github Repo below. Throughput in chars per second at steady state: Supertonic 2-step gets to ~111, Supertonic 5-step ~55, Kokoro hovers around 33 to 36 regardless of backend. The quality side, which actually flips the ranking: Supertonic at 2 steps is fast, but the audio is rough. Words slur, prosody is mechanical, not something I'd ship. At 5 steps it cleans up a lot and is genuinely usable. Kokoro at either backend still produces the most natural speech of anything I've tested in this size class. It's #1 on the TTS Arena leaderboard for a reason. So the practical ranking is more like: Want it to sound like a human → Kokoro, accept the slower speed Want low latency for an assistant/chatbot → Supertonic 5-step is the sweet spot Supertonic 2-step → demos and prototyping, that's it Two things that surprised me: Kokoro ONNX was slower than PyTorch on this CPU. I expected the opposite. ONNX wins on the longer texts but loses on tiny ones because of higher fixed overhead. Worth retesting on Intel hardware to see if it's an AMD thing. Supertonic has way more fixed per-call overhead than Kokoro. RTF on tiny text is 0.30, on medium it drops to 0.13. Kokoro is much flatter across lengths. So if your workload is lots of short utterances, the gap between them narrows. Detailed write up and Github Repo with all 24 audio samples, and the benchmarks are mentioned in comments below 👇 This evaluation of both TTS models was performed using Neo AI Engineer that built the eval harness, handled model runtime issues, and consolidated results. I reviewed everything manually. If anyone has an N100 or a Pi 5 lying around and runs this, I'd love to see the numbers. That's the tier I actually want to deploy on. &#32; submitted by &#32; /u/gvij [link] &#32; [comments]

</details>