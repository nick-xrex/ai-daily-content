---
id: inbox_4cba26b5
date: 2026-06-05
source_ref: "[[00-inbox/2026-06-05/0216-medium-tag-llm-how-the-washington-post-scaled-llms-for-3684]]"
title: "How The Washington Post Scaled LLMs for Taxonomy Classification"
url: https://washpost.engineering/how-the-washington-post-scaled-llms-for-taxonomy-classification-bc390ed8e2fb?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-05T19:07:58+00:00
fetched_at: 2026-06-06T02:22:27.659356+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "華盛頓郵報工程團隊開發了一套 LLM 驅動的分類系統替代商業解決方案，處理約 20,400 個分類法條目（5 個 schema：主題 ~2,100 個、人物/公司/組織/地理 ~18,300 個）。核心問題是規則型系統缺乏透明度和迭代速度，而「樸素的 LLM 提示不適用」於 20,000+ 候選項（文脈溢出、成本爆炸、幻覺產生）。解決方案採用雙管道：(1) 主題管道用精煉的主題嵌入（基於歷史文章的加權平均），避免僅依賴主題名稱；(2) 實體管道先用模糊 n-gram 匹配快速過濾，再透過 LLM 提取提及項，最終 LLM 從合併候選（50–75 項）中選擇。關鍵發現：主題描述無幫助、階層式自上而下遍歷導致誤差級聯、大候選集減損 LLM 判別力。在 1,644 篇手工標註文章上，主題 schema 的 F1 值提升 30 個百分點，去重後達 0.919（+0.266 vs 基線）。"
key_points:
  - "精煉嵌入策略勝過樸素提示：使用歷史文章加權嵌入平均取代主題名稱單獨嵌入，直接改進主題匹配精準度 30 個百分點"
  - "候選集大小限制至 50–75 項對 LLM 判別力至關重要；階層遍歷會級聯誤差，應改用平行管道（主題 + 實體分開）"
  - "模糊 n-gram 過濾 + LLM 聯動遠優於純 LLM 或純統計方法；最終 F1 達 0.919，業務側（廣告定位 & 編輯推薦）認可度高"
tags: [taxonomy-classification, llm-scaling, embedding-optimization, named-entity-recognition, information-retrieval]
topics: []
importance: 4
novelty: 3
insight_quality: 5
insight_type: technique
deep_dive_candidate: true
deep_dive_approved: false
---

## How The Washington Post Scaled LLMs for Taxonomy Classification

華盛頓郵報工程團隊開發了一套 LLM 驅動的分類系統替代商業解決方案，處理約 20,400 個分類法條目（5 個 schema：主題 ~2,100 個、人物/公司/組織/地理 ~18,300 個）。核心問題是規則型系統缺乏透明度和迭代速度，而「樸素的 LLM 提示不適用」於 20,000+ 候選項（文脈溢出、成本爆炸、幻覺產生）。解決方案採用雙管道：(1) 主題管道用精煉的主題嵌入（基於歷史文章的加權平均），避免僅依賴主題名稱；(2) 實體管道先用模糊 n-gram 匹配快速過濾，再透過 LLM 提取提及項，最終 LLM 從合併候選（50–75 項）中選擇。關鍵發現：主題描述無幫助、階層式自上而下遍歷導致誤差級聯、大候選集減損 LLM 判別力。在 1,644 篇手工標註文章上，主題 schema 的 F1 值提升 30 個百分點，去重後達 0.919（+0.266 vs 基線）。

### 重點
- 精煉嵌入策略勝過樸素提示：使用歷史文章加權嵌入平均取代主題名稱單獨嵌入，直接改進主題匹配精準度 30 個百分點
- 候選集大小限制至 50–75 項對 LLM 判別力至關重要；階層遍歷會級聯誤差，應改用平行管道（主題 + 實體分開）
- 模糊 n-gram 過濾 + LLM 聯動遠優於純 LLM 或純統計方法；最終 F1 達 0.919，業務側（廣告定位 & 編輯推薦）認可度高

**原文：** [medium-tag-llm](https://washpost.engineering/how-the-washington-post-scaled-llms-for-taxonomy-classification-bc390ed8e2fb?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A peer-reviewed version of this work will be published at the ACM UMAP 2026 conference industry track. Continue reading on Washington Post Engineering »

</details>