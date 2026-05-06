---
id: inbox_2af149a4
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_2af149a4]]"
title: "Google Chrome silently installs a 4 GB AI model on your device without consent"
url: https://www.thatprivacyguy.com/blog/chrome-silent-nano-install/
source: hackernews
published_at: 2026-05-05T07:34:55+00:00
fetched_at: 2026-05-06T13:35:49.839859+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google Chrome 在用戶無明確同意的情況下，自動下載並安裝 4GB 的 Gemini Nano AI 模型（OptGuideOnDeviceModel/weights.bin），用於啟用「幫我寫作」和詐騙檢測等功能。安裝全程耗時約 14 分鐘，僅需裝置具備 16GB+ RAM/VRAM，過程中使用者完全無從得知。該做法繞過歐盟 ePrivacy 指令第 5(3) 條（設備儲存需事先同意）的要求。刪除該模型後 Chrome 會自動重新下載，使用者需進入 chrome://flags 才能關閉相關功能，隱私侵害程度深遠。"
key_points:
  - "Gemini Nano 模型約 4GB，在無顯式同意下自動安裝於用戶裝置，安裝期間毫無通知"
  - "刪除後自動重新下載，需進入 chrome://flags 才能完全禁用，移除困難重重"
  - "違反 ePrivacy Directive Article 5(3)，且可見 UI（「AI Mode」）實際路由至 Google 伺服器而非本地，造成使用者誤解"
tags: [chrome, privacy, on-device-ai, gemini-nano, consent]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: true
deep_dive_approved: false
---

## Google Chrome silently installs a 4 GB AI model on your device without consent

Google Chrome 在用戶無明確同意的情況下，自動下載並安裝 4GB 的 Gemini Nano AI 模型（OptGuideOnDeviceModel/weights.bin），用於啟用「幫我寫作」和詐騙檢測等功能。安裝全程耗時約 14 分鐘，僅需裝置具備 16GB+ RAM/VRAM，過程中使用者完全無從得知。該做法繞過歐盟 ePrivacy 指令第 5(3) 條（設備儲存需事先同意）的要求。刪除該模型後 Chrome 會自動重新下載，使用者需進入 chrome://flags 才能關閉相關功能，隱私侵害程度深遠。

### 重點
- Gemini Nano 模型約 4GB，在無顯式同意下自動安裝於用戶裝置，安裝期間毫無通知
- 刪除後自動重新下載，需進入 chrome://flags 才能完全禁用，移除困難重重
- 違反 ePrivacy Directive Article 5(3)，且可見 UI（「AI Mode」）實際路由至 Google 伺服器而非本地，造成使用者誤解

**原文：** [hackernews](https://www.thatprivacyguy.com/blog/chrome-silent-nano-install/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Google Chrome silently installs a 4 GB AI model on your device without consent

</details>