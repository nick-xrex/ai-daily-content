---
id: inbox_ee8d0e0d
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_ee8d0e0d]]"
title: "Playing One Night Werewolf (Gemma4 &amp; Qwen3.6)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tcjtmt/playing_one_night_werewolf_gemma4_qwen36/
source: reddit-localllama
published_at: 2026-05-14T01:45:32+00:00
fetched_at: 2026-05-18T03:44:23.050998+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶運用 llama.cpp 客製化 UI，讓四個本地模型（Gemma4 31B/26B、Qwen 3.6 27B/35B）玩角色遊戲「One Night Werewolf」。各模型展現不同特徵：Gemma4 31B 最會欺騙且思考清晰，Qwen 3.6 35B 工具調用最佳但容易被騙，Qwen 3.6 27B 思考關閉後推理較弱且推理慢。每個模型有獨立 markdown 記錄空間用於隱私思考與觀察。提供複雜推理與策略場景下的實務對比數據。"
key_points:
  - "Gemma4 31B：欺騙能力最強、思考記錄清晰；Qwen 3.6 35B：工具調用優異但容易被騙"
  - "Qwen 3.6 27B：思考模式對性能影響顯著（思考關閉後推理能力下降）"
  - "遊戲場景提供複雜推理與策略評估的實務對比"
tags: [gemma4, qwen-3.6, llama-cpp, game-play, reasoning]
topics: []
importance: 2
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Playing One Night Werewolf (Gemma4 & Qwen3.6)

用戶運用 llama.cpp 客製化 UI，讓四個本地模型（Gemma4 31B/26B、Qwen 3.6 27B/35B）玩角色遊戲「One Night Werewolf」。各模型展現不同特徵：Gemma4 31B 最會欺騙且思考清晰，Qwen 3.6 35B 工具調用最佳但容易被騙，Qwen 3.6 27B 思考關閉後推理較弱且推理慢。每個模型有獨立 markdown 記錄空間用於隱私思考與觀察。提供複雜推理與策略場景下的實務對比數據。

### 重點
- Gemma4 31B：欺騙能力最強、思考記錄清晰；Qwen 3.6 35B：工具調用優異但容易被騙
- Qwen 3.6 27B：思考模式對性能影響顯著（思考關閉後推理能力下降）
- 遊戲場景提供複雜推理與策略評估的實務對比

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tcjtmt/playing_one_night_werewolf_gemma4_qwen36/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Playing One Night Werewolf (Gemma4 & Qwen3.6)

Finally feel like it’s possible. I have a custom build (vibe coded) UI on llama.cpp, allows model switching in the same chat. So I thought I’d get Gemma4 31B Q4, Gemma4 26B Q5, Qwen3.6 27B Q5, Qwen3.6 35B Q4 all together to play ONUW. Had to switch the thinking off the Qwens so they don’t think out loud into public chat. So firstly at night I assigned each llm with a card (werewolf, seer, villager, troublemaker) and the read their card.md, and write their observations and thinkings in their own Mr as to keep it private to each. Then day time in the game I bring them to public game chat. Each turn they read their md, defend and ask questions, record their observations for 8-10 turns, then write their final thought down for voting. Back to individual chat for voting. Gemma4 31B — best lier. Clearest thoughts in notes. Gemma4 26B — suck at using tools. Quick to think but no deep thoughts. Qwen3.6 35B — thought it was villager and tried to be bold. Got owned. Best at tool calls. Qwen3.6 27B — not very bright when thinking is off. Oh so slow ... Not a very productive way of using llms I know...Any models I can add to the game ? Suggestions? &#32; submitted by &#32; /u/Some-Cauliflower4902 [link] &#32; [comments]

</details>