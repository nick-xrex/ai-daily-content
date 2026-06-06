---
id: inbox_a87a480e
date: 2026-06-05
source_ref: "[[00-inbox/2026-06-05/0216-medium-tag-llm-thousand-token-wood-emergent-market-dram-10f7]]"
title: "Thousand Token Wood: emergent market drama from 3-billion-parameter agents"
url: https://medium.com/@LesterLeong/thousand-token-wood-emergent-market-drama-from-3-billion-parameter-agents-22545d5982bf?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-05T22:11:51+00:00
fetched_at: 2026-06-06T02:22:27.622769+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Lester Leong 在 Build Small Hackathon（2026年6月）打造了一個實時多代理經濟模擬系統，使用 Qwen2.5-3B-Instruct 模型驅動五個森林生物角色，展示小模型在推理任務中的應用。關鍵發現是「小模型本質上是可靠的格式生成器，但推理能力不穩定」——不是透過升級到大模型，而是透過結構化提示（structured prompting）和明確角色定義改進推理。系統經歷初期的交易失敗（因為資源過多導致交易誘因消失），後來引入飲食多樣性限制、易腐爛商品和燃料危機機制後，產生真實的經濟互動。引人注目的案例：當謠言觸發銀行擠兌時，代理自然地清算資產，蜂蜜價格從 10 崩跌至 3 pebbles。架構採用 vLLM 服務、Gradio 界面和 Modal 部署。"
key_points:
  - "小模型（Qwen2.5-3B）透過結構化提示和角色設計可達成多代理經濟模擬，無需升級至大模型；關鍵是工程設計而非規模"
  - "設計稀缺性（飲食限制、商品易腐爛、燃料危機）是驅動有意義交易的必要條件，克服資源過剩導致的市場失敗"
  - "系統實現「Wood Legend」功能，允許玩家注入歷史市場衝擊（如鬱金香狂熱、銀行擠兌），代理自然地應對，產生完全湧現的行為"
tags: [small-models, multi-agent-simulation, emergent-behavior, structured-prompting, qwen2.5]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Thousand Token Wood: emergent market drama from 3-billion-parameter agents

Lester Leong 在 Build Small Hackathon（2026年6月）打造了一個實時多代理經濟模擬系統，使用 Qwen2.5-3B-Instruct 模型驅動五個森林生物角色，展示小模型在推理任務中的應用。關鍵發現是「小模型本質上是可靠的格式生成器，但推理能力不穩定」——不是透過升級到大模型，而是透過結構化提示（structured prompting）和明確角色定義改進推理。系統經歷初期的交易失敗（因為資源過多導致交易誘因消失），後來引入飲食多樣性限制、易腐爛商品和燃料危機機制後，產生真實的經濟互動。引人注目的案例：當謠言觸發銀行擠兌時，代理自然地清算資產，蜂蜜價格從 10 崩跌至 3 pebbles。架構採用 vLLM 服務、Gradio 界面和 Modal 部署。

### 重點
- 小模型（Qwen2.5-3B）透過結構化提示和角色設計可達成多代理經濟模擬，無需升級至大模型；關鍵是工程設計而非規模
- 設計稀缺性（飲食限制、商品易腐爛、燃料危機）是驅動有意義交易的必要條件，克服資源過剩導致的市場失敗
- 系統實現「Wood Legend」功能，允許玩家注入歷史市場衝擊（如鬱金香狂熱、銀行擠兌），代理自然地應對，產生完全湧現的行為

**原文：** [medium-tag-llm](https://medium.com/@LesterLeong/thousand-token-wood-emergent-market-drama-from-3-billion-parameter-agents-22545d5982bf?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Field notes from the Build Small Hackathon, June 2026. Continue reading on Medium »

</details>