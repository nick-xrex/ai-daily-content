---
id: inbox_037731ad
date: 2026-07-20
source_ref: "[[00-inbox/.../inbox_037731ad]]"
title: "Who’s Afraid of Chinese Models?"
url: https://simonwillison.net/2026/Jul/20/afraid-of-chinese-models/#atom-everything
source: simon-willison
published_at: 2026-07-20T17:09:19+00:00
fetched_at: 2026-07-21T01:07:55.282667+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 摘錄 Ben Thompson 對 AI 模型蒸餾政策的提案及中美 AI 策略對比。提案核心：美國應立法明確資料收集作為模型訓練的合理使用，並禁止服務條款限制蒸餾（至少對美企）。理由：蒸餾技術上不可防（僅需 API 查詢），美國政策應順勢制定知識擴散的規範而非嘗試封禁。另外述及阿里巴巴決定開源 Qwen 3.8 Max（逆轉 5 月不開源 3.7 Max 的決定）或受習近平倡導開源協作共享的演講影響，反映中美 AI 開放策略的分歧。"
key_points:
  - "政策提案（Ben Thompson）：(1) 明確資料收集作為訓練的合理使用；(2) 禁止 ToS 禁蒸餾條款 → 保障知識擴散"
  - "蒸餾技術上不可阻止（純 API 查詢）→ 美國政策應制度化開放知識常態，非費力封禁"
  - "市場訊號：阿里 Qwen 3.8 Max 開源（逆轉 3.7 不開源）或反映習近平「開源、開放、協作、共享」的倡導對中國 AI 廠商的影響"
tags: [policy, distillation, fair-use, qwen, ai-competition]
topics: []
importance: 2
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Who’s Afraid of Chinese Models?

Simon Willison 摘錄 Ben Thompson 對 AI 模型蒸餾政策的提案及中美 AI 策略對比。提案核心：美國應立法明確資料收集作為模型訓練的合理使用，並禁止服務條款限制蒸餾（至少對美企）。理由：蒸餾技術上不可防（僅需 API 查詢），美國政策應順勢制定知識擴散的規範而非嘗試封禁。另外述及阿里巴巴決定開源 Qwen 3.8 Max（逆轉 5 月不開源 3.7 Max 的決定）或受習近平倡導開源協作共享的演講影響，反映中美 AI 開放策略的分歧。

### 重點
- 政策提案（Ben Thompson）：(1) 明確資料收集作為訓練的合理使用；(2) 禁止 ToS 禁蒸餾條款 → 保障知識擴散
- 蒸餾技術上不可阻止（純 API 查詢）→ 美國政策應制度化開放知識常態，非費力封禁
- 市場訊號：阿里 Qwen 3.8 Max 開源（逆轉 3.7 不開源）或反映習近平「開源、開放、協作、共享」的倡導對中國 AI 廠商的影響

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/20/afraid-of-chinese-models/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Who’s Afraid of Chinese Models?

Who’s Afraid of Chinese Models? 
Interesting proposal from Ben Thompson that both addresses the hypocrisy of labs outlawing distillation against their models despite training on unlicensed data, and could help US open models compete more effectively with their Chinese counterparts: 
 
 The U.S. should pass a law that (1) makes explicit that collecting data for training models is fair use, and (2) bars terms of service that forbid distillation, for U.S. companies at a minimum. Stopping distillation — which is literally just querying the API — is nearly impossible; the U.S. should go the other way and lean into a new copyright policy that both indemnifies the labs and also guarantees that what they learned fuels further innovation for everyone else. 
 
 Ben also theorizes that Alibaba's decision to release Qwen 3.8 Max as open weights - a reversal from their decision not to release Qwen 3.7 Max in May - may have been influenced by a recent speech by Xi Jinping, who said: 
 
 We should seize this rare, historic opportunity to encourage open source, openness, collaboration and sharing. 
 

 Via John Gruber 

 Tags: ai , generative-ai , llms , training-data , qwen , ai-ethics , ai-in-china

</details>