---
id: inbox_93834ade
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/1002-reddit-localllama-use-qwen3-6-right-way-send-it-to-pi-codi-e65a]]"
title: "Use Qwen3.6 right way -&gt; send it to pi coding agent and forget"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t4ji36/use_qwen36_right_way_send_it_to_pi_coding_agent/
source: reddit-localllama
published_at: 2026-05-05T15:53:42+00:00
fetched_at: 2026-05-06T10:26:51.819231+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "社群使用者基於 2 個月實踐推薦以 pi.dev（agentic coding 框架）作為 Qwen 3.6 35B 的主要執行環境，搭配 exa web search 與 agent-browser 外掛，宣稱可覆蓋 80% 個人使用場景（編程、機器維運、web 研究）；並採多模型策略，複雜規劃外包 Kimi 2.6。核心發現：執行框架的選擇影響力優於模型本身。"
key_points:
  - "執行環境（harness）選擇比基礎模型更影響實際使用體驗，pi.dev 顯著升級 Qwen 3.6 適用範疇"
  - "多模型組合策略：複雜規劃→Kimi 2.6，編碼→Qwen 3.6，web research→Qwen 3.6+exa，可替代 Perplexity"
  - "2 個月持續運作驗證，覆蓋編程、系統維運、web 研究 3 大場景"
tags: [qwen-3.6, pi-dev, agentic-framework, multi-model]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Use Qwen3.6 right way -> send it to pi coding agent and forget

社群使用者基於 2 個月實踐推薦以 pi.dev（agentic coding 框架）作為 Qwen 3.6 35B 的主要執行環境，搭配 exa web search 與 agent-browser 外掛，宣稱可覆蓋 80% 個人使用場景（編程、機器維運、web 研究）；並採多模型策略，複雜規劃外包 Kimi 2.6。核心發現：執行框架的選擇影響力優於模型本身。

### 重點
- 執行環境（harness）選擇比基礎模型更影響實際使用體驗，pi.dev 顯著升級 Qwen 3.6 適用範疇
- 多模型組合策略：複雜規劃→Kimi 2.6，編碼→Qwen 3.6，web research→Qwen 3.6+exa，可替代 Perplexity
- 2 個月持續運作驗證，覆蓋編程、系統維運、web 研究 3 大場景

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t4ji36/use_qwen36_right_way_send_it_to_pi_coding_agent/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4ji36/use_qwen36_right_way_send_it_to_pi_coding_agent/"> <img alt="Use Qwen3.6 right way -&gt; send it to pi coding agent and forget" src="https://preview.redd.it/z4b01gklaczg1.jpg?width=140&amp;height=116&amp;auto=webp&amp;s=656f42bd4fe7e5c6de8b3a6b693f2f84a0022916" title="Use Qwen3.6 right way -&gt; send it to pi coding agent and forget" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p><a href="https://preview.redd.it/z4b01gklaczg1.jpg?width=1080&amp;format=pjpg&amp;auto=webp&amp;s=3cefa63d5d15eac5eedbb39ef19d6c476b22ae64">https://preview.redd.it/z4b01gklaczg1.jpg?width=1080&amp;format=pjpg&amp;auto=webp&amp;s=3cefa63d5d15eac5eedbb39ef19d6c476b22ae64</a></p> <p>Just a reminder, the harness you use can makes a huge diffrence (your llm client and interface bascially), It's is way more important than people think, I'm using <a href="http://pi.dev">pi.dev</a> for over 2 months and oooh boy Qwen3.6 suddenly become a monster. </p> <p>my local machine + pi + exa web seach + agent-browser extenion and this setup can solve 80% of all my use cases which are:</p> <p>now</p> <p>- coding (python / rust / c++)<br /> - anything require maintance / adminstration on my machines (linux machines mainly)<br /> - web research, qwen3.6 35b with exa web research is a monster and can 100% replace perplixity for me and even give better results (only sacrific some time as side effect) </p> <p>complex planning task i delegate it to kimi2.6 and coding itself is handled by Qwen3.6 </p> <p>at the end: Use your Qwen3.6 with Pi coding and forget 😃 </p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Willing-Toe1942"> /u/Willing-Toe1942 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4ji36/use_qwen36_right_way_send_it_to_pi_coding_agent/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4ji36/use_qwen36_right_way_send_it_to_pi_coding_agent/">[comments]</a></span> </td></tr></table>

</details>