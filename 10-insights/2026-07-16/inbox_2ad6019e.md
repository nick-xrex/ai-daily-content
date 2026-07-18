---
id: inbox_2ad6019e
date: 2026-07-16
source_ref: "[[00-inbox/.../inbox_2ad6019e]]"
title: "Inkling: Our open-weights model"
url: https://simonwillison.net/2026/Jul/16/inkling/#atom-everything
source: simon-willison
published_at: 2026-07-16T15:35:25+00:00
fetched_at: 2026-07-18T01:40:57.736059+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Mira Murati 的 Thinking Machines Lab 發佈首個開源模型 Inkling，975B 總參數、41B 活躍的混合專家 (MoE) transformer，採用 Apache-2.0 許可。多模態能力，訓練資料 45 trillion tokens（文字、圖像、音頻、視頻）。模型定位非 frontier，而是強大的微調基礎，原生支援 Tinker 平台微調工具，填補美國開源生態空白。後續承諾 Inkling-Small (276B 參數，12B 活躍) 版本，當前正在測試中。與 NVIDIA Nemotron 和 Gemma 4 競爭，代表美國開源生態對中國 DeepSeek/GLM 的回應。作者測試 pelican benchmark：生成 SVG 表現可接受，但多模態描述誤認為鸛鷗而非鵜鶘，顯示視覺理解仍有改進空間。"
key_points:
  - "975B 總參數、41B 活躍的 MoE transformer，Apache-2.0 開源許可，多模態能力"
  - "45 trillion tokens 訓練（文字/圖像/音頻/視頻），Tinker 平台原生微調支援，非 frontier 定位"
  - "Inkling-Small (276B/12B active) 承諾；與 Nemotron、Gemma 4 競爭；代表美國開源生態回應"
tags: [inkling, thinking-machines, open-weights, moe-models, multimodal]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Inkling: Our open-weights model

Mira Murati 的 Thinking Machines Lab 發佈首個開源模型 Inkling，975B 總參數、41B 活躍的混合專家 (MoE) transformer，採用 Apache-2.0 許可。多模態能力，訓練資料 45 trillion tokens（文字、圖像、音頻、視頻）。模型定位非 frontier，而是強大的微調基礎，原生支援 Tinker 平台微調工具，填補美國開源生態空白。後續承諾 Inkling-Small (276B 參數，12B 活躍) 版本，當前正在測試中。與 NVIDIA Nemotron 和 Gemma 4 競爭，代表美國開源生態對中國 DeepSeek/GLM 的回應。作者測試 pelican benchmark：生成 SVG 表現可接受，但多模態描述誤認為鸛鷗而非鵜鶘，顯示視覺理解仍有改進空間。

### 重點
- 975B 總參數、41B 活躍的 MoE transformer，Apache-2.0 開源許可，多模態能力
- 45 trillion tokens 訓練（文字/圖像/音頻/視頻），Tinker 平台原生微調支援，非 frontier 定位
- Inkling-Small (276B/12B active) 承諾；與 Nemotron、Gemma 4 競爭；代表美國開源生態回應

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/16/inkling/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Inkling: Our open-weights model

Inkling: Our open-weights model 
Mira Murati's Thinking Machines Lab just released their first open-weights model. Inkling is "a Mixture-of-Experts transformer with 975B total parameters, 41B active" - an Apache-2.0 licensed multimodal model trained on 45 trillion tokens of text, images, audio and video. 
 They're also promising Inkling-Small, a 276B (12B active) model, but that's still being tested and the weights will be released "once that work is complete". 
 The model card is much shorter than I've come to expect from US AI labs. It links to even shorter Training Data Documentation with almost nothing of interest in it - it's best summarized by these two paragraphs: 
 
 The datasets Thinking Machines Lab uses to develop its AI services includes content that is in the public domain as well as content that may be subject to intellectual property protection. 
 Thinking Machines Lab’s services were developed using publicly available content obtained from the open internet and publicly accessible data repositories. Certain datasets were also obtained from third parties. 
 
 By Thinking Machines' own admission, this is not a frontier model. It's instead intended as a strong base model for fine-tuning using their own Tinker training platform : 
 
 Inkling is not the strongest overall model available today, open or closed. Instead, a combination of qualities makes it a good open-weights base for customization: multimodal capabilities, efficient thinking, and availability on Tinker for fine-tuning. 
 
 There's a lot to like about this release. It's Apache-2.0 licensed, and looks competitive with the open weight models coming out of China - it's good to see the US open weights ecosystem gain a new viable contender to join NVIDIA Nemotron and Gemma 4. 
 Here's its attempt at an SVG pelican riding a bicycle, which I generated using this curl command against the Thinking Machines API: 
 curl " https://tinker.thinkingmachines.dev/services/tinker-prod/oai/api/v1/chat/completions " \
 -H " Authorization: Bearer $TINKER_API_KEY " \
 -H " Content-Type: application/json " \
 -d ' { 
 "model": "thinkingmachines/Inkling", 
 "messages": [ 
 {"role": "user", "content": "Generate an SVG of a pelican riding a bicycle"} 
 ], 
 "stream": false 
 } ' 

 Full response here . 
 
 Since it's a multi-modal model I had it describe its own image (after I rendered it to a JPEG) by sending this JSON: 
 {
 "model" : " thinkingmachines/Inkling " ,
 "messages" : [{
 "role" : " user " ,
 "content" : [
 { "type" : " image_url " , "image_url" : { "url" : " data:image/jpeg;base64,$BASE_64_JPEG " }},
 { "type" : " text " , "text" : " Describe this image in detail " },
 ],
 }],
 "stream" : false 
} 

 Here's the full response . It thought it had drawn a "stork or seagull": 
 
 This is a cheerful, flat-vector cartoon illustration featuring a white bird riding a bicycle across a green landscape. 
 The Bird: The central figure is a stylized white bird—resembling a stork or seagull—with a plump, rounded body. It has a long, prominent orange beak that is slightly open, revealing a black line for the mouth. Its eye is small and black with a tiny white highlight. The bird has black wing and tail feathers with white edges, and thin orange legs ending in black feet that rest on the bicycle's orange pedals. 
 The Bicycle: The bike has a simple black frame with two large wheels featuring black tires, gray inner rims, and black spokes arranged in a cross pattern. The handlebars are black, and there are bright orange pedals attached to a black crank. A white seat is visible behind the bird's body. 
 The Setting: The scene is set against a clear, light blue sky. There are two fluffy white clouds—one on the left side and a smaller one near the bird's head on the right. A bright, solid yellow sun shines in the upper right corner. At the bottom, there are rolling green hills with a smooth, curved top edge where the bicycle rests. 
 The overall style is playful, simple, and colorful, with clean lines and a bright, sunny atmosphere. 
 

 Via Hacker News 

 Tags: ai , generative-ai , llms , training-data , pelican-riding-a-bicycle , llm-release

</details>