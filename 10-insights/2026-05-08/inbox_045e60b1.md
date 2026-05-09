---
id: inbox_045e60b1
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0151-reddit-localllama-local-llm-for-electronics-design-work-62d4]]"
title: "Local LLM for electronics design work?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t7c3p6/local_llm_for_electronics_design_work/
source: reddit-localllama
published_at: 2026-05-08T15:58:08+00:00
fetched_at: 2026-05-09T02:26:09.337699+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用户询问是否存在针对电子设计工作优化的本地LLM。指出Qwen3.6虽能把握大框架，但在细节和SPICE netlists理解上不足，故障排查能力弱于云模型。用户约束为CPU-only设置、最大支持27B参数模型。内容为需求提问，无实质发现。"
key_points:
  - "Qwen3.6在SPICE netlists理解和circuits故障排查上弱于云端模型"
  - "本地LLM在电子设计领域缺乏专门优化版本"
  - "用户硬件约束：CPU-only，最大27B模型"
tags: [electronics-design, local-llm, spice-simulation, specialized-models]
topics: []
importance: 1
novelty: 1
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Local LLM for electronics design work?

用户询问是否存在针对电子设计工作优化的本地LLM。指出Qwen3.6虽能把握大框架，但在细节和SPICE netlists理解上不足，故障排查能力弱于云模型。用户约束为CPU-only设置、最大支持27B参数模型。内容为需求提问，无实质发现。

### 重點
- Qwen3.6在SPICE netlists理解和circuits故障排查上弱于云端模型
- 本地LLM在电子设计领域缺乏专门优化版本
- 用户硬件约束：CPU-only，最大27B模型

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t7c3p6/local_llm_for_electronics_design_work/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Another hobby is working on electronics projects ranging from low-voltage control and signal processing to HV tube amp circuits. I design and simulate in LTspice before prototyping. I often use the cloud models for design help; they're great at architecture and topology, but when you get down to the details they start to lose the thread, and in the worst case, start hallucinating and giving patently bad guidance. Qwen3.6 is similar; t gets the big picture fine, but gets lost in the details, *especially* when troubleshooting. It also doesn't understand SPICE netlists as well as the cloud models (obviously). Are there any local LLMs that are optimized for electronics work? My crappy CPU-only rig works for models up to about 27B dense. (Sample prompt for a HV LFO: &quot;Design a wien bridge oscillator circuit using a differential amp built from a pair of DN2540 mosfets and a CCS tail, and a VTL5C2 vactrol as the AGC control element. Power rails are 300V, 0V, -72V. Target frequency is 4Hz. Target output is 20Vpp, driving a 1M load. Start by describing the architecture.&quot;) &#32; submitted by &#32; /u/deafenme [link] &#32; [comments]

</details>