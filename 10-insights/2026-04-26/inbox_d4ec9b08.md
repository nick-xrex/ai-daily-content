---
id: inbox_d4ec9b08
date: 2026-04-26
source_ref: "[[00-inbox/.../inbox_d4ec9b08]]"
title: "SWE-bench Verified no longer measures frontier coding capabilities"
url: https://openai.com/index/why-we-no-longer-evaluate-swe-bench-verified/
source: hackernews
published_at: 2026-04-26T13:58:13+00:00
fetched_at: 2026-04-28T03:41:48.227903+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 宣布停止使用 SWE-bench Verified 評估前沿模型能力，因為深度審計發現該基準存在兩大致命缺陷。其一，在審計的 27.6% 資料集（模型常失敗的問題）中，發現至少 59.4% 問題的測試案例有缺陷，會錯誤拒絕功能正確的提交；其二，訓練資料污染問題，所有受測的前沿模型都在訓練時見過 SWE-bench 的問題與解答，導致模型能複製原始的人工修補方案或逐字重述問題敘述，過去 6 個月從 74.9% 進步到 80.9% 的提升實際上反映的是訓練暴露程度而非真實工程能力進步。OpenAI 建議業界改用 SWE-bench Pro，並表示正開發新的未污染評估來真正追蹤編碼能力。"
key_points:
  - "測試案例缺陷量化：審計子集中 59.4% 的問題存在會拒絕正確方案的測試瑕疵，導致模型能力被嚴重低估"
  - "訓練污染確認：所有前沿模型都在訓練資料中見過 SWE-bench 問題與解答，能見過的模型在有底層信息支撐下更容易通過指定不足的測試"
  - "進度幻覺：74.9% → 80.9%（6 個月）的改善不再反映真實軟體工程能力提升，而是模型訓練時暴露於基準的程度指標"
tags: [benchmark-contamination, swe-bench, evaluation-integrity, training-leakage, model-assessment]
topics: [foundation_models.gpt]
importance: 5
novelty: 5
insight_quality: 4
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## SWE-bench Verified no longer measures frontier coding capabilities

OpenAI 宣布停止使用 SWE-bench Verified 評估前沿模型能力，因為深度審計發現該基準存在兩大致命缺陷。其一，在審計的 27.6% 資料集（模型常失敗的問題）中，發現至少 59.4% 問題的測試案例有缺陷，會錯誤拒絕功能正確的提交；其二，訓練資料污染問題，所有受測的前沿模型都在訓練時見過 SWE-bench 的問題與解答，導致模型能複製原始的人工修補方案或逐字重述問題敘述，過去 6 個月從 74.9% 進步到 80.9% 的提升實際上反映的是訓練暴露程度而非真實工程能力進步。OpenAI 建議業界改用 SWE-bench Pro，並表示正開發新的未污染評估來真正追蹤編碼能力。

### 重點
- 測試案例缺陷量化：審計子集中 59.4% 的問題存在會拒絕正確方案的測試瑕疵，導致模型能力被嚴重低估
- 訓練污染確認：所有前沿模型都在訓練資料中見過 SWE-bench 問題與解答，能見過的模型在有底層信息支撐下更容易通過指定不足的測試
- 進度幻覺：74.9% → 80.9%（6 個月）的改善不再反映真實軟體工程能力提升，而是模型訓練時暴露於基準的程度指標

**原文：** [hackernews](https://openai.com/index/why-we-no-longer-evaluate-swe-bench-verified/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# SWE-bench Verified no longer measures frontier coding capabilities

</details>