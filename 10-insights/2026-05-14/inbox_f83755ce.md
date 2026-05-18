---
id: inbox_f83755ce
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_f83755ce]]"
title: "llama.cpp constantly reprocessing huge prompts with opencode/pi.dev"
url: https://www.reddit.com/r/LocalLLaMA/comments/1td9stc/llamacpp_constantly_reprocessing_huge_prompts/
source: reddit-localllama
published_at: 2026-05-14T20:11:39+00:00
fetched_at: 2026-05-18T04:00:09.856579+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者使用 llama-swap 搭配 llama.cpp 執行長上文編程任務時，遭遇頻繁的大規模提示詞重新處理。儘管 LCP 相似度達 0.996，n_past 仍突然下跌至 4,750 token，導致需要重新計算 40k+ token 的提示詞（耗時 222 秒），TTFT 延遲至數分鐘。配置為 ctx-size 150k、ctx-checkpoints 32、cache-ram 2500MB，但實際緩存用量達 4676MB 已超限。懷疑肇因為 KV 快取失效或 opencode 頻繁改動早期提示詞 token。"
key_points:
  - "長上文編程場景中，提示詞相似度 0.99+ 不保證有效快取重用——cache-ram 限制 2500MB 但實際用量 4676MB"
  - "llama.cpp 配置參數 (ctx-size 150k, ctx-checkpoints 32, cache-reuse 256) 無法完全避免 KV 重建，需進一步優化 checkpoint 策略"
  - "TTFT 從 473ms 跳增至 200+s，源自 n_past 回退導致 40k token 重新評估——提示 opencode 或 pi.dev 可能觸發動態提示詞修改"
tags: [llama-cpp, kv-cache, long-context, context-reuse, performance-tuning]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## llama.cpp constantly reprocessing huge prompts with opencode/pi.dev

開發者使用 llama-swap 搭配 llama.cpp 執行長上文編程任務時，遭遇頻繁的大規模提示詞重新處理。儘管 LCP 相似度達 0.996，n_past 仍突然下跌至 4,750 token，導致需要重新計算 40k+ token 的提示詞（耗時 222 秒），TTFT 延遲至數分鐘。配置為 ctx-size 150k、ctx-checkpoints 32、cache-ram 2500MB，但實際緩存用量達 4676MB 已超限。懷疑肇因為 KV 快取失效或 opencode 頻繁改動早期提示詞 token。

### 重點
- 長上文編程場景中，提示詞相似度 0.99+ 不保證有效快取重用——cache-ram 限制 2500MB 但實際用量 4676MB
- llama.cpp 配置參數 (ctx-size 150k, ctx-checkpoints 32, cache-reuse 256) 無法完全避免 KV 重建，需進一步優化 checkpoint 策略
- TTFT 從 473ms 跳增至 200+s，源自 n_past 回退導致 40k token 重新評估——提示 opencode 或 pi.dev 可能觸發動態提示詞修改

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1td9stc/llamacpp_constantly_reprocessing_huge_prompts/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# llama.cpp constantly reprocessing huge prompts with opencode/pi.dev

I’m using llama-swap with llama.cpp. I mainly use opencode + pi.dev and I’m seeing frequent massive prompt reprocessing / prefills even tho the prompts are very similar between requests. Example behavior: context grows to +50k tokens LCP similarity often shows 0.99+ but sometimes n_past suddenly falls back to ~4-5k then llama.cpp reprocesses 40k+ tokens again TTFT jumps to multiple minutes Example logs: sim_best = 0.996 restored context checkpoint ... n_tokens = 4750 prompt eval time = 222411 ms / 44016 tokens Normal reuse looks fine: prompt eval time = 473 ms / 19 tokens Current config: llama-server --ctx-size 150000 --parallel 1 --ctx-checkpoints 32 --cache-ram 2500 --cache-reuse 256 -no-kvu --no-context-shift Also seeing: cache state: 1 prompts, 4676 MiB (limits: 2500 MiB) I suspect either: cache invalidation bad KV reuse or opencode changing early prompt tokens too often. Would love to hear from others running long-context coding agents with llama.cpp and what settings helped reduce huge prompt reprocessing. &#32; submitted by &#32; /u/No_Algae1753 [link] &#32; [comments]

</details>