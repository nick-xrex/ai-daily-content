---
id: inbox_f317b60f
date: 2026-06-05
source_ref: "[[00-inbox/2026-06-05/1800-infoq-ai-ml-google-litert-lm-speeds-up-local-inferen-55ec]]"
title: "Google LiteRT-LM Speeds Up Local Inference Up to 2.2x With Gemma 4 Multi-Token Prediction"
url: https://www.infoq.com/news/2026/06/google-litertlm-gemma4/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-06-05T09:00:00+00:00
fetched_at: 2026-06-05T18:09:19.694110+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 的 LiteRT-LM 框架現已新增原生支援 Gemma 4 Multi-Token Prediction（多令牌預測）功能，使本地推理速度最高提升 2.2 倍。這個性能提升來自於多令牌預測技術——在單次推理中預測多個令牌，減少往返次數。框架同時擴展 API 支援範圍，除了原有的 Kotlin 和 C++ 外，新增了 Swift 和 JavaScript APIs，讓更多平台的開發者能部署高效的本地推理。這個更新對離線 AI 應用和邊界設備上的推理特別有意義。

```mermaid
graph LR
    GemmaModel[\"Gemma 4<br/>Multi-Token Prediction\"]
    
    GemmaModel --> LiteRTLM[\"LiteRT-LM Framework\"]
    
    LiteRTLM --> Kotlin[\"Kotlin API\"]
    LiteRTLM --> Cpp[\"C++ API\"]
    LiteRTLM --> Swift[\"Swift API<br/>(New)\"]
    LiteRTLM --> JS[\"JavaScript API<br/>(New)\"]
    
    Kotlin --> Speed1[\"2.2x Faster<br/>Inference\"]
    Cpp --> Speed1
    Swift --> Speed1
    JS --> Speed1
```"
key_points:
  - "Gemma 4 Multi-Token Prediction 將 LiteRT-LM 推理速度提升 2.2 倍"
  - "API 平台擴展：新增 Swift 和 JavaScript，支援 Kotlin、C++、Swift、JavaScript 四大平台"
  - "多令牌預測減少推理往返次數，特別適合邊界設備和離線應用場景"
tags: [local-inference, multi-token-prediction, gemma]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Google LiteRT-LM Speeds Up Local Inference Up to 2.2x With Gemma 4 Multi-Token Prediction

Google 的 LiteRT-LM 框架現已新增原生支援 Gemma 4 Multi-Token Prediction（多令牌預測）功能，使本地推理速度最高提升 2.2 倍。這個性能提升來自於多令牌預測技術——在單次推理中預測多個令牌，減少往返次數。框架同時擴展 API 支援範圍，除了原有的 Kotlin 和 C++ 外，新增了 Swift 和 JavaScript APIs，讓更多平台的開發者能部署高效的本地推理。這個更新對離線 AI 應用和邊界設備上的推理特別有意義。

```mermaid
graph LR
    GemmaModel["Gemma 4<br/>Multi-Token Prediction"]
    
    GemmaModel --> LiteRTLM["LiteRT-LM Framework"]
    
    LiteRTLM --> Kotlin["Kotlin API"]
    LiteRTLM --> Cpp["C++ API"]
    LiteRTLM --> Swift["Swift API<br/>(New)"]
    LiteRTLM --> JS["JavaScript API<br/>(New)"]
    
    Kotlin --> Speed1["2.2x Faster<br/>Inference"]
    Cpp --> Speed1
    Swift --> Speed1
    JS --> Speed1
```

### 重點
- Gemma 4 Multi-Token Prediction 將 LiteRT-LM 推理速度提升 2.2 倍
- API 平台擴展：新增 Swift 和 JavaScript，支援 Kotlin、C++、Swift、JavaScript 四大平台
- 多令牌預測減少推理往返次數，特別適合邊界設備和離線應用場景

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/06/google-litertlm-gemma4/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

LiteRT-LM brings native support for Gemma 4 Multi-Token Prediction (MTP) drafters, enabling up to 2.2x faster inference. The framework is expanding beyond Kotlin and C++ adding support for new Swift and a JavaScript APIs. By Sergio De Simone

</details>