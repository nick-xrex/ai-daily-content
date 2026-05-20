---
id: inbox_bbe4e010
date: 2026-05-19
source_ref: "[[00-inbox/2026-05-19/0019-substack-bytebytego-how-snapchat-serves-a-billion-prediction-3092]]"
title: "How Snapchat Serves a Billion Predictions Per Second"
url: https://blog.bytebytego.com/p/how-snapchat-serves-a-billion-predictions
source: substack-bytebytego
published_at: 2026-05-19T15:31:28+00:00
fetched_at: 2026-05-20T00:29:02.915944+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Snapchat 通過內部 Bento 平台在 100 毫秒內完成排序決策，服務 4.77 億日活用戶。ML 架構決定系統的四層選擇：內容推薦（Discover/Spotlight）、廣告競拍、朋友建議、AR 濾鏡推薦。系統採「非對稱請求」設計：一個用戶請求觸發數百至數千個（user, candidate）對的模型評分，再排序返回。為應對這種扇形擴展，架構分為檢索階段（廉價模型快速篩選百萬候選到數千）和排序階段（昂貴模型精細評分）。這是 ML-first 架構的典範——機器學習內植於產品核心，不是疊加的功能層。"
key_points:
  - "Snapchat Bento 平台：100ms 完成四層 ML 決策（內容、廣告、推薦、濾鏡），覆蓋 4.77 億 DAU"
  - "非對稱擴展架構：一個請求 → 數百～千個模型評估 → 排序結果，需要雙階段設計（檢索 + 排序）"
  - "ML-first 不等於「ML 套皮」：每項決策的成本/效益（廣告影響營收、推薦影響留存）直接關聯產品商業目標"
tags: [snapchat, ml-systems, ranking, recommender-systems, bento]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## How Snapchat Serves a Billion Predictions Per Second

Snapchat 通過內部 Bento 平台在 100 毫秒內完成排序決策，服務 4.77 億日活用戶。ML 架構決定系統的四層選擇：內容推薦（Discover/Spotlight）、廣告競拍、朋友建議、AR 濾鏡推薦。系統採「非對稱請求」設計：一個用戶請求觸發數百至數千個（user, candidate）對的模型評分，再排序返回。為應對這種扇形擴展，架構分為檢索階段（廉價模型快速篩選百萬候選到數千）和排序階段（昂貴模型精細評分）。這是 ML-first 架構的典範——機器學習內植於產品核心，不是疊加的功能層。

### 重點
- Snapchat Bento 平台：100ms 完成四層 ML 決策（內容、廣告、推薦、濾鏡），覆蓋 4.77 億 DAU
- 非對稱擴展架構：一個請求 → 數百～千個模型評估 → 排序結果，需要雙階段設計（檢索 + 排序）
- ML-first 不等於「ML 套皮」：每項決策的成本/效益（廣告影響營收、推薦影響留存）直接關聯產品商業目標

**原文：** [substack-bytebytego](https://blog.bytebytego.com/p/how-snapchat-serves-a-billion-predictions)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

For Snap, machine learning is closer to the product itself than a feature on top of it.

</details>