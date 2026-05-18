---
id: inbox_f1745ee1
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_f1745ee1]]"
title: "Scenema Audio: Zero-shot expressive voice cloning and speech generation"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tcwqdd/scenema_audio_zeroshot_expressive_voice_cloning/
source: reddit-localllama
published_at: 2026-05-14T12:29:53+00:00
fetched_at: 2026-05-18T03:42:53.795988+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Scenema Audio 發布開源的零投射語音克隆和表現型語音生成模型，核心創新是將情感表現與聲音身份解耦，讓任何聲音可表現任何情感，即使該聲音從未錄製過該情感狀態。採用擴散模型架構（8 步去雜音，從原始 50 步優化），比自迴歸 TTS 聽起來更自然尤其對情感表現；Docker REST API 自動管理 VRAM（支援 16/24/48GB 配置），提供網頁版和本地部署。提示詞工程至關重要，需詳細的劇場式描述和動作標籤；複雜詞彙用音標拼寫；避免英文負面提示，改用原始中文負面提示效果更好。發布完整開源代碼（MIT 授權），計劃推出 ComfyUI native 支援。"
key_points:
  - "擴散型 TTS 的自然度優於自迴歸模型，尤其在情感表現；但代價是需要挑選多輪生成結果並做後期編輯"
  - "提示詞敏感度高，需要「特定、劇場式描述 + 動作標籤」而非泛用描述；複雜詞用音標拼寫（如 Tchaikovsky → Chai-koff-skee）"
  - "Docker 部署生產級，單卡序列執行 4B 擴散 + 3.5B TTS + 14B 動畫模型，無依賴地獄問題"
tags: [text-to-speech, voice-cloning, diffusion-model, open-source, prompt-engineering]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Scenema Audio: Zero-shot expressive voice cloning and speech generation

Scenema Audio 發布開源的零投射語音克隆和表現型語音生成模型，核心創新是將情感表現與聲音身份解耦，讓任何聲音可表現任何情感，即使該聲音從未錄製過該情感狀態。採用擴散模型架構（8 步去雜音，從原始 50 步優化），比自迴歸 TTS 聽起來更自然尤其對情感表現；Docker REST API 自動管理 VRAM（支援 16/24/48GB 配置），提供網頁版和本地部署。提示詞工程至關重要，需詳細的劇場式描述和動作標籤；複雜詞彙用音標拼寫；避免英文負面提示，改用原始中文負面提示效果更好。發布完整開源代碼（MIT 授權），計劃推出 ComfyUI native 支援。

### 重點
- 擴散型 TTS 的自然度優於自迴歸模型，尤其在情感表現；但代價是需要挑選多輪生成結果並做後期編輯
- 提示詞敏感度高，需要「特定、劇場式描述 + 動作標籤」而非泛用描述；複雜詞用音標拼寫（如 Tchaikovsky → Chai-koff-skee）
- Docker 部署生產級，單卡序列執行 4B 擴散 + 3.5B TTS + 14B 動畫模型，無依賴地獄問題

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tcwqdd/scenema_audio_zeroshot_expressive_voice_cloning/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Scenema Audio: Zero-shot expressive voice cloning and speech generation

We've been building Scenema Audio as part of our video production platform at scenema.ai, and we're releasing the model weights and inference code. The core idea: emotional performance and voice identity are independent. You describe how the speech should be performed (rage, grief, excitement, a child's wonder), and optionally provide reference audio for voice identity. The reference provides the &quot;who.&quot; The prompt provides the &quot;how.&quot; Any voice can perform any emotion, even if that voice has never been recorded in that emotional state. Limitations (and why we still use it) This is a diffusion model, not a traditional TTS pipeline. Common issues include repetition and gibberish on some seeds. Different seeds give different results, and you will not get a perfect output with 0% error rate. This model is meant for a post-editing workflow: generate, pick the best take, trim if needed. Same way you'd work with any generative model. That said, we keep coming back to Scenema Audio over even Gemini 3.1 Flash TTS, which is already more controllable than most TTS systems out there. The reason is simple: the output just sounds more natural and less robotic. There's a quality to diffusion-generated speech that autoregressive TTS doesn't quite match, especially for emotional delivery. Audio-first video generation As this video points out, generating audio first and then using it to drive video generation is a powerful workflow. That's actually how we've used Scenema Audio in some cases. Generate the voice performance, then feed it into an A2V pipeline (LTX 2.3, Wan 2.6, Seedance 2.0, etc.) to generate video that matches the speech. Here's an example of that workflow in action. On distillation and speed A few people have asked this. Our bottleneck is not denoising steps. The diffusion pass is a small fraction of total generation time. The real costs are elsewhere in the pipeline. We're already at 8 steps (down from 50 in the base model), and that's the sweet spot where quality holds. Prompting matters This model is sensitive to prompting, the same way LTX 2.3 is for video. A generic voice description gives you generic output. A specific, theatrical description with action tags gives you a performance. There's also a pace parameter that controls how much time the model gets per word. Takes some experimentation to find what works for your use case, but once you do, you can generate hours of audio with minimal quality loss. Complex words and proper nouns benefit from phonetic spelling. Unlike traditional TTS, it doesn't have a phoneme-to-audio pipeline or a pronunciation dictionary. If it garbles &quot;Tchaikovsky,&quot; you would spell it &quot;Chai-koff-skee&quot; or whatever makes sense to you. Docker REST API with automatic VRAM management We ship this as a Docker container with a REST API. Same setup we use in production on scenema.ai. The service auto-detects your GPU and picks the right configuration: VRAM Audio Model Gemma Notes 16 GB INT8 (4.9 GB) CPU streaming Needs 32 GB system RAM 24 GB INT8 (4.9 GB) NF4 on GPU Default config 48 GB bf16 (9.8 GB) bf16 on GPU Best quality We went with Docker because that's how we serve it. No dependency hell, no conda environments. We built it for production deployment. ComfyUI Native ComfyUI node support is planned. We're hoping to release it in the coming weeks, unless someone from the community beats us to it. In the meantime, the REST API is straightforward to call from a custom node since it's just a local HTTP service. Links All demos + article: scenema.ai/audio Model weights: huggingface.co/ScenemaAI/scenema-audio Code + setup: github.com/ScenemaAI/scenema-audio YouTube demo: youtu.be/VnEQ_ImOaAc This is fully open source. The model weights derive from the LTX-2 Community License but all inference and pipeline code is MIT. How to Try Scenema Audio You can clone the repo and run docker compose up locally or Go to Scenema and start a conversation to create a voiceover. You will be able to try voice design for free, iterate on your prompts, tune pacing, etc. &#32; submitted by &#32; /u/a__side_of_fries [link] &#32; [comments]

</details>