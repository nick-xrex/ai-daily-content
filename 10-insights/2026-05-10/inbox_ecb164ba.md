---
id: inbox_ecb164ba
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_ecb164ba]]"
title: "Anybody else noticing how good gemma-4-26b-a4b is with one-shotting three.js?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t9cle9/anybody_else_noticing_how_good_gemma426ba4b_is/
source: reddit-localllama
published_at: 2026-05-10T17:07:14+00:00
fetched_at: 2026-05-11T02:22:04.458762+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者分享了 Gemma-4-26B-a4b 模型在 one-shot three.js 程式碼生成中的優異表現。基於 80+ 個 three.js 提示（涉及旋轉網格、精靈效果、屏幕投影等）的自動化測試，模型展現了高度準確的 WebGL 代碼生成能力，包含自動崩潰偵測與存檔功能。"
key_points:
  - "Gemma-4-26B-a4b 在 one-shot three.js 代碼生成上表現良好，80+ 提示測試未見系統性失敗"
tags: [gemma-4, code-generation, three-js, one-shot-learning]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Anybody else noticing how good gemma-4-26b-a4b is with one-shotting three.js?

開發者分享了 Gemma-4-26B-a4b 模型在 one-shot three.js 程式碼生成中的優異表現。基於 80+ 個 three.js 提示（涉及旋轉網格、精靈效果、屏幕投影等）的自動化測試，模型展現了高度準確的 WebGL 代碼生成能力，包含自動崩潰偵測與存檔功能。

### 重點
- Gemma-4-26B-a4b 在 one-shot three.js 代碼生成上表現良好，80+ 提示測試未見系統性失敗

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t9cle9/anybody_else_noticing_how_good_gemma426ba4b_is/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Anybody else noticing how good gemma-4-26b-a4b is with one-shotting three.js?

I wrote up this little python app to cycle through a bunch of prompts like this: Single HTML file using three.js from CDN. A central rotating MeshNormalMaterial torus knot. Place a bright Sprite (AdditiveBlending, soft circular canvas texture) at a position projected to screen, and 6 smaller sprites along the line from that position to screen center, each with different sizes/tints. Update positions each frame. I have a .csv in there file with 80 or so of these little prompts to cycle through - It writes the code into a mock terminal window, detects a crash if needed, and then shows and archives the finished hmtl file. Really fun to mess around with. Link above is to a static demo - github page is here https://github.com/RowanUnderwood/auto_demo_scener No cherry picking here so there may be a few dead ones slipped into the archive :D &#32; submitted by &#32; /u/jacobpederson [link] &#32; [comments]

</details>