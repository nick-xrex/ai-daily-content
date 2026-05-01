---
id: inbox_df71143a
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-localllama-terminal-bench-score-for-mistral-3-5-med-5834]]"
title: "Terminal Bench score for Mistral 3.5 Medium"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t00fkh/terminal_bench_score_for_mistral_35_medium/
source: reddit-localllama
published_at: 2026-04-30T15:57:25+00:00
fetched_at: 2026-05-01T13:34:01.725131+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者自行運行 TerminalBench Lite（TBLite，輕量版 TB 2.0）對 Mistral 3.5 Medium 進行基準測試，相比 Mistral Small 4 工具調用與代理循環能力大幅改進。測試結果與 GPT-4o、Claude Opus 4.6、GLM-5 對標，顯示 Mistral 3.5 Medium 在同等規模模型中表現優異，MoE 架構相比前代有明顯進步。"
key_points:
  - "Mistral 3.5 Medium 在 TBLite 基準上相比 Mistral Small 4 工具調用與代理性能顯著提升"
  - "提供了 SWEBench Verified 跨模型對標：GPT-4o、Opus 4.6、GLM-5，便於量化對比"
  - "MoE 架構改進使同等參數量下代理任務性能躍升"
tags: [mistral-3.5-medium, benchmark, terminalbench, agentic-loops, tool-calling]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Terminal Bench score for Mistral 3.5 Medium

使用者自行運行 TerminalBench Lite（TBLite，輕量版 TB 2.0）對 Mistral 3.5 Medium 進行基準測試，相比 Mistral Small 4 工具調用與代理循環能力大幅改進。測試結果與 GPT-4o、Claude Opus 4.6、GLM-5 對標，顯示 Mistral 3.5 Medium 在同等規模模型中表現優異，MoE 架構相比前代有明顯進步。

### 重點
- Mistral 3.5 Medium 在 TBLite 基準上相比 Mistral Small 4 工具調用與代理性能顯著提升
- 提供了 SWEBench Verified 跨模型對標：GPT-4o、Opus 4.6、GLM-5，便於量化對比
- MoE 架構改進使同等參數量下代理任務性能躍升

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t00fkh/terminal_bench_score_for_mistral_35_medium/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t00fkh/terminal_bench_score_for_mistral_35_medium/"> <img alt="Terminal Bench score for Mistral 3.5 Medium" src="https://preview.redd.it/bgrl55b6ocyg1.png?width=140&amp;height=78&amp;auto=webp&amp;s=a52ada2a11dfeeb87bd3569a0f8b81cc7e00eb11" title="Terminal Bench score for Mistral 3.5 Medium" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>So... there were a couple promising benchmark scores reported by mistralai in the model card for Mistral 3.5 Medium, BUT there wasn't the one that I usually care about the most, which is TerminalBench 2.0. So... since I was really curious how the new Mistral handles agentic stuff, I decided to benchmark it myself.</p> <p>I didn't run TerminalBench 2.0, because I'm not crazy (usage would be biiiig), BUT I did run TBLite, which is a lighter/faster version of TerminalBench 2.0. The scores in this smaller variant don't correlate directly with TB2 scores, however the trend among models does (if a model does better than other model in TBLite, it would also do better at TerminalBench 2.0).</p> <p>I did only one run, so it's not 100% accurate likely, however I decided to share the result here, since maybe someone is also curious, especially as Mistral Small 4 was... quite bad in terms of tool calling and agentic loops. Still... the result is below. I added a couple other models that have a TBLite score reported in the benchmark card + added SWEBench Verified scores for them and for GPT-5.4, Opus4.6 and GLM-5 (just to see comparison). Tbh. for it's size Mistral 3.5 Medium does really well and most of all is a big improvement when compared with previous mistralai models. (Hurray, I really cheer for Mistral)</p> <p><a href="https://preview.redd.it/bgrl55b6ocyg1.png?width=1672&amp;format=png&amp;auto=webp&amp;s=a3b9a87e4bce2b1b3cb7787c377c5387a7c0a67e">https://preview.redd.it/bgrl55b6ocyg1.png?width=1672&amp;format=png&amp;auto=webp&amp;s=a3b9a87e4bce2b1b3cb7787c377c5387a7c0a67e</a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Real_Ebb_7417"> /u/Real_Ebb_7417 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t00fkh/terminal_bench_score_for_mistral_35_medium/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t00fkh/terminal_bench_score_for_mistral_35_medium/">[comments]</a></span> </td></tr></table>

</details>