---
id: inbox_23f14daf
date: 2026-05-03
source_ref: "[[00-inbox/.../inbox_23f14daf]]"
title: "Built a Voice Agents from Scratch GitHub tutorial: mic &gt; Whisper &gt; local LLM (GGUF) &gt; Kokoro &gt; speaker, fully local, no API keys"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t2pisc/built_a_voice_agents_from_scratch_github_tutorial/
source: reddit-localllama
published_at: 2026-05-03T16:06:28+00:00
fetched_at: 2026-05-04T14:27:18.238662+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者分享「voice-agents-from-scratch」完整教程專案，以 9 章漸進式結構循序漸進教授本地語音代理架構：麥克風 → Whisper STT → 本地 GGUF LLM (llama.cpp) → Kokoro TTS → 揚聲器。核心創新是實時流式設計——不等待 LLM 完整回應即開始 TTS，營造自然對話感而非有聲聊天機器人。每章配套可運行腳本、CODE.md 說明與共享庫展示元件組合；內容涵蓋音頻 I/O、STT、TTS、完整語音迴路、實時系統、工具整合、人格化、部署（規劃採用 modal.com）。作者指出 Node.js 生態未臻成熟（缺乏 Whisper 和音頻處理方案），故採 Python；強調本地運行優勢在於延遲根源可視化（預熱、首音頻延遲、串流塊大小）不再是黑箱。"
key_points:
  - "流式優於等待：邊生成邊播放而非等待完整回應，關鍵差異在於用戶感知的自然對話度"
  - "九章結構化教程：音頻 I/O、STT、TTS、完整迴路、實時系統、工具、個性化、部署，每章皆有可運行程式碼與詳細說明"
  - "本地執行的透明度優勢：預熱時間、首字延遲、串流塊大小等實時可測可優化，而非 API 調用的不可見黑箱"
tags: [voice-agent, real-time-streaming, local-llm, system-architecture, tutorial]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Built a Voice Agents from Scratch GitHub tutorial: mic > Whisper > local LLM (GGUF) > Kokoro > speaker, fully local, no API keys

開發者分享「voice-agents-from-scratch」完整教程專案，以 9 章漸進式結構循序漸進教授本地語音代理架構：麥克風 → Whisper STT → 本地 GGUF LLM (llama.cpp) → Kokoro TTS → 揚聲器。核心創新是實時流式設計——不等待 LLM 完整回應即開始 TTS，營造自然對話感而非有聲聊天機器人。每章配套可運行腳本、CODE.md 說明與共享庫展示元件組合；內容涵蓋音頻 I/O、STT、TTS、完整語音迴路、實時系統、工具整合、人格化、部署（規劃採用 modal.com）。作者指出 Node.js 生態未臻成熟（缺乏 Whisper 和音頻處理方案），故採 Python；強調本地運行優勢在於延遲根源可視化（預熱、首音頻延遲、串流塊大小）不再是黑箱。

### 重點
- 流式優於等待：邊生成邊播放而非等待完整回應，關鍵差異在於用戶感知的自然對話度
- 九章結構化教程：音頻 I/O、STT、TTS、完整迴路、實時系統、工具、個性化、部署，每章皆有可運行程式碼與詳細說明
- 本地執行的透明度優勢：預熱時間、首字延遲、串流塊大小等實時可測可優化，而非 API 調用的不可見黑箱

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t2pisc/built_a_voice_agents_from_scratch_github_tutorial/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Built a Voice Agents from Scratch GitHub tutorial: mic > Whisper > local LLM (GGUF) > Kokoro > speaker, fully local, no API keys

<!-- SC_OFF --><div class="md"><p>Been building this for a while and finally cleaned it up enough to share.</p> <p><strong>voice-agents-from-scratch</strong> is a numbered, chapter-by-chapter repo that walks the full real-time pipeline:</p> <ul> <li>Microphone capture</li> <li>Whisper for STT</li> <li>Local GGUF LLM (via llama.cpp)</li> <li>Kokoro for TTS</li> <li>Speaker output</li> </ul> <p>Everything streams - you don't wait for the full LLM response before TTS starts speaking. That's the part that makes it feel like a real conversation instead of a chatbot with a voice skin.</p> <p>Chapters:</p> <ol> <li>Intro</li> <li>Audio IO</li> <li>Speech to Text (STT)</li> <li>Text to Speech (TTS)</li> <li>Full voice loop</li> <li>Real time systems</li> <li>Tools</li> <li>Personality</li> <li>Projects</li> </ol> <p>Each chapter is a runnable script + a short <a href="http://CODE.md">CODE.md</a> walkthrough. There's also a small shared library so you can see how the pieces compose into a real system, not just isolated calls.</p> <p><strong>Why fully local matters here:</strong> you can actually see where latency lives. Warm-up, first-audio time, streaming chunk size - these aren't abstractions when you're running it on your own machine.</p> <p>I plan a deployment chapter, thinking of using <a href="http://modal.com">modal.com</a> for it, wishes and suggestions are welcome.</p> <p>Repo: <a href="https://github.com/pguso/voice-agents-from-scratch">https://github.com/pguso/voice-agents-from-scratch</a></p> <p>I originally wanted to publish this repo using Node.js, but the ecosystem in Node.js is really not ready. There is a very good Kokoro-JS npm package, but when it comes to Whisper support or audio processing in general there are no good options.</p> <p>Happy to answer questions about the architecture or tradeoffs I ran into.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/purellmagents"> /u/purellmagents </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2pisc/built_a_voice_agents_from_scratch_github_tutorial/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2pisc/built_a_voice_agents_from_scratch_github_tutorial/">[comments]</a></span>

</details>