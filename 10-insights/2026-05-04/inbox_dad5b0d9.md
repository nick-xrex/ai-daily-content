---
id: inbox_dad5b0d9
date: 2026-05-04
source_ref: "[[00-inbox/2026-05-04/0819-reddit-localllama-the-first-ai-model-in-egypt-491b]]"
title: "The first AI Model in Egypt 🇪🇬"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t3nh7d/the_first_ai_model_in_egypt/
source: reddit-localllama
published_at: 2026-05-04T16:53:36+00:00
fetched_at: 2026-05-05T08:40:41.420366+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "TokenAI 團隊（由 Assem Sabry 領導）發布 Horus，埃及首個完全自主從零開始訓練的開源語言模型，既提供模型權重（HuggingFace）也開源訓練源代碼（GitHub），促進區域開發者生態。計畫推出 Horus 1.5 Instruct，預期性能較 1.0 提升 5 倍、上下文長度從 8K 擴展至 64K（增 8 倍）、並加入顯著架構改進。同時開發專門的網路安全模型用於漏洞檢測與修復，基於數萬億安全專門數據訓練。整個項目在埃及本土完全開發，標誌中東地區在 AI 基礎模型領域的自主建設加速。"
key_points:
  - "Horus 1.0：埃及首個從零訓練 LLM，4B 參數、8K 上下文；開源模型權重 (HuggingFace) + 完整訓練源代碼 (GitHub)"
  - "Horus 1.5 Instruct 計畫：性能提升 5 倍、上下文擴至 64K（比 1.0 增 8 倍）、重大架構改進"
  - "TokenAI 並行開發網路安全專用模型，用於漏洞檢測與即時修復，基於數萬億安全相關數據；全程埃及本土開發"
tags: [egyptian-ai, open-source, regional-development, cybersecurity]
topics: []
importance: 4
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## The first AI Model in Egypt 🇪🇬

TokenAI 團隊（由 Assem Sabry 領導）發布 Horus，埃及首個完全自主從零開始訓練的開源語言模型，既提供模型權重（HuggingFace）也開源訓練源代碼（GitHub），促進區域開發者生態。計畫推出 Horus 1.5 Instruct，預期性能較 1.0 提升 5 倍、上下文長度從 8K 擴展至 64K（增 8 倍）、並加入顯著架構改進。同時開發專門的網路安全模型用於漏洞檢測與修復，基於數萬億安全專門數據訓練。整個項目在埃及本土完全開發，標誌中東地區在 AI 基礎模型領域的自主建設加速。

### 重點
- Horus 1.0：埃及首個從零訓練 LLM，4B 參數、8K 上下文；開源模型權重 (HuggingFace) + 完整訓練源代碼 (GitHub)
- Horus 1.5 Instruct 計畫：性能提升 5 倍、上下文擴至 64K（比 1.0 增 8 倍）、重大架構改進
- TokenAI 並行開發網路安全專用模型，用於漏洞檢測與即時修復，基於數萬億安全相關數據；全程埃及本土開發

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t3nh7d/the_first_ai_model_in_egypt/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3nh7d/the_first_ai_model_in_egypt/"> <img alt="The first AI Model in Egypt 🇪🇬" src="https://external-preview.redd.it/b3sW-Zrc1oU7OY8C5e_91cmEQMY4TmcVd7CiQ-GBjkA.png?width=140&amp;height=75&amp;auto=webp&amp;s=adfd3b23cde1eb499af20ae82951a13e9809edf4" title="The first AI Model in Egypt 🇪🇬" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Following up on the Horus project — the first fully built-from-scratch language model in Egypt.</p> <p>If this is your first time hearing about Horus: it’s a fully built-from-scratch language model, and it’s open-source.</p> <p><a href="https://preview.redd.it/v0lw20vuh5zg1.jpg?width=3267&amp;format=pjpg&amp;auto=webp&amp;s=10af499b2c5aab925c549a64cd6a6149217c490a">https://preview.redd.it/v0lw20vuh5zg1.jpg?width=3267&amp;format=pjpg&amp;auto=webp&amp;s=10af499b2c5aab925c549a64cd6a6149217c490a</a></p> <p><a href="https://preview.redd.it/3blbewtuh5zg1.jpg?width=1459&amp;format=pjpg&amp;auto=webp&amp;s=fc7ce3c706ba94bc776305f8f172169a69c00818">https://preview.redd.it/3blbewtuh5zg1.jpg?width=1459&amp;format=pjpg&amp;auto=webp&amp;s=fc7ce3c706ba94bc776305f8f172169a69c00818</a></p> <p>Hugging Face repo: <a href="https://huggingface.co/tokenaii/horus">https://huggingface.co/tokenaii/horus</a></p> <p>About a week ago, the source code used to train the model was also released, making it available for developers to explore, use, and build on.</p> <p><a href="https://github.com/tokenaii/horus-1.0">https://github.com/tokenaii/horus-1.0</a></p> <p>This makes Horus the first fully trained-from-scratch LLM in Egypt, developed by Assem Sabry and TokenAI.</p> <p>Today, I’m sharing some early details about the next version: Horus 1.5 Instruct.</p> <p>This new version is expected to be 5x better than Horus 1.0, with a 64K context length, which is 8x larger than the 8K context in Horus 1.0 4B.</p> <p>But it’s not just about scaling — Horus 1.5 comes with major improvements in architecture and overall capability, pushing the model to a completely different level.</p> <p>Also, there are updates about a new cybersecurity model from TokenAI.</p> <p>A specialized model designed to detect vulnerabilities and fix them instantly. It’s planned to be a large-scale model, trained on trillions of highly specialized security-related data, which puts us in front of something extremely powerful.</p> <p>All of this is fully built in Egypt, in the field of AI.</p> <p>TokenAI is starting to seriously shift the AI scene in Egypt and the Arab world, and what we're building is honestly something exceptional.</p> <p>More official announcements are coming soon about the next Horus models </p> <p>bigger, stronger, and significantly more efficient.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/assemsabryy"> /u/assemsabryy </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3nh7d/the_first_ai_model_in_egypt/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3nh7d/the_first_ai_model_in_egypt/">[comments]</a></span> </td></tr></table>

</details>