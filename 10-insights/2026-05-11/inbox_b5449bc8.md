---
id: inbox_b5449bc8
date: 2026-05-11
source_ref: "[[00-inbox/.../inbox_b5449bc8]]"
title: "PSA: Watch out for extra spaces in chat-template-kwargs when using Qwen3.6 with llama-server"
url: https://www.reddit.com/r/LocalLLaMA/comments/1ta1og5/psa_watch_out_for_extra_spaces_in/
source: reddit-localllama
published_at: 2026-05-11T12:21:50+00:00
fetched_at: 2026-05-12T01:39:55.208724+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用 Qwen3.6 與 llama-server v9102 時，chat-template-kwargs JSON 字符串中的多餘空格會破壞 preserve_thinking 參數解析，導致思考層功能失效。正確做法是移除 JSON 中的所有空格。作者提供了驗證方法：發送特定提示詞後檢查推理輸出一致性，若前後不一致則表示配置解析有誤。"
key_points:
  - "llama-server v9102 JSON 解析 bug：`{\"preserve_thinking\": true}` 成功，`{ \"preserve_thinking\": true }` 失敗"
  - "preserve_thinking 參數對 Qwen3.6 思考層至關重要"
  - "提供具體測試 prompt 驗證配置是否生效"
tags: [qwen3.6, llama-server, json-parsing, preserve-thinking, troubleshooting]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## PSA: Watch out for extra spaces in chat-template-kwargs when using Qwen3.6 with llama-server

使用 Qwen3.6 與 llama-server v9102 時，chat-template-kwargs JSON 字符串中的多餘空格會破壞 preserve_thinking 參數解析，導致思考層功能失效。正確做法是移除 JSON 中的所有空格。作者提供了驗證方法：發送特定提示詞後檢查推理輸出一致性，若前後不一致則表示配置解析有誤。

### 重點
- llama-server v9102 JSON 解析 bug：`{"preserve_thinking": true}` 成功，`{ "preserve_thinking": true }` 失敗
- preserve_thinking 參數對 Qwen3.6 思考層至關重要
- 提供具體測試 prompt 驗證配置是否生效

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1ta1og5/psa_watch_out_for_extra_spaces_in/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# PSA: Watch out for extra spaces in chat-template-kwargs when using Qwen3.6 with llama-server

Hey folks, just a heads-up for anyone running Qwen3.6 through llama-server . I ran into an issue where the preserve_thinking parameter wasn't working as expected, even though I had it explicitly enabled in my models.ini config. After some digging, I found that extra spaces in the JSON string are breaking the parser for this specific parameter in my build. ❌ Does NOT work: chat-template-kwargs = { &quot;preserve_thinking&quot;: true } ✅ Works: chat-template-kwargs = {&quot;preserve_thinking&quot;: true} How to test it: The easiest way to verify if it's working is to send this prompt: think of a number from 1 to 100, don't tell me what it is, I'm going to guess it Then check the reasoning/thinking output to verify that the &quot;hidden&quot; number stays consistent across your guesses. If it changes, your template kwargs are likely being parsed incorrectly. My env: llama-server v9102 (7d442abf5) | RTX 4090 Might be a minor parsing quirk in how llama-server handles JSON in the ini file, but it's definitely worth checking. Hope this saves someone some debugging time! &#32; submitted by &#32; /u/CaptBrick [link] &#32; [comments]

</details>