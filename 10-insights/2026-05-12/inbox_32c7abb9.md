---
id: inbox_32c7abb9
date: 2026-05-12
source_ref: "[[00-inbox/2026-05-12/1800-reddit-localllama-examples-add-llama-eval-by-ggerganov-pul-1aba]]"
title: "examples : add llama-eval by ggerganov · Pull Request #21152 · ggml-org/llama.cpp"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tb0uln/examples_add_llamaeval_by_ggerganov_pull_request/
source: reddit-localllama
published_at: 2026-05-12T12:57:10+00:00
fetched_at: 2026-05-12T18:11:04.462054+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llama.cpp 新增 llama-eval 評估工具，支持 AIME、AIME2025、GSM8K、GPQA 等多個標準基準數據集的模型評測。此工具便於本地開發者直接評估與比較不同量化版本（如 Q4 vs Q6）和微調模型的性能表現，無需依賴外部服務或雲端資源，有助於降低評估成本與掌控環境一致性。"
key_points:
  - "llama.cpp 整合 llama-eval 工具，支持 AIME、AIME2025、GSM8K、GPQA 四個標準基準數據集"
  - "可在本地直接評估不同量化版本（Q4、Q6）和微調模型的性能差異，無需外部服務"
  - "開發者完整掌控評測環境，便於模型對比和版本選擇決策"
tags: [llama-cpp, model-evaluation, benchmark, open-source]
topics: []
importance: 3
novelty: 4
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## examples : add llama-eval by ggerganov · Pull Request #21152 · ggml-org/llama.cpp

llama.cpp 新增 llama-eval 評估工具，支持 AIME、AIME2025、GSM8K、GPQA 等多個標準基準數據集的模型評測。此工具便於本地開發者直接評估與比較不同量化版本（如 Q4 vs Q6）和微調模型的性能表現，無需依賴外部服務或雲端資源，有助於降低評估成本與掌控環境一致性。

### 重點
- llama.cpp 整合 llama-eval 工具，支持 AIME、AIME2025、GSM8K、GPQA 四個標準基準數據集
- 可在本地直接評估不同量化版本（Q4、Q6）和微調模型的性能差異，無需外部服務
- 開發者完整掌控評測環境，便於模型對比和版本選擇決策

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tb0uln/examples_add_llamaeval_by_ggerganov_pull_request/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

now you can evaluate your models at home, sounds like a perfect tool to compare quants and finetunes Datasets: AIME, AIME2025, GSM8K, GPQA &#32; submitted by &#32; /u/jacek2023 [link] &#32; [comments]

</details>