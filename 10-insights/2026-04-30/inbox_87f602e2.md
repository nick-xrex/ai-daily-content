---
id: inbox_87f602e2
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-localllama-deepseek-released-thinking-with-visual-p-f190]]"
title: "DeepSeek released &#39;Thinking-with-Visual-Primitives&#39; framework"
url: https://www.reddit.com/r/LocalLLaMA/comments/1szwi1d/deepseek_released_thinkingwithvisualprimitives/
source: reddit-localllama
published_at: 2026-04-30T13:43:54+00:00
fetched_at: 2026-05-01T13:30:13.947306+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "DeepSeek 與北京大學、清華大學合作發布「Thinking with Visual Primitives」多模態推理框架。核心創新：將坐標點與邊界框等空間標記提升為「思維最小單位」，直接穿插於鏈式思考過程，使模型在推理時能「指向」影像內特定位置。開源倉庫已發佈但隨後被移除。該框架無效能基準數據在貼文中呈現。"
key_points:
  - "坐標點、邊界框融入 CoT 推理鏈，作為多模態「思維單位」，而非純文字推理"
  - "模型能在視覺推理過程中顯式指涉影像區域，提升空間推理透明度與可解釋性"
  - "開源倉庫隨後被移除，實際應用可達性受限"
tags: [deepseek, multimodal-reasoning, visual-primitives, chain-of-thought]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## DeepSeek released 'Thinking-with-Visual-Primitives' framework

DeepSeek 與北京大學、清華大學合作發布「Thinking with Visual Primitives」多模態推理框架。核心創新：將坐標點與邊界框等空間標記提升為「思維最小單位」，直接穿插於鏈式思考過程，使模型在推理時能「指向」影像內特定位置。開源倉庫已發佈但隨後被移除。該框架無效能基準數據在貼文中呈現。

### 重點
- 坐標點、邊界框融入 CoT 推理鏈，作為多模態「思維單位」，而非純文字推理
- 模型能在視覺推理過程中顯式指涉影像區域，提升空間推理透明度與可解釋性
- 開源倉庫隨後被移除，實際應用可達性受限

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1szwi1d/deepseek_released_thinkingwithvisualprimitives/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1szwi1d/deepseek_released_thinkingwithvisualprimitives/"> <img alt="DeepSeek released 'Thinking-with-Visual-Primitives' framework" src="https://preview.redd.it/47r9qee44cyg1.png?width=140&amp;height=45&amp;auto=webp&amp;s=af5a4968d1ae7052f67d020d912d471f559c5123" title="DeepSeek released 'Thinking-with-Visual-Primitives' framework" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p><a href="https://preview.redd.it/47r9qee44cyg1.png?width=1450&amp;format=png&amp;auto=webp&amp;s=0d6f9687115be6ff96d0a194d95232ac0413a7e9">https://preview.redd.it/47r9qee44cyg1.png?width=1450&amp;format=png&amp;auto=webp&amp;s=0d6f9687115be6ff96d0a194d95232ac0413a7e9</a></p> <p>DeepSeek, in collaboration with Peking University and Tsinghua University, has released the paper &quot;Thinking with Visual Primitives&quot; along with its open-source repository, introducing a new multimodal reasoning framework. The core approach of this framework is to elevate spatial tokens—specifically coordinate points and bounding boxes—into the &quot;minimal units of thought&quot; within the model's chain-of-thought. These are directly interleaved during the reasoning process, enabling the model to &quot;point&quot; to specific locations within an image while it &quot;thinks.&quot;</p> <p><a href="https://github.com/deepseek-ai/Thinking-with-Visual-Primitives">https://github.com/deepseek-ai/Thinking-with-Visual-Primitives</a></p> <p><a href="https://preview.redd.it/lt5qu53g0cyg1.png?width=1844&amp;format=png&amp;auto=webp&amp;s=5d6f0a8de6481035faa22c9d57873c51ca97b1fb">https://preview.redd.it/lt5qu53g0cyg1.png?width=1844&amp;format=png&amp;auto=webp&amp;s=5d6f0a8de6481035faa22c9d57873c51ca97b1fb</a></p> <p><strong>notice: deepseek removed the repo</strong></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/External_Mood4719"> /u/External_Mood4719 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1szwi1d/deepseek_released_thinkingwithvisualprimitives/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1szwi1d/deepseek_released_thinkingwithvisualprimitives/">[comments]</a></span> </td></tr></table>

</details>