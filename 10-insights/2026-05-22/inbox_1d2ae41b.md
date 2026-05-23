---
id: inbox_1d2ae41b
date: 2026-05-22
source_ref: "[[00-inbox/2026-05-22/1800-simon-willison-ftc-to-require-cox-media-group-two-other-6b84]]"
title: "FTC to Require Cox Media Group, Two Other Firms to Pay Nearly $1 Million to Settle Charges They Deceived Customers About “Active Listening” AI-Powered Marketing Service"
url: https://simonwillison.net/2026/May/22/ftc-active-listening/#atom-everything
source: simon-willison
published_at: 2026-05-22T04:48:32+00:00
fetched_at: 2026-05-22T18:13:42.136635+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "美國 FTC 與 Cox Media Group、MindSift、1010 Digital Works 達成和解，罰款近 $1M。三家公司聲稱「Active Listening」服務可監聽消費者通過智能設備的對話進行實時廣告投放，搜集語音數據與行為數據進行 in-market consumer 精準投放。實際上該服務僅是以顯著加成 reselling 其他數據經紀人的電郵列表，完全沒有語音監聽或聲音數據使用。公司聲稱消費者已「選擇加入」該服務，但實則從未尋求同意，僅在應用下載時強制服務條款中嵌入聲明。FTC 明確澄清：點擊強制性服務條款 (mandatory terms of service) 不構成「適當同意」(adequate consent for invasive service)，更不用說家中語音數據的蒐集。若該服務真如廣告宣傳運作，未經適當同意使用消費者語音數據本身將違反 FTC Act Section 5。此案為反駁「智能設備通過麥克風監聽投放廣告」陰謀論提供官方執法證據。"
key_points:
  - "服務實質：純 reselling email lists from data brokers at significant markup，零語音數據實際使用；聲稱 voice-data + behavioral-data 投放，實則 none"
  - "欺詐手法：Clicking through mandatory T&S ≠ adequate opt-in consent，特別對侵入式服務 (invasive service) + 家中語音數據 (voice data inside homes)；FTC 明確規定不接受該隱蔽手段"
  - "FTC 法律框架：若服務如廣告所述運作，未經 adequate consent 蒐集 + 使用家中語音數據本身違反 FTC Act Section 5，無論實際技術能力如何"
tags: [ftc-settlement, privacy, voice-data-deception, regulatory, consent-definition]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## FTC to Require Cox Media Group, Two Other Firms to Pay Nearly $1 Million to Settle Charges They Deceived Customers About “Active Listening” AI-Powered Marketing Service

美國 FTC 與 Cox Media Group、MindSift、1010 Digital Works 達成和解，罰款近 $1M。三家公司聲稱「Active Listening」服務可監聽消費者通過智能設備的對話進行實時廣告投放，搜集語音數據與行為數據進行 in-market consumer 精準投放。實際上該服務僅是以顯著加成 reselling 其他數據經紀人的電郵列表，完全沒有語音監聽或聲音數據使用。公司聲稱消費者已「選擇加入」該服務，但實則從未尋求同意，僅在應用下載時強制服務條款中嵌入聲明。FTC 明確澄清：點擊強制性服務條款 (mandatory terms of service) 不構成「適當同意」(adequate consent for invasive service)，更不用說家中語音數據的蒐集。若該服務真如廣告宣傳運作，未經適當同意使用消費者語音數據本身將違反 FTC Act Section 5。此案為反駁「智能設備通過麥克風監聽投放廣告」陰謀論提供官方執法證據。

### 重點
- 服務實質：純 reselling email lists from data brokers at significant markup，零語音數據實際使用；聲稱 voice-data + behavioral-data 投放，實則 none
- 欺詐手法：Clicking through mandatory T&S ≠ adequate opt-in consent，特別對侵入式服務 (invasive service) + 家中語音數據 (voice data inside homes)；FTC 明確規定不接受該隱蔽手段
- FTC 法律框架：若服務如廣告所述運作，未經 adequate consent 蒐集 + 使用家中語音數據本身違反 FTC Act Section 5，無論實際技術能力如何

**原文：** [simon-willison](https://simonwillison.net/2026/May/22/ftc-active-listening/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

FTC to Require Cox Media Group, Two Other Firms to Pay Nearly $1 Million to Settle Charges They Deceived Customers About “Active Listening” AI-Powered Marketing Service 
Back in 2024 Cox Media Group were caught trying to sell advertisers packages based on "active listening", with this deck which claimed: 
 
 
 Smart devices capture real-time intent data by listening to our conversations 
 Advertisers can pair this voice-data with behavioral data to target in-market consumers 
 
 
 I wrote about this in September 2024 . My theory: 
 
 I think active listening is the term that the team came up with for “something that sounds fancy but really just means the way ad targeting platforms work already”. Then they got over-excited about the new metaphor and added that first couple of slides that talk about “voice data”, without really understanding how the tech works or what kind of a shitstorm that could kick off when people who DID understand technology started paying attention to their marketing. 
 
 This FTC press release appears to confirm that's pretty much what happened: 
 
 CMG, MindSift and 1010 Digital Works claimed their “Active Listening” branded marketing service listened in on consumers’ conversations overheard by smart devices, in real time, to target advertising [...] 
 According to the complaints, this service did not, in fact, listen in on consumers’ conversations or use voice data at all—nor did the service accurately place ads in customers’ desired locations. Instead, the service the companies provided consisted of reselling—at a significant markup—email lists obtained from other data brokers. 
 
 The FTC also clarify that hiding an "opt-in" to using voice data in terms of service would not be acceptable, as tricks like that do not constitute "adequate consent": 
 
 The FTC also alleged that all three companies deceived potential customers by claiming that consumers had opted into the Active Listening service. The company, however, did not seek or obtain consumers’ consent, according to the complaints. Instead, the companies claimed that consumers had “opted in” by agreeing to the terms of service that people have to accept when downloading and using apps. Clicking through mandatory terms of service does not constitute “opt-in consent” for such an invasive service or for use of consumers’ voice data from inside their homes. If the Active Listening service had functioned as advertised, this collection and use of consumers’ voice data without adequate consent would itself violate Section 5 of the FTC Act. 
 
 Attempting to myth bust the conspiracy theory that our mobile devices target ads to us based on spying through the microphones continues to be my least rewarding niche online hobby. It's nice to have a new piece of ammunition.

 Via @nydiatisdale 

 Tags: privacy , microphone-ads-conspiracy

</details>