---
id: inbox_7a19aaf7
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-localllama-psa-llama-swap-released-a-new-grouping-f-b84d]]"
title: "PSA: llama-swap released a new grouping feature, matrix, allowing you to fine tune which models can run together"
url: https://www.reddit.com/r/LocalLLaMA/comments/1szwjrp/psa_llamaswap_released_a_new_grouping_feature/
source: reddit-localllama
published_at: 2026-04-30T13:45:50+00:00
fetched_at: 2026-05-01T13:31:34.627390+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llama-swap 工具發布新的 matrix 分組功能，突破傳統一模型一組的限制。新功能允許模型存在於多個並發組合中，使用 DSL 語言（支持 &、|、() 邏輯）定義靈活的模型共存策略，如「STT + 大模型」「RAG 專用組」等場景。系統基於卸載成本的求解器自動選擇最優組合，可為不同模型設定不同的卸載成本（例：vLLM 後端設 50、70B 模型設 30），避免頻繁重啟高成本模型。"
key_points:
  - "Matrix DSL 支持邏輯組合定義：(g|q|m)&v&e 自動展開為 [g,v,e]、[q,v,e]、[m,v,e] 三組"
  - "成本導向求解器：當請求模型 X 時，計算卸載現有模型的總成本，選擇成本最低的組合並執行"
  - "靈活卸載成本：TTS 模型設 50、大模型設 30、預設 1，支持場景化優化"
tags: [llama-swap, model-orchestration, resource-management, dsl-config]
topics: []
importance: 3
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## PSA: llama-swap released a new grouping feature, matrix, allowing you to fine tune which models can run together

llama-swap 工具發布新的 matrix 分組功能，突破傳統一模型一組的限制。新功能允許模型存在於多個並發組合中，使用 DSL 語言（支持 &、|、() 邏輯）定義靈活的模型共存策略，如「STT + 大模型」「RAG 專用組」等場景。系統基於卸載成本的求解器自動選擇最優組合，可為不同模型設定不同的卸載成本（例：vLLM 後端設 50、70B 模型設 30），避免頻繁重啟高成本模型。

### 重點
- Matrix DSL 支持邏輯組合定義：(g|q|m)&v&e 自動展開為 [g,v,e]、[q,v,e]、[m,v,e] 三組
- 成本導向求解器：當請求模型 X 時，計算卸載現有模型的總成本，選擇成本最低的組合並執行
- 靈活卸載成本：TTS 模型設 50、大模型設 30、預設 1，支持場景化優化

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1szwjrp/psa_llamaswap_released_a_new_grouping_feature/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Previously a model could only be present in a single group. Now you can create whatever groups you want: one for big models that should run on their own, a group for STT + bigger model, a group for RAG usages, etc. It'll intelligently unload models based on &quot;cost&quot; of doing so.</p> <p>Check out the config: <a href="https://github.com/mostlygeek/llama-swap/blob/main/config.example.yaml">llama-swap/config.example.yaml at main · mostlygeek/llama-swap</a></p> <pre><code># ============================================================================= # matrix: run concurrent models with a solver-based swap DSL # ============================================================================= # # Note: # A config must use either a matrix or legacy groups, not both. A configuration error # will occur if both are defined. Configuration examples for legacy Groups can be found: # https://github.com/mostlygeek/llama-swap/blob/40e39f7/config.example.yaml#L334-L396 # # The matrix declares valid combinations of models that can run concurrently. # When a model is requested, the solver finds the cheapest way to make it # available by evicting as few (and least costly) running models as possible. # # Solver behavior: # 1. Request arrives for model X # 2. If X is already running, forward immediately. Done. # 3. Find all sets containing X # 4. For each candidate set, compute cost: sum of evict_costs for # every running model NOT in that set # 5. Pick lowest cost candidate. Ties broken by definition order. # 6. Evict what needs to stop. Start X. Forward request. # # Subset semantics: a set [a, b, c] means any subset is valid. # Only the requested model is started — others are not preloaded. # # A model not appearing in any set can only run alone. # matrix: # vars: short names for models (alphanumeric, 1-8 chars) # - required for sets and evict_costs settings # - each entry is a short name to a real model ID. Do not use an alias # - used to keep set DSL logic short and easier to read # - sets and evict_costs only use identifiers defined in vars vars: g: gemma-model q: qwen-model m: mistral-model v: voxtral-model e: reranker-model L: llama-70B sd: stable-diffusion # evict_costs: relative cost of losing a running model (default: 1) evict_costs: v: 50 # vllm backend, slow cold start L: 30 # 70B weights, slow to load # sets: named sets of concurrent model combinations # Values are DSL strings with operators: # &amp; AND (models run together) # | OR (alternatives) # () grouping # +ref inline another set's expression # # Expansion examples: # &quot;L&quot; → [L] # &quot;a &amp; b&quot; → [a, b] # &quot;a | b&quot; → [a], [b] # &quot;(a | b) &amp; c&quot; → [a, c], [b, c] # &quot;(a | b) &amp; (c | d)&quot; → [a,c], [a,d], [b,c], [b,d] # &quot;+llms &amp; v&quot; → expands llms inline, then applies &amp; v sets: # LLM + TTS: switching between g/q/m won't evict v # expands to: [g,v], [q,v], [m,v] standard: &quot;(g | q | m) &amp; v&quot; # LLM + TTS + reranker # expands to: [g,v,e], [q,v,e] with_rerank: &quot;(g | q) &amp; v &amp; e&quot; # LLM + image generation, no TTS # expands to: [g,sd], [q,sd] creative: &quot;(g | q) &amp; sd&quot; # 70B model uses all GPUs, can only run alone # expands to: [L] full: &quot;L&quot; </code></pre> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/walden42"> /u/walden42 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1szwjrp/psa_llamaswap_released_a_new_grouping_feature/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1szwjrp/psa_llamaswap_released_a_new_grouping_feature/">[comments]</a></span>

</details>