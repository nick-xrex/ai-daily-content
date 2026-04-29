---
id: inbox_0a5e0674
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0657-reddit-localllama-xiaomimimo-mimo-v2-5-not-pro-architectur-7ed1]]"
title: "XiaomiMiMo MiMo-V2.5 (not pro) - Architecture: Sparse MoE (Mixture of Experts), 310B total / 15B activated parameters"
url: https://www.reddit.com/r/LocalLLaMA/comments/1sy9u3h/xiaomimimo_mimov25_not_pro_architecture_sparse/
source: reddit-localllama
published_at: 2026-04-28T18:27:13+00:00
fetched_at: 2026-04-29T07:23:09.010986+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "小米發布 MiMo-V2.5 模型，採用稀疏 Mixture of Experts（MoE）架構，總參數 310B 但僅 15B 參數在推理時活躍。相比 Pro 版本，此版本可在配置相對普通的硬件上運行，大幅降低本地推理的硬件要求和成本。"
key_points:
  - "稀疏 MoE 設計：310B 總參數但僅 15B 活躍，通過參數選擇性啟用降低推理成本"
  - "硬件親民性：相比 Pro 版本可在「更人性化」配置上運行，擴大可用用戶基數"
tags: [model-release, sparse-moe, local-inference, parameter-efficiency]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## XiaomiMiMo MiMo-V2.5 (not pro) - Architecture: Sparse MoE (Mixture of Experts), 310B total / 15B activated parameters

小米發布 MiMo-V2.5 模型，採用稀疏 Mixture of Experts（MoE）架構，總參數 310B 但僅 15B 參數在推理時活躍。相比 Pro 版本，此版本可在配置相對普通的硬件上運行，大幅降低本地推理的硬件要求和成本。

### 重點
- 稀疏 MoE 設計：310B 總參數但僅 15B 活躍，通過參數選擇性啟用降低推理成本
- 硬件親民性：相比 Pro 版本可在「更人性化」配置上運行，擴大可用用戶基數

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1sy9u3h/xiaomimimo_mimov25_not_pro_architecture_sparse/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p><a href="https://huggingface.co/XiaomiMiMo/MiMo-V2.5">https://huggingface.co/XiaomiMiMo/MiMo-V2.5</a></p> <p>Interesting because unlike its bigger brother it can be run on &quot;more human&quot; configurations </p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/LegacyRemaster"> /u/LegacyRemaster </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1sy9u3h/xiaomimimo_mimov25_not_pro_architecture_sparse/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1sy9u3h/xiaomimimo_mimov25_not_pro_architecture_sparse/">[comments]</a></span>

</details>