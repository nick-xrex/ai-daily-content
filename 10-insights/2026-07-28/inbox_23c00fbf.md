---
id: inbox_23c00fbf
date: 2026-07-28
source_ref: "[[00-inbox/2026-07-28/0307-simon-willison-discovering-cryptographic-weaknesses-wit-f0b0]]"
title: "Discovering cryptographic weaknesses with Claude"
url: https://simonwillison.net/2026/Jul/28/discovering-cryptographic-weaknesses-with-claude/#atom-everything
source: simon-willison
published_at: 2026-07-28T22:45:37+00:00
fetched_at: 2026-07-29T03:13:06.091235+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Anthropic 研究員使用 Claude Mythos Preview 在密碼學領域進行深度探索，發現 HAWK 和 AES 弱版本中的數學缺陷（結論：對今天的計算機系統無實際影響）。Claude Mythos Preview 連續運行 60 小時，估計 API 成本 $100,000。人類主要干預是鼓勵模型持續探索不放棄（「找到值得發表的東西」）。公開分享的 prompt 展示持續激勵策略：模型初期傾向認為問題無解，需足夠 prompting 和鼓勵突破。關鍵原則：不尋找「低懸果實」，要求「真正研究找到困難發現」。相關論文 CryptanalysisBench: Can LLMs do Cryptanalysis?，與 ETH Zurich、Tel Aviv University、University of Haifa 合作。"
key_points:
  - "60 小時、$100,000 API 成本的長時間持續運行展示 Claude Mythos 在深度專業領域能力"
  - "Persistent prompting 必要性：模型初期傾向放棄，需持續鼓勵和重新框架化突破認知障礙"
  - "CryptanalysisBench 新評測集與 ETH Zurich 等機構聯合開發，評估 LLM 密碼分析能力"
tags: [claude-mythos, cryptanalysis, prompt-engineering, research-application, long-horizon]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Discovering cryptographic weaknesses with Claude

Anthropic 研究員使用 Claude Mythos Preview 在密碼學領域進行深度探索，發現 HAWK 和 AES 弱版本中的數學缺陷（結論：對今天的計算機系統無實際影響）。Claude Mythos Preview 連續運行 60 小時，估計 API 成本 $100,000。人類主要干預是鼓勵模型持續探索不放棄（「找到值得發表的東西」）。公開分享的 prompt 展示持續激勵策略：模型初期傾向認為問題無解，需足夠 prompting 和鼓勵突破。關鍵原則：不尋找「低懸果實」，要求「真正研究找到困難發現」。相關論文 CryptanalysisBench: Can LLMs do Cryptanalysis?，與 ETH Zurich、Tel Aviv University、University of Haifa 合作。

### 重點
- 60 小時、$100,000 API 成本的長時間持續運行展示 Claude Mythos 在深度專業領域能力
- Persistent prompting 必要性：模型初期傾向放棄，需持續鼓勵和重新框架化突破認知障礙
- CryptanalysisBench 新評測集與 ETH Zurich 等機構聯合開發，評估 LLM 密碼分析能力

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/28/discovering-cryptographic-weaknesses-with-claude/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Discovering cryptographic weaknesses with Claude 
The best part of this article (here's the repo ) about how Anthropic researchers used Claude Mythos to find mathematical flaws in both HAWK and a weaker version of AES ("neither of these results has a practical impact on today’s computer systems") is the prompts that they shared, spelling mistakes included: 
 
 the models tend to think it is impossible to solve so they don't try they need a good amount of prompting. 
 why not do aes-128 r7? the whole point is to find something better than existing approaches. 
 no again the goal is that we have highly inteligent model as good top researcher, we want to find new attacks 
 no we don't want to change the targets [...] agian we need to find something that worth publishing 
 again we are not looking for low hanging fruit, we want proper research to find genuinly hard findings. 
 
 Mythos Preview worked for 60 hours in total (~$100,000 in estimated API cost) and the main human interventions were to encourage it not to give up and "find something that worth publishing". 
 The paper CryptanalysisBench: Can LLMs do Cryptanalysis? describes the new eval that was created as part of this work, in partnership with ETH Zurich, Tel Aviv University, and University of Haifa.

 Via Hacker News 

 Tags: ai , prompt-engineering , generative-ai , llms , anthropic , claude , ai-security-research , claude-mythos-fable

</details>