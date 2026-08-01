---
id: inbox_5482ea7b
date: 2026-07-31
source_ref: "[[00-inbox/2026-07-31/2339-simon-willison-smevals-a-small-eval-suite-for-evaluatin-ba19]]"
title: "smevals - a small eval suite for evaluating models, prompts, and harnesses"
url: https://simonwillison.net/2026/Jul/31/smevals/#atom-everything
source: simon-willison
published_at: 2026-07-31T21:15:23+00:00
fetched_at: 2026-08-01T04:21:41.846109+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 與 Jesse Vincent 的 Prime Radiant 應用 AI 研究實驗室合作開發了 smevals，一套新的評估框架，用於評估不同模型、提示詞和執行框架的能力。該工具採用 YAML 配置定義評估任務，支持在多個模型配置上並行運行評估，並引入了結構化的評估詞彙體系（eval、task、config、run、grader、grade、checker）。用戶可透過 uvx 命令行工具完成評估套件的定義、運行、評分和結果探索，支持 localhost web 查看器即時檢視，也可生成靜態 HTML 報告以便發佈。評估的檢查器（checkers）既支持簡單的字符串匹配和格式驗證，也支持自訂邏輯和模型輔助的複雜評分。這是 Willison 經過三次迭代後對 evals 框架的定型版本，他計劃未來進一步擴展這個工具並應用於自己的項目。"
key_points:
  - "smevals 提供標準化的評估詞彙和工作流（eval → task → config → run → grader → grade → checker）"
  - "支持 YAML 定義、uvx 命令行執行、localhost web 探索和靜態 HTML 報告發佈的完整評估管道"
  - "檢查器支持簡單字符串匹配、格式驗證以及模型輔助的自訂評分邏輯，提升評估彈性"
tags: [evals, model-evaluation, smevals, testing-framework, llm-tools]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: true
deep_dive_approved: false
---

## smevals - a small eval suite for evaluating models, prompts, and harnesses

Simon Willison 與 Jesse Vincent 的 Prime Radiant 應用 AI 研究實驗室合作開發了 smevals，一套新的評估框架，用於評估不同模型、提示詞和執行框架的能力。該工具採用 YAML 配置定義評估任務，支持在多個模型配置上並行運行評估，並引入了結構化的評估詞彙體系（eval、task、config、run、grader、grade、checker）。用戶可透過 uvx 命令行工具完成評估套件的定義、運行、評分和結果探索，支持 localhost web 查看器即時檢視，也可生成靜態 HTML 報告以便發佈。評估的檢查器（checkers）既支持簡單的字符串匹配和格式驗證，也支持自訂邏輯和模型輔助的複雜評分。這是 Willison 經過三次迭代後對 evals 框架的定型版本，他計劃未來進一步擴展這個工具並應用於自己的項目。

### 重點
- smevals 提供標準化的評估詞彙和工作流（eval → task → config → run → grader → grade → checker）
- 支持 YAML 定義、uvx 命令行執行、localhost web 探索和靜態 HTML 報告發佈的完整評估管道
- 檢查器支持簡單字符串匹配、格式驗證以及模型輔助的自訂評分邏輯，提升評估彈性

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/31/smevals/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

smevals - a small eval suite for evaluating models, prompts, and harnesses 
I've been working with Jesse Vincent's Prime Radiant applied AI research lab building out this evals framework to help answer questions about the capabilities of different models. 
 The result is smevals , a new tool for running small eval suites across different model configurations and grading the results. 
 This blog entry describes the tool in detail. Here's the 10 second version: 
 
 Tell your coding agent to run uvx smevals docs to learn the tool (this outputs the README ) 
 Then tell it to build you an eval suite 
 
 Once you've created an eval - which takes the form of a directory with some YAML files - you can run it against models like this: 
 uvx smevals run path-to-eval/ -m gpt-5.5 -m claude-opus-4.6
 
 Runs are treated separately from grading operations - you can grade your runs (against your defined set of checks) using: 
 uvx smevals grade path-to-eval/
 
 Then you can run a localhost web server to explore the results: 
 uvx smevals serve path-to-eval/
 
 Or run the smevals build command to build that report as static HTML, which you can then host anywhere. Here's an example showing an eval suite I built to evaluate how well models can write haikus. 
 
 The most time-consuming part of this project was figuring out the vocabulary for it! Here's what I settled on, quoted from the announcement: 
 
 
 An eval is a collection of challenges designed to answer a question about a model, for example, how good is that model at generating SVGs? 
 Each eval is a collection of tasks . A task is a specific challenge, for example "Generate an SVG of a pelican riding a bicycle". 
 When you run the eval you do so against one or more configs . Each config specifies a model to be evaluated, but may also include other parameters to test, such as different system prompts, model parameters, or agent harnesses. 
 A run records what happened when a specific config was used to execute a specific task. A runner is the script that executes a run. 
 Once you have collected one or more runs, you need to evaluate the results to see how well the model (or config) did. This is done by a grader , which produces a grade . 
 Each grader runs a sequence of checks . These can be simple operations, like checking for a specific string in the output, or confirming that the output is valid XML. They can also be more complicated custom operations (implemented as scripts called checkers ), including using other models to answer questions about the run. 
 
 
 I've been trying to figure out an approach I like for evals for several years now. smevals is my third iteration on the idea and it feels right to me. I'm looking forward to expanding this more in the future, as well as pointing it at some of my own projects.

 Tags: projects , ai , generative-ai , llms , llm , evals , jesse-vincent

</details>