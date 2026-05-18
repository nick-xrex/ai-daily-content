---
id: inbox_08ea8626
date: 2026-05-12
source_ref: "[[00-inbox/2026-05-12/1800-reddit-localllama-models-and-quants-quality-test-results-t-de7d]]"
title: "Models and Quants quality test results - the chessboard svg (Qwen3.6 27B/35B-A3B/Zaya1)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tax6hj/models_and_quants_quality_test_results_the/
source: reddit-localllama
published_at: 2026-05-12T10:11:08+00:00
fetched_at: 2026-05-12T18:12:25.032958+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶以「國際象棋棋盤 SVG 生成」任務評測 Qwen3.6、Zaya1、HY3 及多個開源衍生模型的輸出品質。Qwen3.6 35B-A3B Q4 幾乎完美但多 2 個棋子，ZAYA1 8B 完美但缺行列標記且本地推理陷入循環，Qwen3.6 27B Q6 很好但 Q3.5 失效，GRM 2.6 Plus Q4K_M 優秀，Qwopus 35B-A3B 出現棋盤錯誤。反映了不同模型在相同 prompt 上表現差異極大，同一模型不同量化版本品質差異也大（Q5K_S 正確但 Q5K_S 衍生品完全錯誤）。"
key_points:
  - "Qwen3.6 35B-A3B Q4 與 ZAYA1 8B 都接近完美，但細節差異（棋子數、標記缺失）影響可用性"
  - "同一模型不同量化版本品質不一致（Q4K_M 好但 Q3K_M 失效），高 bit 未必優於低 bit"
  - "衍生模型差異大：GRM Q4 可用但 Q3 失效，Qwopus 完全出錯，反映量化和微調互動複雜"
tags: [model-evaluation, quantization-quality, qwen3.6, svg-generation]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Models and Quants quality test results - the chessboard svg (Qwen3.6 27B/35B-A3B/Zaya1)

用戶以「國際象棋棋盤 SVG 生成」任務評測 Qwen3.6、Zaya1、HY3 及多個開源衍生模型的輸出品質。Qwen3.6 35B-A3B Q4 幾乎完美但多 2 個棋子，ZAYA1 8B 完美但缺行列標記且本地推理陷入循環，Qwen3.6 27B Q6 很好但 Q3.5 失效，GRM 2.6 Plus Q4K_M 優秀，Qwopus 35B-A3B 出現棋盤錯誤。反映了不同模型在相同 prompt 上表現差異極大，同一模型不同量化版本品質差異也大（Q5K_S 正確但 Q5K_S 衍生品完全錯誤）。

### 重點
- Qwen3.6 35B-A3B Q4 與 ZAYA1 8B 都接近完美，但細節差異（棋子數、標記缺失）影響可用性
- 同一模型不同量化版本品質不一致（Q4K_M 好但 Q3K_M 失效），高 bit 未必優於低 bit
- 衍生模型差異大：GRM Q4 可用但 Q3 失效，Qwopus 完全出錯，反映量化和微調互動複雜

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tax6hj/models_and_quants_quality_test_results_the/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

According to this. I run several more tests to cover more models and quants. https://www.reddit.com/r/LocalLLaMA/comments/1t53dhp/quality_comparison_between_qwen_36_27b/ Qwen3.6 35B-A3B MLX oQ4. 2 extra pawns. (oMLX - local) Qwen 3.6 35B-A3B MLX oQ4's output is almost perfect. With title, last move label, row and col. But the 2 cursors, one show starting point and the other show end point (red triangles), are a bit confusing at first glance. But 2 extra pawns. ZAYA1 8B - Perfect but without a-h, 1-8 row/column mark (Zaya Cloud) ZAYA1 8B is open weight. I used MLX-LM to run it with this PR , but no luck. The 8 bits model kept reasoning in a loop without producing any svg. I don't think the local inference engine is ready yet. Since the model needs RSA technique to perform. So I posted the result from zaya cloud's playground - assuming it is FP16 version of it. If somehow local inference engine can produce the same answer, we will have a VERY promising model to run in our tiny computer. The whole process of running 8 bits quant in my computer take less than 12GB of memory. Qwen3.6 27B MLX oQ6. Very good (oMLX - local) no row/no column marks MLX-oQ 6 bit quant of 27B delivered good and correct answer, but no luck pushing to 3.5 bits. Qwen3.6 27B MLX oQ3.5e, Not so good. (oMLX - local) HY3 Preview 295B A21B - Perfect but no line. no row and no column. (Open Router) HY3's 295B is not gonna cut it on my machine. So the result is from the cloud. Now we're entering the weird territory - using those thousand derivatives found floating in the hugging face. I'll be use ones from Jackrong, OrionLLM and DavidAU since all of them published some kind of benchmarks and promise good results. GRM 2.6 Plus Q4K_M - a OrionLLM's derivative of Qwen3.6 27B - a correct one and looks really good. GRM 2.6 Plus Q3K_M - a OrionLLM's derivative of Qwen3.6 27B - 3 bits was not gonna cut it. qwen3.6-27b-neo-code-di-imatrix-max@iq4_nl - This 4 bits quant is good. qwen3.6-27b-neo-code-di-imatrix-max@q5k_s - However its 5 bits counterpart was totally wrong. It doesn't mean that higher bit quant will always perform better than the lower bit ones. Qwopus 35B-A3B-v1 Jackrong's Q4K_S - the board is wrong and the word game ended came out of nowhere. GRM 2.6 Opus 3 bit Q3K_M, correct but the visual was degraded. The smallest 27B quant that somehow works. &#32; submitted by &#32; /u/Beamsters [link] &#32; [comments]

</details>