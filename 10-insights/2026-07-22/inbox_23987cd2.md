---
id: inbox_23987cd2
date: 2026-07-22
source_ref: "[[00-inbox/.../inbox_23987cd2]]"
title: "Are AI labs pelicanmaxxing?"
url: https://simonwillison.net/2026/Jul/22/are-ai-labs-pelicanmaxxing/#atom-everything
source: simon-willison
published_at: 2026-07-22T23:01:00+00:00
fetched_at: 2026-07-24T02:37:25.968603+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Dylan Castillo 对 Simon Willison 的「AI labs 是否刻意优化 pelicans on bicycles」的非正式基准进行了系统性评估。通过 8 × 6 = 48 个提示 × 3 次重复，测试 GPT-5.6 Terra、Claude Sonnet 5、Gemini 3.5 Flash、Grok 4.5、Qwen 3.7-Max、GLM-5.2、DeepSeek V4 Pro 等 7 个模型。用 GPT-5.6 Luna 和 Gemini 3.1 Flash-Lite 辅助评估，结论为：无证据表明 labs 对该特定场景进行了优化；pelicans、bicycles 或组合均无异常改进，GLM-5.2 效果最接近但仍不显著。"
key_points:
  - "系统方法：8 animals × 6 vehicles × 3 repeats × 7 models = 336 生成样本"
  - "7 个模型对标测试：GPT-5.6 Terra、Claude Sonnet 5、Gemini 3.5 Flash、Grok 4.5、Qwen 3.7-Max、GLM-5.2、DeepSeek V4 Pro"
  - "结论：无证据支持 pelicanmaxxing；GLM-5.2 最接近但效果不显著"
tags: [ai-evals, generative-ai, model-comparison, benchmark]
topics: []
importance: 2
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Are AI labs pelicanmaxxing?

Dylan Castillo 对 Simon Willison 的「AI labs 是否刻意优化 pelicans on bicycles」的非正式基准进行了系统性评估。通过 8 × 6 = 48 个提示 × 3 次重复，测试 GPT-5.6 Terra、Claude Sonnet 5、Gemini 3.5 Flash、Grok 4.5、Qwen 3.7-Max、GLM-5.2、DeepSeek V4 Pro 等 7 个模型。用 GPT-5.6 Luna 和 Gemini 3.1 Flash-Lite 辅助评估，结论为：无证据表明 labs 对该特定场景进行了优化；pelicans、bicycles 或组合均无异常改进，GLM-5.2 效果最接近但仍不显著。

### 重點
- 系统方法：8 animals × 6 vehicles × 3 repeats × 7 models = 336 生成样本
- 7 个模型对标测试：GPT-5.6 Terra、Claude Sonnet 5、Gemini 3.5 Flash、Grok 4.5、Qwen 3.7-Max、GLM-5.2、DeepSeek V4 Pro
- 结论：无证据支持 pelicanmaxxing；GLM-5.2 最接近但效果不显著

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/22/are-ai-labs-pelicanmaxxing/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Are AI labs pelicanmaxxing?

Are AI labs pelicanmaxxing? 
Excellent piece of work by Dylan Castillo, who took a deep-dive into the frequently pondered question of whether the AI labs have been deliberately training models to draw pelicans riding bicycles in response to my deeply unscientific benchmark . 
 I've been randomly spot-checking this in the past by testing models against other animals riding other types of vehicle, but never with anything close to the diligence of Dylan's methodology here. 
 Dylan took 8 animals × 6 vehicles = 48 prompts and ran them three times each through 7 different models ( GPT-5.6 Terra, Claude Sonnet 5, Gemini 3.5 Flash, Grok 4.5, Qwen3.7-Max, GLM-5.2, and DeepSeek V4 Pro). He then used GPT-5.6 Luna and Gemini 3.1 Flash-Lite to help evaluate the results. 
 There's a neat filter view for exploring the results: 
 
 For the models he tested he could find no evidence of pelimaxxing: 
 
 
 The pelicans on bicycles don’t look any better 
 Labs are not better at drawing pelicans 
 Labs are not better at drawing bicycles 
 Labs are not better at drawing pelicans on bicycles, even adjusting for difficulty 
 The pelican-bicycle scenes don’t look memorized [...] 
 
 Pelicans aren’t drawn any better than other animals. Bicycles aren’t drawn any better than other vehicles. And no lab draws the combination better than its pelicans and bicycles already predict. GLM-5.2 comes closest: it has the largest boost on the exact pelican-bicycle cell, and and its first pelican-on-bicycle sample caught my eye. But the effect is small and not significant, so I wouldn’t put too much weight on it. 
 

 Via Hacker News 

 Tags: ai , generative-ai , llms , evals , pelican-riding-a-bicycle

</details>