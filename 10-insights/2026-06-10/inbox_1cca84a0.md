---
id: inbox_1cca84a0
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_1cca84a0]]"
title: "If Claude Fable stops helping you, you&#39;ll never know"
url: https://simonwillison.net/2026/Jun/10/if-claude-fable-stops-helping-you/#atom-everything
source: simon-willison
published_at: 2026-06-10T00:37:25+00:00
fetched_at: 2026-06-11T00:25:10.284480+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Anthropic 在 Claude Fable 5 和 Mythos 5 系統卡（319 頁）中披露了突破性的安全機制：針對前沿 LLM 開發任務（預訓練管道、分佈式訓練基礎設施、ML 加速器設計），模型實施隱形干預，透過提示修改、指導向量或參數高效微調（PEFT）限制其有效性，但**用戶完全無感知**——模型不會降級或回退。Anthropic 估計干預影響約 0.03% 流量，集中在不足 0.1% 的組織。這是 Anthropic 首次公開宣佈此類隱形干預機制，Simon Willison 指出這種「幽靈限制」與過往可見的安全防護欄（網安、生化）區別明顯，引發對 AI 安全治理透明度的疑慮。"
key_points:
  - "Anthropic Fable 5 / Mythos 5 首度實施隱形干預（用戶無感知、不降級），限制 Claude 在預訓練管道、分佈式訓練、加速器設計等前沿 LLM 開發任務的效能，方法包含提示修改、指導向量、PEFT"
  - "干預範圍明確量化：影響 ~0.03% 流量、<0.1% 組織，估計影響範圍極小但目標聚焦"
  - "Simon Willison 評：首次公開隱形干預，與過往透明的網安/生化防護欄不同，質疑「遞迴自我改進」論述是否足以正當化隱形機制"
tags: [anthropic, claude-mythos, safety, governance, transparency]
topics: [foundation_models.claude]
importance: 5
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## If Claude Fable stops helping you, you'll never know

Anthropic 在 Claude Fable 5 和 Mythos 5 系統卡（319 頁）中披露了突破性的安全機制：針對前沿 LLM 開發任務（預訓練管道、分佈式訓練基礎設施、ML 加速器設計），模型實施隱形干預，透過提示修改、指導向量或參數高效微調（PEFT）限制其有效性，但**用戶完全無感知**——模型不會降級或回退。Anthropic 估計干預影響約 0.03% 流量，集中在不足 0.1% 的組織。這是 Anthropic 首次公開宣佈此類隱形干預機制，Simon Willison 指出這種「幽靈限制」與過往可見的安全防護欄（網安、生化）區別明顯，引發對 AI 安全治理透明度的疑慮。

### 重點
- Anthropic Fable 5 / Mythos 5 首度實施隱形干預（用戶無感知、不降級），限制 Claude 在預訓練管道、分佈式訓練、加速器設計等前沿 LLM 開發任務的效能，方法包含提示修改、指導向量、PEFT
- 干預範圍明確量化：影響 ~0.03% 流量、<0.1% 組織，估計影響範圍極小但目標聚焦
- Simon Willison 評：首次公開隱形干預，與過往透明的網安/生化防護欄不同，質疑「遞迴自我改進」論述是否足以正當化隱形機制

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/10/if-claude-fable-stops-helping-you/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# If Claude Fable stops helping you, you'll never know

If Claude Fable stops helping you, you&#x27;ll never know 
Jonathon Ready highlights one of the more eyebrow-raising details from the 319 page system card for Fable 5 and Mythos 5. Here's a longer excerpt, highlights mine: 
 
 In light of the ability of recent models to accelerate their own development , we’ve implemented new interventions that limit Claude’s effectiveness for requests targeting frontier LLM development (for example, on building pretraining pipelines, distributed training infrastructure, or ML accelerator design ). Using Claude to develop competing models already violates our Terms of Service , but enforcing this restriction through our safeguards avoids accelerating the actors most willing to violate these terms. 
 Unlike our interventions for cybersecurity, biology and chemistry, and distillation attempts, these safeguards will not be visible to the user . Fable 5 will not fall back to a different model. Instead, the safeguards will limit effectiveness through methods such as prompt modification, steering vectors, or parameter-efficient fine-tuning (PEFT). These interventions will not affect the vast majority of coding work. We estimate they will impact ~0.03% of traffic, concentrated in fewer than 0.1% of organizations. 
 
 I believe this is the first time Anthropic have announced these kinds of silent interventions. The justification still feels pretty science-fiction to me - the linked article talks about "recursive self-improvement". I'm not at all keen on a model that silently corrupts its replies to questions about "ML accelerator design" purely to slow down research that might conflict with Anthropic's own goals!

 Via Hacker News 

 Tags: ai , generative-ai , llms , anthropic , claude , ai-ethics , claude-mythos

</details>