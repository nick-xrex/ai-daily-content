---
id: inbox_d828877d
date: 2026-05-27
source_ref: "[[00-inbox/2026-05-27/2345-medium-tag-llm-a-practical-guide-to-evaluating-multi-tu-4860]]"
title: "A Practical Guide to Evaluating Multi-Turn Agent Trajectories"
url: https://medium.com/google-cloud/a-practical-guide-to-evaluating-multi-turn-agent-trajectories-bc21042dbac8?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-27T17:33:04+00:00
fetched_at: 2026-05-27T23:57:22.632652+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "提出評估多轉多步智慧體系統的軌跡級框架，超越單筆回應評分。論點：agent 執行 k 步時，成功機率是各步可靠度的乘積；每步 95% 可靠度下，5 步時整體成功率跌至 77%、10 步降至 59%（複合衰減）。單轉演示高分不等於多轉實戰成功；需評估完整軌跡（每筆 prompt、思考、tool call、狀態變化）。文章推薦追蹤成功率、工具呼叫失敗率、目標達成時間等指標，並警告公開基準（GAIA、SWE-bench）可能被遊戲化而無法反映真實性能。"
key_points:
  - "複合衰減法則：k 步 agent 成功率 = 各步可靠度乘積；95% 可靠度下 10 步→59% 整體成功率，解釋多轉失敗快速累積"
  - "單轉 demo 不可預測多轉實戰：一次失敗可致 agent 卡住或崩潰；需軌跡級評估而非終點回應評分"
  - "客製化評估軌跡優於公開基準：GAIA、SWE-bench 可被遊戲化；應追蹤成功率、工具失敗率、達成時間等客製指標"
tags: [agent-evaluation, trajectory-level, multi-turn-systems, agentic-ai]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## A Practical Guide to Evaluating Multi-Turn Agent Trajectories

提出評估多轉多步智慧體系統的軌跡級框架，超越單筆回應評分。論點：agent 執行 k 步時，成功機率是各步可靠度的乘積；每步 95% 可靠度下，5 步時整體成功率跌至 77%、10 步降至 59%（複合衰減）。單轉演示高分不等於多轉實戰成功；需評估完整軌跡（每筆 prompt、思考、tool call、狀態變化）。文章推薦追蹤成功率、工具呼叫失敗率、目標達成時間等指標，並警告公開基準（GAIA、SWE-bench）可能被遊戲化而無法反映真實性能。

### 重點
- 複合衰減法則：k 步 agent 成功率 = 各步可靠度乘積；95% 可靠度下 10 步→59% 整體成功率，解釋多轉失敗快速累積
- 單轉 demo 不可預測多轉實戰：一次失敗可致 agent 卡住或崩潰；需軌跡級評估而非終點回應評分
- 客製化評估軌跡優於公開基準：GAIA、SWE-bench 可被遊戲化；應追蹤成功率、工具失敗率、達成時間等客製指標

**原文：** [medium-tag-llm](https://medium.com/google-cloud/a-practical-guide-to-evaluating-multi-turn-agent-trajectories-bc21042dbac8?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Would you let an AI agent run in your terminal for hours, executing hundreds of tools, without being able to see what it is doing under&#x2026; Continue reading on Google Cloud - Community »

</details>