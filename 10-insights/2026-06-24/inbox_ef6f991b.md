---
id: inbox_ef6f991b
date: 2026-06-24
source_ref: "[[00-inbox/2026-06-24/2201-medium-tag-claude-pare-de-pedir-slides-pra-ia-o-truque-pra-7b17]]"
title: "Pare de pedir “slides” pra IA: o truque pra apresentações profissionais (de graça)"
url: https://medium.com/@jonathancotting/pare-de-pedir-slides-pra-ia-o-truque-pra-apresenta%C3%A7%C3%B5es-profissionais-de-gra%C3%A7a-e80e3e5abeec?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-06-24T21:05:01+00:00
fetched_at: 2026-06-24T22:13:59.139103+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者Jonathan Cotting论述AI生成演示文稿的质量问题与解决方案。核心洞察：PowerPoint/Google Slides为人工编辑优化而非AI输出优化，导致生成结果呆板如「学生作业」。LLM擅长代码生成，故改用HTML+CSS为输出格式能大幅提升专业度。三步工作流：(1)要求输出「HTML+CSS」而非「演示文稿」以激发LLM代码能力；(2)收集设计参考（aura.build或motionsites.ai）以指导样式；(3)在Prompt中明确要求「内联SVG动画」实现幻灯片动态化。不同AI平台Token消耗差异显著（Claude倾向最大输出，ChatGPT最小化Token），Gemini提供不同接口质量差异。"
key_points:
  - "PowerPoint/Slides非AI友好格式，改请求「HTML+CSS」输出可激发LLM代码优化能力，直接对标设计系统"
  - "设计参考关键：从aura.build、motionsites.ai收集模板CSS，在Prompt中明确「follow this design system」指令提高一致性"
  - "内联SVG动画指令（\"Include inline SVG animations to enrich each slide\"）可将静态幻灯片转为动态专业演示，完全免费可行"
tags: [presentation-design, prompt-engineering, html-css-generation, svg-animation]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 5
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Pare de pedir “slides” pra IA: o truque pra apresentações profissionais (de graça)

作者Jonathan Cotting论述AI生成演示文稿的质量问题与解决方案。核心洞察：PowerPoint/Google Slides为人工编辑优化而非AI输出优化，导致生成结果呆板如「学生作业」。LLM擅长代码生成，故改用HTML+CSS为输出格式能大幅提升专业度。三步工作流：(1)要求输出「HTML+CSS」而非「演示文稿」以激发LLM代码能力；(2)收集设计参考（aura.build或motionsites.ai）以指导样式；(3)在Prompt中明确要求「内联SVG动画」实现幻灯片动态化。不同AI平台Token消耗差异显著（Claude倾向最大输出，ChatGPT最小化Token），Gemini提供不同接口质量差异。

### 重點
- PowerPoint/Slides非AI友好格式，改请求「HTML+CSS」输出可激发LLM代码优化能力，直接对标设计系统
- 设计参考关键：从aura.build、motionsites.ai收集模板CSS，在Prompt中明确「follow this design system」指令提高一致性
- 内联SVG动画指令（"Include inline SVG animations to enrich each slide"）可将静态幻灯片转为动态专业演示，完全免费可行

**原文：** [medium-tag-claude](https://medium.com/@jonathancotting/pare-de-pedir-slides-pra-ia-o-truque-pra-apresenta%C3%A7%C3%B5es-profissionais-de-gra%C3%A7a-e80e3e5abeec?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Por que a IA gera slides feios &#x2014; e o ajuste simples de workflow (HTML + CSS + refer&#xea;ncias) que leva o resultado a n&#xed;vel profissional, sem&#x2026; Continue reading on Medium »

</details>