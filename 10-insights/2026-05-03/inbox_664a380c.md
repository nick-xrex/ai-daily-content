---
id: inbox_664a380c
date: 2026-05-03
source_ref: "[[00-inbox/.../inbox_664a380c]]"
title: "Local LLM Benchmark about Backend Generation by Function Calling (GLM vs Qwen vs DeepSeek)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t2m7wi/local_llm_benchmark_about_backend_generation_by/
source: reddit-localllama
published_at: 2026-05-03T13:59:02+00:00
fetched_at: 2026-05-04T14:27:18.220020+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AutoBe 發佈了本地 LLM 函數呼叫能力的受控基準測試（non-trivial AST schema 填充），嚴格對比 Qwen、DeepSeek、GLM 與前沿模型（GPT-5.4、Claude-Sonnet-4.6）。核心發現：Qwen3.5-35b-a3b 的 DB/API 設計能力接近 GPT-5.4，Qwen3.5-27b 的邏輯推理接近 Claude-Sonnet-4.6，函數呼叫框架已有效縮小本地與前沿模型間的性能差距。此後停止納入前沿模型（每月成本 $1000–1500）改為聚焦 <$0.25/M 的模型或 64GB 筆記本可運行版本。報告揭示數個反常結果（GPT-5.4 低於自身 mini 版本、Deepseek-v4-pro 落後 Qwen、27B 密集模型勝 MoE 大模型），初步歸因於 CoT 依從性現象——大型模型傾向跳過程序指令，框架強制執行導致性能反轉。"
key_points:
  - "性能追平：Qwen3.5-35b-a3b DB/API ≈ GPT-5.4；Qwen3.5-27b 邏輯 ≈ Claude-Sonnet-4.6，本地模型已與前沿並駕齊驅"
  - "成本最優化：下月聚焦 gpt-5.4-nano($0.25/M)、qwen3.6-27b($0.195/M)、deepseek-v4-flash($0.14/M)，避免 $1000–1500/月測試成本"
  - "CoT 依從性現象：更大/更前沿的模型傾向忽視程序指令，函數呼叫框架強制遵循，可能導致性能逆轉，需進一步調查"
tags: [local-llm-benchmark, function-calling, model-comparison, cost-efficiency, backend-generation]
topics: [foundation_models.claude, foundation_models.gpt]
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Local LLM Benchmark about Backend Generation by Function Calling (GLM vs Qwen vs DeepSeek)

AutoBe 發佈了本地 LLM 函數呼叫能力的受控基準測試（non-trivial AST schema 填充），嚴格對比 Qwen、DeepSeek、GLM 與前沿模型（GPT-5.4、Claude-Sonnet-4.6）。核心發現：Qwen3.5-35b-a3b 的 DB/API 設計能力接近 GPT-5.4，Qwen3.5-27b 的邏輯推理接近 Claude-Sonnet-4.6，函數呼叫框架已有效縮小本地與前沿模型間的性能差距。此後停止納入前沿模型（每月成本 $1000–1500）改為聚焦 <$0.25/M 的模型或 64GB 筆記本可運行版本。報告揭示數個反常結果（GPT-5.4 低於自身 mini 版本、Deepseek-v4-pro 落後 Qwen、27B 密集模型勝 MoE 大模型），初步歸因於 CoT 依從性現象——大型模型傾向跳過程序指令，框架強制執行導致性能反轉。

### 重點
- 性能追平：Qwen3.5-35b-a3b DB/API ≈ GPT-5.4；Qwen3.5-27b 邏輯 ≈ Claude-Sonnet-4.6，本地模型已與前沿並駕齊驅
- 成本最優化：下月聚焦 gpt-5.4-nano($0.25/M)、qwen3.6-27b($0.195/M)、deepseek-v4-flash($0.14/M)，避免 $1000–1500/月測試成本
- CoT 依從性現象：更大/更前沿的模型傾向忽視程序指令，函數呼叫框架強制遵循，可能導致性能逆轉，需進一步調查

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t2m7wi/local_llm_benchmark_about_backend_generation_by/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Local LLM Benchmark about Backend Generation by Function Calling (GLM vs Qwen vs DeepSeek)

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2m7wi/local_llm_benchmark_about_backend_generation_by/"> <img alt="Local LLM Benchmark about Backend Generation by Function Calling (GLM vs Qwen vs DeepSeek)" src="https://preview.redd.it/1savo9unhxyg1.png?width=140&amp;height=104&amp;auto=webp&amp;s=aeeac419ec840ef4df5b2578b89d3f8abeb0b2f8" title="Local LLM Benchmark about Backend Generation by Function Calling (GLM vs Qwen vs DeepSeek)" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p><strong>Detailed Article: <a href="https://autobe.dev/articles/local-llm-benchmark-about-backend-generation.html">https://autobe.dev/articles/local-llm-benchmark-about-backend-generation.html</a></strong></p> <hr /> <p>Five months ago I posted the <a href="https://www.reddit.com/r/LocalLLaMA/comments/1p2ziil/hardcore_function_calling_benchmark_in_backend/">&quot;Hardcore function calling benchmark in backend coding agent&quot;</a> thread here. As I wrote in that post, it was an uncontrolled measurement — useful for showing whether each model could fill our complex recursive-union AST schemas at all, but not really a benchmark in any rigorous sense.</p> <p>This post is the proper version, with controlled variables and a real scoring rubric.</p> <h2>Three findings worth sharing</h2> <ol> <li><p><strong>The <a href="https://autobe.dev/articles/qwen-meetup-function-calling-harness.html">function calling harness</a> has effectively closed the frontier-vs-local gap on backend generation.</strong> <code>gpt-5.4</code>'s DB/API design ≈ <code>qwen3.5-35b-a3b</code>'s. <code>claude-sonnet-4.6</code>'s logic ≈ <code>qwen3.5-27b</code>'s.</p></li> <li><p><strong>This is the last round we include frontier models.</strong> Running them every month is genuinely too expensive for an open-source project — one shopping-mall run is ~200–300M tokens (~$1,000–$1,500 per model on GPT 5.5 pricing). From next month, the comparison set is limited to OpenRouter endpoints under $0.25/M, or models that fit on a 64GB unified-memory laptop.</p></li> <li><p><a href="https://nestia.io/articles/well-designed-backend-fully-automated-frontend-development.html"><strong>Frontend automation joins the benchmark in two or three months.</strong></a> The SDK that AutoBe already emits is enough to drive a working AI-built frontend end-to-end (visuals rough, but every function works). The June/July round will cover backend + auto-generated frontend together.</p></li> </ol> <h2>Three inversions, still investigating</h2> <p>A few results I'm honestly not sure how to read yet:</p> <ul> <li><code>openai/gpt-5.4</code> actually scores below its own <code>mini</code> sibling.</li> <li><code>deepseek-v4-pro</code> lands one notch below <code>qwen3.5-35b-a3b</code>, and barely separates from its own Flash sibling.</li> <li>Within the Qwen family, dense 27B beats every MoE variant — even 397B-A17B.</li> </ul> <p>Two readings I want to investigate before claiming anything:</p> <ol> <li><a href="https://autobe.dev/articles/function-calling-harness-2-cot-compliance.html"><strong>CoT-compliance phenomenon</strong></a> — bigger / more frontier-tier models tending to skip procedural instructions, which our harness enforces hard.</li> <li><strong>Benchmark defects</strong> — n=4 reference projects, narrow score band, our own harness scoring our own pipeline.</li> </ol> <p>I'll report back in a future round once we've dug more.</p> <h2>Recommendations welcome</h2> <p>Three candidates we're locked in on so far:</p> <ul> <li><code>openai/gpt-5.4-nano</code> — $0.25/M</li> <li><code>qwen/qwen3.6-27b</code> — $0.195/M</li> <li><code>deepseek/deepseek-v4-flash</code> — $0.14/M</li> </ul> <p>If you know other small models that meet either condition (under $0.25/M on OpenRouter, or runnable on a 64GB unified-memory laptop) and handle function calling cleanly, please drop a comment. </p> <p><a href="https://www.reddit.com/r/LocalLLaMA">r/LocalLLaMA</a> tends to spot these faster than we do, and recommendations from this thread will fill out a big chunk of next month's comparison set.</p> <h2>References</h2> <ul> <li>Benchmark Dashboard: <a href="https://autobe.dev/benchmark/">https://autobe.dev/benchmark/</a></li> <li>Generation Results: <a href="https://github.com/wrtnlabs/autobe-examples">https://github.com/wrtnlabs/autobe-examples</a></li> <li>Github Repository: <a href="https://github.com/wrtnlabs/autobe">https://github.com/wrtnlabs/autobe</a></li> </ul> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/jhnam88"> /u/jhnam88 </a> <br /> <span><a href="https://www.reddit.com/gallery/1t2m7wi">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2m7wi/local_llm_benchmark_about_backend_generation_by/">[comments]</a></span> </td></tr></table>

</details>