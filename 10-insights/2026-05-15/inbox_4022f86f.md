---
id: inbox_4022f86f
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_4022f86f]]"
title: "Evaluated a RAG chatbot and the most expensive model was the worst performer. Notes on what actually moved the needle."
url: https://www.reddit.com/r/LocalLLaMA/comments/1tdusvx/evaluated_a_rag_chatbot_and_the_most_expensive/
source: reddit-localllama
published_at: 2026-05-15T12:24:59+00:00
fetched_at: 2026-05-18T03:59:24.994849+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "生產環境客服 RAG 聊天機器人評估揭示五個關鍵洞察，顛覆常見假設。首先，檢索問題偽裝成 LLM 問題：ChromaDB similarity 閾值 0.7 過嚴導致零檢索，無提示工程能修復；監控實際上下文是根本。其次，LLM judge (Claude Haiku 4.5 via OpenRouter) 遠優於啟發式評估，成本數美分/run，得分基於相關性、準確性、幫助度四個維度。第三，移除 >80% token 重疊的重複文脈減少幻覺。第四，嚴格接地（僅述存在於檢索文件中的事實）交易幫助度換準確性。第五，模型掃描發現 Gemma 4 26B (評分 7.88) 優於 Gemini 3.1 Flash (7.33)，成本僅 $0.000509 vs $0.002420/session。端到端結果：品質 +19%、成本 −79%，兩向優化。"
key_points:
  - "檢索非 LLM 問題：similarity 0.7 過嚴；解法：監控實際傳入 LLM 的上下文，調低閾值至 0.5–0.6，檢索為零時提示工程無效"
  - "評估方法：LLM judge (Claude Haiku 4.5) 評相關性、準確性、幫助度、整體各 0–10 分，成本遠低於人力，勝過 keyword matching"
  - "模型掃描：Gemma 4 26B (7.88 分) > Gemini 3.1 Flash (7.33)，成本降 79% ($0.000509 vs $0.002420/session)，實現帕累托改進"
tags: [rag, evaluation, cost-optimization, llm-judge, model-sweep]
topics: []
importance: 4
novelty: 3
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## Evaluated a RAG chatbot and the most expensive model was the worst performer. Notes on what actually moved the needle.

生產環境客服 RAG 聊天機器人評估揭示五個關鍵洞察，顛覆常見假設。首先，檢索問題偽裝成 LLM 問題：ChromaDB similarity 閾值 0.7 過嚴導致零檢索，無提示工程能修復；監控實際上下文是根本。其次，LLM judge (Claude Haiku 4.5 via OpenRouter) 遠優於啟發式評估，成本數美分/run，得分基於相關性、準確性、幫助度四個維度。第三，移除 >80% token 重疊的重複文脈減少幻覺。第四，嚴格接地（僅述存在於檢索文件中的事實）交易幫助度換準確性。第五，模型掃描發現 Gemma 4 26B (評分 7.88) 優於 Gemini 3.1 Flash (7.33)，成本僅 $0.000509 vs $0.002420/session。端到端結果：品質 +19%、成本 −79%，兩向優化。

### 重點
- 檢索非 LLM 問題：similarity 0.7 過嚴；解法：監控實際傳入 LLM 的上下文，調低閾值至 0.5–0.6，檢索為零時提示工程無效
- 評估方法：LLM judge (Claude Haiku 4.5) 評相關性、準確性、幫助度、整體各 0–10 分，成本遠低於人力，勝過 keyword matching
- 模型掃描：Gemma 4 26B (7.88 分) > Gemini 3.1 Flash (7.33)，成本降 79% ($0.000509 vs $0.002420/session)，實現帕累托改進

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tdusvx/evaluated_a_rag_chatbot_and_the_most_expensive/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Evaluated a RAG chatbot and the most expensive model was the worst performer. Notes on what actually moved the needle.

We had a customer support RAG bot. Standard setup: ChromaDB, system prompt, an LLM doing generation. Nobody had actually measured the response quality. In the name of evaluation, I only had a keyword matching script producing numbers that looked like scores and meant nothing. I went in to fix this properly. Sharing what I found because most of it was not where I expected. 1. Retrieval problems disguise themselves as LLM problems. User asks &quot;hey what do you guys do?&quot; Bot says &quot;I don't have access to specific information about our company's services.&quot; Everyone's first instinct is to tweak the prompt or swap the model. Wrong. The similarity threshold in ChromaDB was set to 0.7 (cosine distance, lower = more similar, so this is actually strict). Casual openers don't produce embeddings close enough to any chunk to pass that filter. Zero docs retrieved. The model was honestly reporting it had nothing. Lesson: always log what context the LLM actually received before blaming generation. If retrieval returns nothing, no amount of prompt engineering fixes it. 2. Heuristic evaluators are worse than no evaluator. Counting keywords and source references gives you a number. That number has no correlation with whether users are being helped. Worse, it gives you false confidence that you are measuring something. Bit the bullet and used an LLM judge (Claude Haiku 4.5 via OpenRouter) scoring relevance, accuracy, helpfulness, and overall on 0-10. Costs a few cents per full run. Cheap insurance. 3. Deduplicate chunks before sending to the model. Two of our turns had three near-identical FAQ chunks in the context window. Added a check for &gt;80% token overlap from the same source file. Cleaner context, fewer tokens, and the agent stopped hallucinating product names on one turn (probably because the noise was gone). 4. Stricter grounding trades helpfulness for accuracy. Added a rule that the agent only states facts present in retrieved docs. Accuracy went up. Helpfulness went down on knowledge-gap turns because the bot started saying &quot;the docs don't specify this, contact support&quot; instead of guessing. This is the right call for a factual support bot but you need to make it consciously. Otherwise users complain the bot got worse even though your scores say it got better. 5. Run a model sweep. The defaults are usually wrong. I was running Gemini 3.1 Flash Lite Preview. Swept 5 models against the same eval harness. Gemma 4 26B scored higher (7.88 vs 7.33) and cost 75% less per session. Mistral Small 3.2 close second. Nova Micro cheapest but terse responses got penalized for not being actionable. The point is not that Gemma is the best model. The point is your production model is probably not on the Pareto frontier and you only find that out by measuring. End to end: quality 6.62 to 7.88 (+19%), cost $0.002420 to $0.000509 per session (−79%). Both directions, same run. This entire evaluation was done using Neo AI Engineer. It built the eval harness, handled checkpointed runs, dealt with timeout and context limit issues, and consolidated results. I reviewed everything manually and made the calls on what to ship. Full walkthrough write up in the comments if anyone wants to replicate it on their own system. 👇 &#32; submitted by &#32; /u/gvij [link] &#32; [comments]

</details>