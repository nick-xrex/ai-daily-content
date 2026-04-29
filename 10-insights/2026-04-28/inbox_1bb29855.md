---
id: inbox_1bb29855
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0657-reddit-localllama-lemonade-omnirouter-unifying-the-best-lo-53d2]]"
title: "Lemonade OmniRouter: unifying the best local AI engines for omni-modality"
url: https://www.reddit.com/r/LocalLLaMA/comments/1sy54d1/lemonade_omnirouter_unifying_the_best_local_ai/
source: reddit-localllama
published_at: 2026-04-28T15:43:25+00:00
fetched_at: 2026-04-29T07:23:09.003289+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Lemonade 推出 OmniRouter，一個統一的本地 AI 多模態框架，集成 sd.cpp（圖像生成/編輯）、kokoros（文字轉語音）、whisper.cpp（轉錄）及 llama.cpp（視覺）四大引擎。用戶通過單一端點以 OpenAI 相容的 tool calling 方式調用這些功能，無需自建協調層。核心優勢是簡化複雜度：Python 完整範例僅 181 行，開發者即可構建多模態應用（如 TTRPG 冒險遊戲配文圖與語音）。已提供網頁 UI 和 Tauri 應用實現。"
key_points:
  - "四引擎整合架構：sd.cpp + kokoros + whisper.cpp + llama.cpp，透過 OpenAI 兼容 tool calling 統一路由，無需自定義協調層"
  - "開發效率：完整 Python 範例 181 行，降低多模態應用開發門檻"
  - "應用場景：已驗證可構建具沈浸感的體驗（配文圖語音的故事敘述）"
tags: [local-ai, omni-modal, tool-calling, framework, llm-orchestration]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Lemonade OmniRouter: unifying the best local AI engines for omni-modality

Lemonade 推出 OmniRouter，一個統一的本地 AI 多模態框架，集成 sd.cpp（圖像生成/編輯）、kokoros（文字轉語音）、whisper.cpp（轉錄）及 llama.cpp（視覺）四大引擎。用戶通過單一端點以 OpenAI 相容的 tool calling 方式調用這些功能，無需自建協調層。核心優勢是簡化複雜度：Python 完整範例僅 181 行，開發者即可構建多模態應用（如 TTRPG 冒險遊戲配文圖與語音）。已提供網頁 UI 和 Tauri 應用實現。

### 重點
- 四引擎整合架構：sd.cpp + kokoros + whisper.cpp + llama.cpp，透過 OpenAI 兼容 tool calling 統一路由，無需自定義協調層
- 開發效率：完整 Python 範例 181 行，降低多模態應用開發門檻
- 應用場景：已驗證可構建具沈浸感的體驗（配文圖語音的故事敘述）

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1sy54d1/lemonade_omnirouter_unifying_the_best_local_ai/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1sy54d1/lemonade_omnirouter_unifying_the_best_local_ai/"> <img alt="Lemonade OmniRouter: unifying the best local AI engines for omni-modality" src="https://external-preview.redd.it/bWM1Ymc2Y3NieXhnMYt8C7mo9BjJCz9oL63TvAKEUMjlwi1zV3PUzTslmebL.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=967725cd8238002572b6f37d26d48d615a79a721" title="Lemonade OmniRouter: unifying the best local AI engines for omni-modality" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>I’ve always liked how if I ask ChatGPT to make or edit an image, it just does it. Local AI should be this convenient! One install, one endpoint. Ask for an image of a cat and it appears. Ask for a hat on the cat, with a narrated story. Now we can easily build immersive experiences.</p> <p>Lemonade's OmniRouter brings that same pattern to local through built-in tools:</p> <ul> <li>Image generation/ editing through sd.cpp</li> <li>Text-to-speech through kokoros</li> <li>Transcription through whisper.cpp</li> <li>Vision through llama.cpp</li> </ul> <p>Your workflow talks to Lemonade running on your own NPU/GPU through OpenAI-compatible tool calling.</p> <p>How it works:</p> <ol> <li>Lemonade sets up all these local AI engines for your system.</li> <li>Add Lemonade’s tool definitions to your workflows.</li> <li>When your LLM triggers a tool call it gets routed to the corresponding engine (sd.cpp, whisper.cpp, kokoros).</li> <li>Feed the result back into your loop.</li> </ol> <p>That’s it. No custom orchestration layer, no new abstractions to learn. Check it out in <a href="https://github.com/lemonade-sdk/lemonade/blob/main/examples/lemonade_tools.py">this 181-line e2e Python example</a>.</p> <p>We’ve added support for OmniRouter in our reference web ui (also available as a Tauri app), which is what you’re seeing in the video. But I’m much more excited to see what people build on top.</p> <p>I know my next project is going to be some kind of TTRPG-style adventure game. It’s already surprisingly fun to ask OmniRouter to be a dungeon master who illustrates and narrates the story, and I think it can be enhanced quite a bit if I build an app/harness around it.</p> <p>If you find this interesting, please drop us a star and say hi! * GitHub: <a href="https://github.com/lemonade-sdk/lemonade">https://github.com/lemonade-sdk/lemonade</a> * Discord: <a href="https://discord.gg/5xXzkMu8Zk">https://discord.gg/5xXzkMu8Zk</a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/jfowers_amd"> /u/jfowers_amd </a> <br /> <span><a href="https://v.redd.it/se6dt0csbyxg1">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1sy54d1/lemonade_omnirouter_unifying_the_best_local_ai/">[comments]</a></span> </td></tr></table>

</details>