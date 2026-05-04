---
id: inbox_5f1315dc
date: 2026-05-04
source_ref: "[[00-inbox/.../inbox_5f1315dc]]"
title: "&#34;Second Thoughts&#34; Been playing with adding a small transformer that reads output near the end of generation, and feeds it back near the top as a refinement loop. A quick test of 1.7B model showed drastic improvement in focused tasks (like coding)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t33mlw/second_thoughts_been_playing_with_adding_a_small/
source: reddit-localllama
published_at: 2026-05-04T01:26:59+00:00
fetched_at: 2026-05-04T14:23:44.104019+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "研究者發表「Second Thoughts」技術：嵌入小型 Transformer 在生成流程末尾讀取中間輸出，反饋至序列開頭形成自我精煉迴圈。1.7B 模型在編程等聚焦任務實現「驚人進步」。靈感來自神經解剖學研究（Repeat Yourself），目前訓練 9B 版本進行完整 HumanEval 評測。提供雙向精煉循環提升小型模型性能的具體架構框架。"
key_points:
  - "雙向精煉迴圈架構：末尾 Transformer 讀輸出 → 反饋序列頂部，形成自我改進閉環"
  - "1.7B 模型在編碼任務大幅改善，9B 版本評測中（完整結果待 HumanEval 報告）"
  - "資源受限場景的可行方案：用小額外計算成本換性能提升，尤其聚焦任務"
tags: [small-llm-optimization, refinement-loop, technique, bidirectional-inference]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## "Second Thoughts" Been playing with adding a small transformer that reads output near the end of generation, and feeds it back near the top as a refinement loop. A quick test of 1.7B model showed drastic improvement in focused tasks (like coding)

研究者發表「Second Thoughts」技術：嵌入小型 Transformer 在生成流程末尾讀取中間輸出，反饋至序列開頭形成自我精煉迴圈。1.7B 模型在編程等聚焦任務實現「驚人進步」。靈感來自神經解剖學研究（Repeat Yourself），目前訓練 9B 版本進行完整 HumanEval 評測。提供雙向精煉循環提升小型模型性能的具體架構框架。

### 重點
- 雙向精煉迴圈架構：末尾 Transformer 讀輸出 → 反饋序列頂部，形成自我改進閉環
- 1.7B 模型在編碼任務大幅改善，9B 版本評測中（完整結果待 HumanEval 報告）
- 資源受限場景的可行方案：用小額外計算成本換性能提升，尤其聚焦任務

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t33mlw/second_thoughts_been_playing_with_adding_a_small/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# "Second Thoughts" Been playing with adding a small transformer that reads output near the end of generation, and feeds it back near the top as a refinement loop. A quick test of 1.7B model showed drastic improvement in focused tasks (like coding)

<!-- SC_OFF --><div class="md"><p>A 1.7B model can actually turn out some code, so I'm running the training for a 9B model, then will re-run HumanEval (a full one this time). I've shown most of my homework in the article, but will be posting to github after I clean things up.</p> <p>It was inspired by Repeat Yourself's <a href="https://dnhkng.github.io/posts/rys/"><strong>dnhkng.github.io/posts/rys/</strong></a> neuroanatomy findings... this gave me a start and end point to attach my &quot;reverse LLM&quot; side car model (so it reads from the end, and then injects its output back at the top - in a loop), in this case focusing on syntax - drastically improving a very tiny model.</p> <p>I'll also go back and run the full HumanEval dataset on both, instead of just the first 20.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/bigattichouse"> /u/bigattichouse </a> <br /> <span><a href="https://bigattichouse.medium.com/second-thoughts-improving-small-llms-with-bidirectional-refinement-loops-part-1-fa5ab51af656?sk=907cce272a3aed0eb3f1e3a0669a3964">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t33mlw/second_thoughts_been_playing_with_adding_a_small/">[comments]</a></span>

</details>