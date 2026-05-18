---
id: inbox_a802e0e7
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_a802e0e7]]"
title: "I am not sure if I should be proud or not."
url: https://www.reddit.com/r/LocalLLaMA/comments/1tdn8yp/i_am_not_sure_if_i_should_be_proud_or_not/
source: reddit-localllama
published_at: 2026-05-15T05:52:06+00:00
fetched_at: 2026-05-18T04:00:09.878281+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者在雙 RTX 3090 上成功部署 4 個 Qwen 3.6 35B 本地子智能體 + DeepSeek 協調器的混合架構。每個子智能體上文 131,072 token，4 builder 併行執行後由 4 local reviewer 驗證，最後用雲端 GPT-5.5 進行終級審查。API 月費壓低至 $20（改用 DeepSeek 協調，ChatGPT 亦可 $20/月）。配置透過 opencode.json 公開，展示本地推理 + 雲端驗證的三層成本優化架構。"
key_points:
  - "4 × Qwen 35B (131k ctx) 併行執行，雙 3090 硬體足以支撐，API 成本僅 $20/月（vs 純雲端 >$100+）"
  - "混合層級設計：便宜協調 (DeepSeek Pro) + 本地執行 (Qwen Builder) + 雲端驗證 (GPT-5.5)，兼顧成本、隱私、品質"
  - "opencode 平台支援子智能體自訂 prompt 及多模型混搭，但作者遺失 prompt 詳情——暗示可重複性仍需改進"
tags: [multi-agent, local-inference, hybrid-architecture, cost-optimization, qwen]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## I am not sure if I should be proud or not.

開發者在雙 RTX 3090 上成功部署 4 個 Qwen 3.6 35B 本地子智能體 + DeepSeek 協調器的混合架構。每個子智能體上文 131,072 token，4 builder 併行執行後由 4 local reviewer 驗證，最後用雲端 GPT-5.5 進行終級審查。API 月費壓低至 $20（改用 DeepSeek 協調，ChatGPT 亦可 $20/月）。配置透過 opencode.json 公開，展示本地推理 + 雲端驗證的三層成本優化架構。

### 重點
- 4 × Qwen 35B (131k ctx) 併行執行，雙 3090 硬體足以支撐，API 成本僅 $20/月（vs 純雲端 >$100+）
- 混合層級設計：便宜協調 (DeepSeek Pro) + 本地執行 (Qwen Builder) + 雲端驗證 (GPT-5.5)，兼顧成本、隱私、品質
- opencode 平台支援子智能體自訂 prompt 及多模型混搭，但作者遺失 prompt 詳情——暗示可重複性仍需改進

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tdn8yp/i_am_not_sure_if_i_should_be_proud_or_not/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I am not sure if I should be proud or not.

I managed to get working 4 sub-agents Qwen3.6 35b on dual rtx 3090, I am using deepseek as orchestrator. https://preview.redd.it/biksbgq0n81h1.png?width=783&amp;format=png&amp;auto=webp&amp;s=cf8a4481c1ac439c3283925001c12841b8e6c2e7 They all working locally in parallel!! Each subagent has a max context of 131072, which is &quot;good&quot; for the task it needs to work with. Once the 4 builders the orchestrator is calling 4 local reviewers just to make sure the job was done correctly. https://preview.redd.it/vlirjrcco81h1.png?width=778&amp;format=png&amp;auto=webp&amp;s=fc92810cd1c0922a31f0576812051c4816bfb944 And after everything is passed, the reviewer sub-agent (cloud model will review the whole thing) https://preview.redd.it/mt58vlkzo81h1.png?width=787&amp;format=png&amp;auto=webp&amp;s=4c6b2715e9e695c0c7cda0fd80be2dbe0e9d6a5d With this configuration I managed to have very low usage on APIs (I am now using deepseek for being cheap but $20 to chatgpt is also more than enough). opencode.json (in case anyone is interested) { &quot;$schema&quot;: &quot;https://opencode.ai/config.json&quot;, &quot;plugin&quot;: [ &quot;@mohak34/opencode-notifier@latest&quot; ], &quot;permission&quot;: { &quot;external_directory&quot;: { &quot;/tmp/**&quot;: &quot;allow&quot; } }, &quot;model&quot;: &quot;local/qwen&quot;, &quot;provider&quot;: { &quot;local-ai&quot;: { &quot;npm&quot;: &quot;@ai-sdk/openai-compatible&quot;, &quot;name&quot;: &quot;Local AI&quot;, &quot;options&quot;: { &quot;baseURL&quot;: &quot;http://localai.tailscale.ts.net:8080/v1&quot; }, &quot;models&quot;: { &quot;qwen&quot;: { &quot;name&quot;: &quot;Qwen text local-ai&quot;, &quot;tools&quot;: true, &quot;max_input_tokens&quot;: 131072, &quot;modalities&quot;: { &quot;input&quot;: [ &quot;image&quot;, &quot;text&quot; ], &quot;output&quot;: [ &quot;text&quot; ] } } } }, &quot;deepseek&quot;: { &quot;npm&quot;: &quot;@ai-sdk/openai-compatible&quot;, &quot;name&quot;: &quot;DeepSeek&quot;, &quot;options&quot;: { &quot;baseURL&quot;: &quot;https://api.deepseek.com/v1&quot; }, &quot;models&quot;: { &quot;deepseek-v4-pro&quot;: { &quot;name&quot;: &quot;deepseek-v4-pro&quot;, &quot;tools&quot;: true, &quot;modalities&quot;: { &quot;input&quot;: [ &quot;text&quot; ], &quot;output&quot;: [ &quot;text&quot; ] } }, &quot;deepseek-v4-flash&quot;: { &quot;name&quot;: &quot;deepseek-v4-flash&quot;, &quot;tools&quot;: true, &quot;modalities&quot;: { &quot;input&quot;: [ &quot;text&quot; ], &quot;output&quot;: [ &quot;text&quot; ] } } } } }, &quot;agent&quot;: { &quot;orchestrator&quot;: { &quot;mode&quot;: &quot;primary&quot;, &quot;model&quot;: &quot;deepseek/deepseek-v4-pro&quot;, &quot;temperature&quot;: 0.1, &quot;options&quot;: { &quot;reasoning&quot;: { &quot;effort&quot;: &quot;high&quot; } }, &quot;tools&quot;: { &quot;write&quot;: false, &quot;edit&quot;: false, &quot;bash&quot;: false } }, &quot;orchestrator_dashboards&quot;: { &quot;mode&quot;: &quot;primary&quot;, &quot;model&quot;: &quot;deepseek/deepseek-v4-pro&quot;, &quot;temperature&quot;: 0.1, &quot;options&quot;: { &quot;reasoning&quot;: { &quot;effort&quot;: &quot;high&quot; } }, &quot;tools&quot;: { &quot;write&quot;: false, &quot;edit&quot;: false, &quot;bash&quot;: false } }, &quot;planner&quot;: { &quot;mode&quot;: &quot;subagent&quot;, &quot;model&quot;: &quot;deepseek/deepseek-v4-pro&quot;, &quot;temperature&quot;: 0.1, &quot;options&quot;: { &quot;reasoning&quot;: { &quot;effort&quot;: &quot;high&quot; } }, &quot;tools&quot;: { &quot;write&quot;: false, &quot;edit&quot;: false, &quot;bash&quot;: false } }, &quot;builder&quot;: { &quot;mode&quot;: &quot;subagent&quot;, &quot;model&quot;: &quot;local-ai/qwen&quot;, &quot;permission&quot;: { &quot;edit&quot;: &quot;allow&quot;, &quot;bash&quot;: &quot;allow&quot;, &quot;webfetch&quot;: &quot;allow&quot; }, &quot;temperature&quot;: 0.2, &quot;options&quot;: { &quot;reasoning&quot;: { &quot;effort&quot;: &quot;medium&quot; } }, &quot;tools&quot;: { &quot;write&quot;: true, &quot;edit&quot;: true, &quot;bash&quot;: true } }, &quot;visual_reviewer&quot;: { &quot;mode&quot;: &quot;subagent&quot;, &quot;model&quot;: &quot;openai/gpt-5.5&quot;, &quot;temperature&quot;: 0.1, &quot;options&quot;: { &quot;reasoning&quot;: { &quot;effort&quot;: &quot;low&quot; } }, &quot;tools&quot;: { &quot;write&quot;: false, &quot;edit&quot;: false, &quot;bash&quot;: false } }, &quot;reviewer_local&quot;: { &quot;mode&quot;: &quot;subagent&quot;, &quot;model&quot;: &quot;local-ai/qwen&quot;, &quot;permission&quot;: { &quot;edit&quot;: &quot;allow&quot;, &quot;bash&quot;: &quot;allow&quot;, &quot;webfetch&quot;: &quot;allow&quot; }, &quot;temperature&quot;: 0.1, &quot;options&quot;: { &quot;reasoning&quot;: { &quot;effort&quot;: &quot;max&quot; } }, &quot;tools&quot;: { &quot;write&quot;: false, &quot;edit&quot;: false, &quot;bash&quot;: false } }, &quot;reviewer&quot;: { &quot;mode&quot;: &quot;subagent&quot;, &quot;model&quot;: &quot;openai/gpt-5.5&quot;, &quot;temperature&quot;: 0.1, &quot;options&quot;: { &quot;reasoning&quot;: { &quot;effort&quot;: &quot;medium&quot; } }, &quot;tools&quot;: { &quot;write&quot;: false, &quot;edit&quot;: false, &quot;bash&quot;: false } } } } I remember the subagents had a custom prompt... but for some reason I don't have them. BTW, opencode is great for this. &#32; submitted by &#32; /u/robertpro01 [link] &#32; [comments]

</details>