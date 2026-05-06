---
id: inbox_3834db24
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1251-medium-tag-ai-every-llm-just-scored-0-on-this-ai-bench-e093]]"
title: "Every LLM Just Scored 0% on this AI Benchmark"
url: https://medium.com/data-science-in-your-pocket/every-llm-just-scored-0-on-this-ai-benchmark-c4df5e4ee228?source=rss------artificial_intelligence-5
source: medium-tag-ai
published_at: 2026-05-06T12:33:15+00:00
fetched_at: 2026-05-06T12:56:52.359160+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "新基準 ProgramBench 測試 LLM 從零開始獨立構建完整軟體系統的能力（對象：FFmpeg、SQLite、ripgrep 等真實工程），所有現有 LLM 都得 0%。失敗根源：LLM 只擅長「完成模式」和「回憶結構」，缺乏真正的系統級思維；無法在數千個相互依賴函數間保持邏輯一致；context window 和規劃深度有限；依賴訓練數據的部分重疊而非真實理解。對比：SWE-Bench 測試維護任務（修補現有倉庫），造成了一個虛假的進度錯覺，隱藏了「協助編程」和「自主軟體工程」之間的巨大鴻溝。"
key_points:
  - "ProgramBench 0% 成績揭示現有基準（SWE-Bench 等）隱藏的能力缺口：測試維護（修補現存代碼）vs 真正的自主系統設計"
  - "失敗機制：LLM 缺乏跨數千函數的一致性維護、系統級規劃、深度因果推理；只能「完成模式」而非「理解系統」"
  - "測試條件：無互聯網、無現有代碼、無外部幫助——模擬真正的自主軟體工程需求"
tags: [benchmark, llm-limitations, coding-capability, programbench, system-design]
topics: [foundation_models.gpt]
importance: 4
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Every LLM Just Scored 0% on this AI Benchmark

新基準 ProgramBench 測試 LLM 從零開始獨立構建完整軟體系統的能力（對象：FFmpeg、SQLite、ripgrep 等真實工程），所有現有 LLM 都得 0%。失敗根源：LLM 只擅長「完成模式」和「回憶結構」，缺乏真正的系統級思維；無法在數千個相互依賴函數間保持邏輯一致；context window 和規劃深度有限；依賴訓練數據的部分重疊而非真實理解。對比：SWE-Bench 測試維護任務（修補現有倉庫），造成了一個虛假的進度錯覺，隱藏了「協助編程」和「自主軟體工程」之間的巨大鴻溝。

### 重點
- ProgramBench 0% 成績揭示現有基準（SWE-Bench 等）隱藏的能力缺口：測試維護（修補現存代碼）vs 真正的自主系統設計
- 失敗機制：LLM 缺乏跨數千函數的一致性維護、系統級規劃、深度因果推理；只能「完成模式」而非「理解系統」
- 測試條件：無互聯網、無現有代碼、無外部幫助——模擬真正的自主軟體工程需求

**原文：** [medium-tag-ai](https://medium.com/data-science-in-your-pocket/every-llm-just-scored-0-on-this-ai-benchmark-c4df5e4ee228?source=rss------artificial_intelligence-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/data-science-in-your-pocket/every-llm-just-scored-0-on-this-ai-benchmark-c4df5e4ee228?source=rss------artificial_intelligence-5"><img src="https://cdn-images-1.medium.com/max/2600/0*_IscAv3aXF8LNj04" width="5560" /></a></p><p class="medium-feed-snippet">What is ProgramBench?</p><p class="medium-feed-link"><a href="https://medium.com/data-science-in-your-pocket/every-llm-just-scored-0-on-this-ai-benchmark-c4df5e4ee228?source=rss------artificial_intelligence-5">Continue reading on Data Science in Your Pocket »</a></p></div>

</details>