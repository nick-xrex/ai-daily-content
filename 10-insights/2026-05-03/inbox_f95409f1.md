---
id: inbox_f95409f1
date: 2026-05-03
source_ref: "[[00-inbox/2026-05-03/0131-medium-tag-llm-when-ai-agents-all-think-the-same-thing-0b5c]]"
title: "When AI Agents All Think the Same Thing - Diversity Collapse !"
url: https://osintteam.blog/when-ai-agents-all-think-the-same-thing-diversity-collapse-f057a9acdf33?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-03T00:48:17+00:00
fetched_at: 2026-05-03T01:46:29.685673+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "多個 AI 智能體執行分析時，預期獲得多元視角，但實際結果是同答案的多個變體，這是「多樣性崩潰」現象。三大收斂機制：(1) 共享背景資訊將不同初始提示拉向共同解釋；(2) 相互反饋循環導致異常觀點被多數派『糾正』；(3) LLM 使用重疊訓練數據與相似架構，潛在表示本質相似。使用 Vendi 分數量化多樣性（1=完全相同，N=N 個智能體）。在 OSINT 應用中造成「印證幻覺」——多智能體一致可能源於結構耦合而非獨立推理。防止方案包括顯式測量指標、隔離推理階段、多樣化輸入、將收斂視為警告、採異構架構。"
key_points:
  - "多智能體存在內在收斂機制：共享背景、相互反饋循環、模型結構相似性，導致多樣性自然塌陷"
  - "Vendi 分數量化多樣性（1-N 範圍），可測量多智能體系統的實際獨立性，揭示『一致幻覺』"
  - "防止方案：採異構架構混用不同 LLM、隔離推理階段、顯式測量多樣性指標、將收斂視為系統警告信號"
tags: [multi-agent-systems, diversity-collapse, osint, llm-behavior, system-design]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## When AI Agents All Think the Same Thing - Diversity Collapse !

多個 AI 智能體執行分析時，預期獲得多元視角，但實際結果是同答案的多個變體，這是「多樣性崩潰」現象。三大收斂機制：(1) 共享背景資訊將不同初始提示拉向共同解釋；(2) 相互反饋循環導致異常觀點被多數派『糾正』；(3) LLM 使用重疊訓練數據與相似架構，潛在表示本質相似。使用 Vendi 分數量化多樣性（1=完全相同，N=N 個智能體）。在 OSINT 應用中造成「印證幻覺」——多智能體一致可能源於結構耦合而非獨立推理。防止方案包括顯式測量指標、隔離推理階段、多樣化輸入、將收斂視為警告、採異構架構。

### 重點
- 多智能體存在內在收斂機制：共享背景、相互反饋循環、模型結構相似性，導致多樣性自然塌陷
- Vendi 分數量化多樣性（1-N 範圍），可測量多智能體系統的實際獨立性，揭示『一致幻覺』
- 防止方案：採異構架構混用不同 LLM、隔離推理階段、顯式測量多樣性指標、將收斂視為系統警告信號

**原文：** [medium-tag-llm](https://osintteam.blog/when-ai-agents-all-think-the-same-thing-diversity-collapse-f057a9acdf33?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://osintteam.blog/when-ai-agents-all-think-the-same-thing-diversity-collapse-f057a9acdf33?source=rss------large_language_models-5"><img src="https://cdn-images-1.medium.com/max/1536/1*aX7iu3L6sS5z_GUGjh7hUA.png" width="1536" /></a></p><p class="medium-feed-snippet">You set up 5 AI agents to brainstorm solutions. Different prompts. Different starting conditions. Maybe even different model architectures&#x2026;</p><p class="medium-feed-link"><a href="https://osintteam.blog/when-ai-agents-all-think-the-same-thing-diversity-collapse-f057a9acdf33?source=rss------large_language_models-5">Continue reading on OSINT Team »</a></p></div>

</details>