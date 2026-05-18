---
id: inbox_dd2ab048
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_dd2ab048]]"
title: "internlm/Intern-S2-Preview · Hugging Face"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tdrw0s/internlminterns2preview_hugging_face/
source: reddit-localllama
published_at: 2026-05-15T10:09:59+00:00
fetched_at: 2026-05-18T03:56:37.270219+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "InternLM 發佈 Intern-S2-Preview，一個 35B 參數的科學多模態基礎模型，通過「任務規模化」（提升科學任務的難度、多樣性和覆蓋範圍）達到與千億級別 Intern-S1-Pro 相當的性能，基於 Qwen3.5 持續預訓練。模型首次整合小分子結構生成與實值預測模塊，成為開源首個同時具備材料結構生成能力與通用推理能力的模型。引入共享權重的 MTP（多令牌預測）與 KL loss、CoT 壓縮等高效 RL 推理技術，顯著改善智能體任務性能與生成效率。"
key_points:
  - "參數效率突破：35B 參數達千億級性能，基於 Qwen3.5 續訓，科學任務全鏈條規模化"
  - "首次整合小分子結構生成與實值預測模塊，支援材料晶體結構生成"
  - "MTP + CoT 壓縮：多令牌預測搭配 KL loss 及推理壓縮，提升智能體接受率與生成速度"
tags: [task-scaling, scientific-foundation-model, mtp-optimization]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## internlm/Intern-S2-Preview · Hugging Face

InternLM 發佈 Intern-S2-Preview，一個 35B 參數的科學多模態基礎模型，通過「任務規模化」（提升科學任務的難度、多樣性和覆蓋範圍）達到與千億級別 Intern-S1-Pro 相當的性能，基於 Qwen3.5 持續預訓練。模型首次整合小分子結構生成與實值預測模塊，成為開源首個同時具備材料結構生成能力與通用推理能力的模型。引入共享權重的 MTP（多令牌預測）與 KL loss、CoT 壓縮等高效 RL 推理技術，顯著改善智能體任務性能與生成效率。

### 重點
- 參數效率突破：35B 參數達千億級性能，基於 Qwen3.5 續訓，科學任務全鏈條規模化
- 首次整合小分子結構生成與實值預測模塊，支援材料晶體結構生成
- MTP + CoT 壓縮：多令牌預測搭配 KL loss 及推理壓縮，提升智能體接受率與生成速度

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tdrw0s/internlminterns2preview_hugging_face/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# internlm/Intern-S2-Preview · Hugging Face

Introduction We introduce Intern-S2-Preview , an efficient 35B scientific multimodal foundation model. Beyond conventional parameter and data scaling, Intern-S2-Preview explores task scaling : increasing the difficulty, diversity, and coverage of scientific tasks to further unlock model capabilities. By extending professional scientific tasks into a full-chain training pipeline from pre-training to reinforcement learning, Intern-S2-Preview achieves performance comparable to the trillion-scale Intern-S1-Pro on multiple core professional scientific tasks, while using only 35B parameters (continued pretrained from Qwen3.5) . At the same time, it maintains strong general reasoning, multimodal understanding, and agent capabilities. Features Scientific task scaling with full-chain training. Intern-S2-Preview scales hundreds of professional scientific tasks from pre-training to RL, enabling strong performance across multiple specialized domains at only 35B parameters. It further strengthens spatial modeling for small-molecule structures and introduces real-valued prediction modules, making it the first open-source model with both material crystal structure generation capability and strong general capabilities. Enhanced agent capabilities for scientific workflows. Intern-S2-Preview significantly improves agentic abilities over the previous generation, achieving strong results on multiple scientific agent benchmarks. Efficient RL reasoning with MTP and CoT compression. During RL, Intern-S2-Preview adopts shared-weight MTP with KL loss to reduce the mismatch between training and inference behavior, substantially improving MTP accept rate and token generation speed. It also introduces CoT compression techniques to shorten responses while preserving strong reasoning capability, achieving improvements in both performance and efficiency. &#32; submitted by &#32; /u/pmttyji [link] &#32; [comments]

</details>