---
id: inbox_fd4bb3a6
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/1002-reddit-localllama-qwen3-6-merged-chat-template-from-allanc-7402]]"
title: "Qwen3.6 merged chat template from allanchan339 and froggeric"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t4cev0/qwen36_merged_chat_template_from_allanchan339_and/
source: reddit-localllama
published_at: 2026-05-05T11:16:48+00:00
fetched_at: 2026-05-06T10:26:51.818142+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "社群開發者使用 Claude Opus 合併兩套獨立的 Qwen 3.6 chat template 改進方案，生成統一版本涵蓋 8 項功能增強：strict tool rules、developer role、think_on/off 切換、reasoning 隱藏、JSON 參數解析、非 ASCII 轉義、多 closing tag 識別、unclosed think 自動閉合；已於 llama-server + Qwen 3.6 35B 驗證，開源至 GitHub gist。"
key_points:
  - "Merged template 整合兩套方案的全部優勢，涵蓋 tool calling、thinking、JSON 處理 8 個維度"
  - "使用 Claude Opus 進行複雜 template 邏輯設計與整合，展示大模型在開發工具鏈中的應用"
  - "提供即用型 gist 供社群直接整合至 llama-server"
tags: [qwen-3.6, chat-template, prompt-engineering, tool-calling]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen3.6 merged chat template from allanchan339 and froggeric

社群開發者使用 Claude Opus 合併兩套獨立的 Qwen 3.6 chat template 改進方案，生成統一版本涵蓋 8 項功能增強：strict tool rules、developer role、think_on/off 切換、reasoning 隱藏、JSON 參數解析、非 ASCII 轉義、多 closing tag 識別、unclosed think 自動閉合；已於 llama-server + Qwen 3.6 35B 驗證，開源至 GitHub gist。

### 重點
- Merged template 整合兩套方案的全部優勢，涵蓋 tool calling、thinking、JSON 處理 8 個維度
- 使用 Claude Opus 進行複雜 template 邏輯設計與整合，展示大模型在開發工具鏈中的應用
- 提供即用型 gist 供社群直接整合至 llama-server

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t4cev0/qwen36_merged_chat_template_from_allanchan339_and/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Hi,</p> <p>recently <a href="https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates">froggeric</a> and <a href="https://github.com/allanchan339/vLLM-Qwen3-3.5-3.6-chat-template-fix">allanchan339</a> released enhanced/fixed template for Qwen3.6 each one addressing different topics.<br /> I didn't know which one to use so I merged both with the help of Claude Opus to have the best of both.</p> <p>I've uploaded it to this gist<br /> <a href="https://gist.github.com/fakezeta/9e8e039c60332fcb143c6e805558afe0">https://gist.github.com/fakezeta/9e8e039c60332fcb143c6e805558afe0</a></p> <p>Here a summary table done with Opus</p> <table><thead> <tr> <th align="left">Feature</th> <th align="left">allanchan339</th> <th align="left">froggeric</th> <th align="left">Merged</th> </tr> </thead><tbody> <tr> <td align="left">Long strict tool rules + follow-up example</td> <td align="left">✅</td> <td align="left">❌</td> <td align="left">✅</td> </tr> <tr> <td align="left"><code>developer</code> role accepted</td> <td align="left">❌</td> <td align="left">✅</td> <td align="left">✅</td> </tr> <tr> <td align="left">think_off &amp; think_on toggles</td> <td align="left">❌</td> <td align="left">✅</td> <td align="left">✅</td> </tr> <tr> <td align="left">Historical reasoning hidden by default</td> <td align="left">✅</td> <td align="left">❌</td> <td align="left">✅</td> </tr> <tr> <td align="left">String tool args parsed as JSON into <code>&lt;parameter&gt;</code> blocks</td> <td align="left">✅</td> <td align="left">❌</td> <td align="left">✅</td> </tr> <tr> <td align="left">Non-ASCII in JSON escaped (<code>uXXXX</code>)</td> <td align="left">❌</td> <td align="left">✅</td> <td align="left">✅</td> </tr> <tr> <td align="left"><code>&lt;/thinking&gt;</code> recognized (not just <code>&lt;/think&gt;</code>)</td> <td align="left">❌</td> <td align="left">✅</td> <td align="left">✅</td> </tr> <tr> <td align="left">Auto-close unclosed <code>&lt;think&gt;</code> before <code>&lt;tool_call&gt;</code></td> <td align="left">✅</td> <td align="left">❌</td> <td align="left">✅</td> </tr> <tr> <td align="left">Vision + tool_response structure</td> <td align="left">same</td> <td align="left">same</td> <td align="left">same</td> </tr> </tbody></table> <p>I've tested with llama-server and Qwen3.6 35B A3B</p> <p>Hope you like it.<br /> If there is anything good the praise it for froggeric and allanchan339.</p> <p>Any blame instead is for me but please be kind 😄</p> <p>edit: fixed table messed up by <code>&lt;|think_off|&gt;</code> / <code>&lt;|think_on|&gt;</code> toggles</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/fakezeta"> /u/fakezeta </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4cev0/qwen36_merged_chat_template_from_allanchan339_and/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4cev0/qwen36_merged_chat_template_from_allanchan339_and/">[comments]</a></span>

</details>