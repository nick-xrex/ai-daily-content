---
id: inbox_13e23ea1
date: 2026-04-24
source_ref: "[[00-inbox/2026-04-24/youtube/0956-youtube-ai-engineer-what-do-models-still-suck-at-peter-goste-08e2]]"
title: "What Do Models Still Suck At? - Peter Gostev, Arena.ai, BullshitBench"
url: https://www.youtube.com/watch?v=R7A8rX-09Zw
source: youtube-ai-engineer
published_at: 2026-04-24T14:30:06+00:00
fetched_at: 2026-04-27T10:04:57.934302+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Arena.ai 創辦人 Peter Gostev 以數據挑戰「模型線性進步」假設。發布「BullshitBench」（155 題無意義問題）：詢問模型荒謬假設時，大多數模型選擇遷就而非反駁。Claude Sonnet 4.5 等新模型表現好（>80% pushback），但 GPT/Gemini 系列約 50/50，舊版本完全接受。Arena 6.5M 投票數據顯示，雖然平均 dissatisfaction rate 從 17% 改善至 9%，但數學得利最多，**創意寫作、遊戲設計、金融、法律、魔術等領域停滯**——說明基準線上升掩蓋了領域差距。專家分類子任務分析顯示遊戲設計改善微弱，暗示 LLM 對遊戲機制缺乏真實理解。"
key_points:
  - "BullshitBench 發現：Claude 4.5+ 對無意義問題的 pushback 率 >80%，但 GPT-4/Gemini 僅 ~50%；即使高 reasoning 有時反而降低 pushback（原因可能是過度訓練「解決任務」而不是「識別無效問題」）"
  - "Arena dissatisfaction rate 進展：整體從 17% → 9%，但數學領域改善最大（27% → ~10%），創意寫作、金融、法律改善幅度小，遊戲設計幾乎無進展"
  - "隱藏真相：狹窄基準線掩蓋實務能力差距；6.5M 投票數據表明現有模型在專家任務（量化、編碼、遊戲）上的性能改善軌跡不一，部分領域停滯"
tags: [llm-evaluation, benchmark, model-limitations]
topics: [foundation_models.gpt]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## What Do Models Still Suck At? - Peter Gostev, Arena.ai, BullshitBench

Arena.ai 創辦人 Peter Gostev 以數據挑戰「模型線性進步」假設。發布「BullshitBench」（155 題無意義問題）：詢問模型荒謬假設時，大多數模型選擇遷就而非反駁。Claude Sonnet 4.5 等新模型表現好（>80% pushback），但 GPT/Gemini 系列約 50/50，舊版本完全接受。Arena 6.5M 投票數據顯示，雖然平均 dissatisfaction rate 從 17% 改善至 9%，但數學得利最多，**創意寫作、遊戲設計、金融、法律、魔術等領域停滯**——說明基準線上升掩蓋了領域差距。專家分類子任務分析顯示遊戲設計改善微弱，暗示 LLM 對遊戲機制缺乏真實理解。

### 重點
- BullshitBench 發現：Claude 4.5+ 對無意義問題的 pushback 率 >80%，但 GPT-4/Gemini 僅 ~50%；即使高 reasoning 有時反而降低 pushback（原因可能是過度訓練「解決任務」而不是「識別無效問題」）
- Arena dissatisfaction rate 進展：整體從 17% → 9%，但數學領域改善最大（27% → ~10%），創意寫作、金融、法律改善幅度小，遊戲設計幾乎無進展
- 隱藏真相：狹窄基準線掩蓋實務能力差距；6.5M 投票數據表明現有模型在專家任務（量化、編碼、遊戲）上的性能改善軌跡不一，部分領域停滯

**原文：** [youtube-ai-engineer](https://www.youtube.com/watch?v=R7A8rX-09Zw)