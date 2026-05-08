---
id: inbox_352c5acc
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-simon-willison-notes-on-the-xai-anthropic-data-center-d-7419]]"
title: "Notes on the xAI/Anthropic data center deal"
url: https://simonwillison.net/2026/May/7/xai-anthropic/#atom-everything
source: simon-willison
published_at: 2026-05-07T17:09:28+00:00
fetched_at: 2026-05-08T07:43:22.050990+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Anthropic 與 SpaceX/xAI 達成 $5 億年度交易，獲得 Colossus 1 數據中心全部 300MW 容量以解決計算瓶頸。該數據中心因環保問題引發爭議：燃氣渦輪機在無污染控制和清潔空氣法許可下運作，與當地呼吸疾病增加相關。xAI 同時棄用 Grok 4.1 Fast 等多個模型，僅給開發者兩週遷移期。Elon Musk 聲稱已被說服支持交易，但保留若 Claude「傷害人類」即單方面回收計算資源的權利。在 AI 數據中心成為政治議題的背景下，這為 Anthropic 帶來新的供應鏈風險。"
key_points:
  - "Anthropic 獲得 Colossus 1 全部 300MW 容量（年度 $5 億），但該數據中心缺乏污染控制、與當地呼吸疾病增加相關"
  - "Elon Musk 保有單方面決定標準（「傷害人類」）並回收計算資源的權利，構成供應鏈風險"
  - "xAI 同步棄用 Grok 4.1 Fast 等模型，僅提供兩週遷移期，影響依賴該模型的開發者生態"
tags: [anthropic, xai-spacex, data-center-deal, ai-ethics, supply-chain-risk]
topics: [foundation_models.claude]
importance: 5
novelty: 5
insight_quality: 4
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## Notes on the xAI/Anthropic data center deal

Anthropic 與 SpaceX/xAI 達成 $5 億年度交易，獲得 Colossus 1 數據中心全部 300MW 容量以解決計算瓶頸。該數據中心因環保問題引發爭議：燃氣渦輪機在無污染控制和清潔空氣法許可下運作，與當地呼吸疾病增加相關。xAI 同時棄用 Grok 4.1 Fast 等多個模型，僅給開發者兩週遷移期。Elon Musk 聲稱已被說服支持交易，但保留若 Claude「傷害人類」即單方面回收計算資源的權利。在 AI 數據中心成為政治議題的背景下，這為 Anthropic 帶來新的供應鏈風險。

### 重點
- Anthropic 獲得 Colossus 1 全部 300MW 容量（年度 $5 億），但該數據中心缺乏污染控制、與當地呼吸疾病增加相關
- Elon Musk 保有單方面決定標準（「傷害人類」）並回收計算資源的權利，構成供應鏈風險
- xAI 同步棄用 Grok 4.1 Fast 等模型，僅提供兩週遷移期，影響依賴該模型的開發者生態

**原文：** [simon-willison](https://simonwillison.net/2026/May/7/xai-anthropic/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

There weren't a lot of big new announcements from Anthropic at yesterday's Code w/ Claude event, but the biggest by far was the deal they've struck with SpaceX/xAI to use "all of the capacity of their Colossus data center". 
 As I mentioned in my live blog of the keynote , that's the one with the particularly bad environmental record . The gas turbines installed to power the facility initially ran without Clean Air Act permits or pollution control devices, which they got away with by classifying them as "temporary". Credible reports link it to increases in hospital admissions relating to low air quality. 
 Andy Masley, one of the most prolific voices pushing back against misleading rhetoric about data centers (see The AI water issue is fake and Data center land issues are fake ), had this to say about Colossus: 
 
 I would simply not run my computing out of this specific data center 
 
 I get that Anthropic are severely compute-constrained, but in a world where the very existence of "AI data centers" is a red-hot political issue (see recent news out of Utah for a fresh example), signing up with this particular data center is a really bad look. 
 There was a lot of initial chatter about how this meant xAI were clearly giving up on their own Grok models, since all of their capacity would be sold to Anthropic instead. That was a misconception - Anthropic are getting Colossus 1, but xAI are keeping their larger Colossus 2 data center for their own work. 
 As an interesting side note, the night before the Anthropic announcement, xAI sent out a deprecation notice for Grok 4.1 Fast and several other models providing just two weeks' notice before shutdown, reported here by @xlr8harder from SpeechMap: 
 
 
 This is terrible @xai. I just spent time and money to migrate to grok 4.1 fast, and you're disabling it with less than two weeks notice, after releasing it in November, with no migration path to a fast/cheap alternative. 
 I will never depend on one of your products again. 
 
 Here's SpeechMap's detailed explanation of how they selected Grok 4.1 Fast for their project in March. 
 Were xAI serving those models out of Colossus 1? 
 xAI owner Elon Musk (who previously delighted in calling Anthropic "Misanthropic" ) tweeted the following: 
 
 By way of background for those who care, I spent a lot of time last week with senior members of the Anthropic team to understand what they do to ensure Claude is good for humanity and was impressed. [...] 
 After that, I was ok leasing Colossus 1 to Anthropic, as SpaceXAI had already moved training to Colossus 2. 
 
 And then shortly afterwards : 
 
 Just as SpaceX launches hundreds of satellites for competitors with fair terms and pricing, we will provide compute to AI companies that are taking the right steps to ensure it is good for humanity. 
 We reserve the right to reclaim the compute if their AI engages in actions that harm humanity. 
 
 Presumably the criteria for "harm humanity" are decided by Elon himself. Sounds like a new form of supply chain risk for Anthropic to me! 
 
 Tags: ai , llms , anthropic , ai-ethics , ai-energy-usage , xai , andy-masley

</details>