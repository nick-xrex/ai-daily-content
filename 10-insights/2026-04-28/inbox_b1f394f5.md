---
id: inbox_b1f394f5
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0657-reddit-localllama-qwen-3-6-27b-bf16-vs-q4-k-m-vs-q8-0-gguf-d3f0]]"
title: "Qwen 3.6 27B BF16 vs Q4_K_M vs Q8_0 GGUF evaluation"
url: https://www.reddit.com/r/LocalLLaMA/comments/1sxzqry/qwen_36_27b_bf16_vs_q4_k_m_vs_q8_0_gguf_evaluation/
source: reddit-localllama
published_at: 2026-04-28T12:18:37+00:00
fetched_at: 2026-04-29T07:19:25.913636+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用 llama-cpp-python 對 Qwen 3.6 27B 進行三種量化方案的詳細評估。BF16（完整精度）達 69.78% 平均精度（HumanEval 56.10%、HellaSwag 90%、BFCL 63.25%），吞吐 15.5 tok/s，佔用 54GB 記憶體。Q4_K_M（4-bit）精度 66.54%，吞吐 22.5 tok/s（快 1.45 倍），記憶體僅 28GB（少 48%），模型檔 16.8GB（縮小 69%），函數調用精度 63.0% 與 BF16 無異（252 vs 253/400）。Q8_0（8-bit）精度 66.15%，介於兩者但在 HellaSwag 低於 Q4_K_M，記憶體 42GB，吞吐 18 tok/s。結論：本地/CPU 部署建議優先 Q4_K_M，除非工作量極度偏向代碼生成。評估覆蓋 HumanEval 164 樣本、HellaSwag 100 樣本、BFCL 400 樣本，採用檢查點機制確保可重現性，使用 Neo AI Engineer 建立評估流程。"
key_points:
  - "Qwen 3.6 27B 量化權衡：Q4_K_M 在函數調用上精度不減（63.0%），HumanEval 僅下降 ~5.5 點（50.61% vs 56.10%），卻獲得 1.45 倍吞吐與 48% 記憶體節省"
  - "Q8_0 未展現預期效果：HumanEval 相對 Q4_K_M 僅改善 ~1.8 點（52.44%），卻佔用 14GB 更多記憶體且速度更慢，HellaSwag 反而下滑至 83%"
  - "評估範疇明確：HumanEval 164 樣本、HellaSwag 100 樣本、BFCL 400 樣本，context window 32768，採檢查點機制，由 Neo AI Engineer 自動化檢查點管理與結果彙整"
tags: [model-quantization, qwen-3.6, gguf, llama-cpp, benchmarking]
topics: []
importance: 4
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen 3.6 27B BF16 vs Q4_K_M vs Q8_0 GGUF evaluation

使用 llama-cpp-python 對 Qwen 3.6 27B 進行三種量化方案的詳細評估。BF16（完整精度）達 69.78% 平均精度（HumanEval 56.10%、HellaSwag 90%、BFCL 63.25%），吞吐 15.5 tok/s，佔用 54GB 記憶體。Q4_K_M（4-bit）精度 66.54%，吞吐 22.5 tok/s（快 1.45 倍），記憶體僅 28GB（少 48%），模型檔 16.8GB（縮小 69%），函數調用精度 63.0% 與 BF16 無異（252 vs 253/400）。Q8_0（8-bit）精度 66.15%，介於兩者但在 HellaSwag 低於 Q4_K_M，記憶體 42GB，吞吐 18 tok/s。結論：本地/CPU 部署建議優先 Q4_K_M，除非工作量極度偏向代碼生成。評估覆蓋 HumanEval 164 樣本、HellaSwag 100 樣本、BFCL 400 樣本，採用檢查點機制確保可重現性，使用 Neo AI Engineer 建立評估流程。

### 重點
- Qwen 3.6 27B 量化權衡：Q4_K_M 在函數調用上精度不減（63.0%），HumanEval 僅下降 ~5.5 點（50.61% vs 56.10%），卻獲得 1.45 倍吞吐與 48% 記憶體節省
- Q8_0 未展現預期效果：HumanEval 相對 Q4_K_M 僅改善 ~1.8 點（52.44%），卻佔用 14GB 更多記憶體且速度更慢，HellaSwag 反而下滑至 83%
- 評估範疇明確：HumanEval 164 樣本、HellaSwag 100 樣本、BFCL 400 樣本，context window 32768，採檢查點機制，由 Neo AI Engineer 自動化檢查點管理與結果彙整

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1sxzqry/qwen_36_27b_bf16_vs_q4_k_m_vs_q8_0_gguf_evaluation/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1sxzqry/qwen_36_27b_bf16_vs_q4_k_m_vs_q8_0_gguf_evaluation/"> <img alt="Qwen 3.6 27B BF16 vs Q4_K_M vs Q8_0 GGUF evaluation" src="https://preview.redd.it/ncwdmp21bxxg1.jpeg?width=640&amp;crop=smart&amp;auto=webp&amp;s=a5b4caef8b59ccd3aae4c95a42b00f9b14365e5e" title="Qwen 3.6 27B BF16 vs Q4_K_M vs Q8_0 GGUF evaluation" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Evaluated Qwen 3.6 27B across BF16, Q4_K_M, and Q8_0 GGUF quant variants with llama-cpp-python using Neo AI Engineer.</p> <p>Benchmarks used:</p> <ul> <li>HumanEval: code generation</li> <li>HellaSwag: commonsense reasoning</li> <li>BFCL: function calling</li> </ul> <p>Total samples:</p> <ul> <li>HumanEval: 164</li> <li>HellaSwag: 100</li> <li>BFCL: 400</li> </ul> <p>Results:</p> <p><strong>BF16</strong></p> <ul> <li>HumanEval: 56.10% 92/164</li> <li>HellaSwag: 90.00% 90/100</li> <li>BFCL: 63.25% 253/400</li> <li>Avg accuracy: 69.78%</li> <li>Throughput: 15.5 tok/s</li> <li>Peak RAM: 54 GB</li> <li>Model size: 53.8 GB</li> </ul> <p><strong>Q4_K_M</strong></p> <ul> <li>HumanEval: 50.61% 83/164</li> <li>HellaSwag: 86.00% 86/100</li> <li>BFCL: 63.00% 252/400</li> <li>Avg accuracy: 66.54%</li> <li>Throughput: 22.5 tok/s</li> <li>Peak RAM: 28 GB</li> <li>Model size: 16.8 GB</li> </ul> <p><strong>Q8_0</strong></p> <ul> <li>HumanEval: 52.44% 86/164</li> <li>HellaSwag: 83.00% 83/100</li> <li>BFCL: 63.00% 252/400</li> <li>Avg accuracy: 66.15%</li> <li>Throughput: 18.0 tok/s</li> <li>Peak RAM: 42 GB</li> <li>Model size: 28.6 GB</li> </ul> <p><strong>What stood out:</strong></p> <p>Q4_K_M looks like the best practical variant here. It keeps BFCL almost identical to BF16, drops about 5.5 points on HumanEval, and is still only 4 points behind BF16 on HellaSwag.</p> <p>The tradeoff is pretty good:</p> <ul> <li>1.45x faster than BF16</li> <li>48% less peak RAM</li> <li>68.8% smaller model file</li> <li>nearly identical function calling score</li> </ul> <p>Q8_0 was a bit underwhelming in this run. It improved HumanEval over Q4_K_M by ~1.8 points, but used 42 GB RAM vs 28 GB and was slower. It also scored lower than Q4_K_M on HellaSwag in this eval.</p> <p>For local/CPU deployment, I would probably pick Q4_K_M unless the workload is heavily code-generation focused. For maximum quality, BF16 still wins.</p> <p>Evaluation setup:</p> <ul> <li>GGUF via llama-cpp-python</li> <li>n_ctx: 32768</li> <li>checkpointed evaluation</li> <li>HumanEval, HellaSwag, and BFCL all completed</li> <li>BFCL had 400 function calling samples</li> </ul> <p>This evaluation was done using Neo AI Engineer, which built the GGUF eval setup, handled checkpointed runs, and consolidated the benchmark results. I manually reviewed the outcome as well.</p> <p>Complete case study with benchmarking results, approach and code snippets in mentioned in the comments below 👇</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/gvij"> /u/gvij </a> <br /> <span><a href="https://i.redd.it/ncwdmp21bxxg1.jpeg">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1sxzqry/qwen_36_27b_bf16_vs_q4_k_m_vs_q8_0_gguf_evaluation/">[comments]</a></span> </td></tr></table>

</details>