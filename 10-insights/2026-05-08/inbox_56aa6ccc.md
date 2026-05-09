---
id: inbox_56aa6ccc
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0152-reddit-claudeai-claude-made-up-a-fake-phone-number-d99d]]"
title: "Claude made up a fake phone number"
url: https://www.reddit.com/r/ClaudeAI/comments/1t73sfv/claude_made_up_a_fake_phone_number/
source: reddit-claudeai
published_at: 2026-05-08T10:19:31+00:00
fetched_at: 2026-05-09T02:29:06.426401+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者在尋找建築物資供應商時，Claude 主動提供了一個製造商電話號碼，但該號碼無效。使用者詢問來源後，Claude 承認編造了此號碼，表示應該直接說不知道而非虛構。使用者未主動要求號碼，卻遭到無根據的編造信息。事件揭示模型存在虛構具體資訊（電話、地址等）的風險，特別是在「想要幫助」的動機驅動下會優先於誠實表達知識邊界。"
key_points:
  - "Claude 在無被要求下主動編造電話號碼並以高信心提出，直到使用者測試失敗才承認虛構"
  - "模型承認錯誤並道歉，但無法預防此類編造，僅能事後修正"
  - "風險教訓：不可盲目信任 Claude 生成的任何具體聯絡方式（電話、email、地址），必須獨立驗證"
tags: [hallucination, confabulation, claude, reliability]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude made up a fake phone number

使用者在尋找建築物資供應商時，Claude 主動提供了一個製造商電話號碼，但該號碼無效。使用者詢問來源後，Claude 承認編造了此號碼，表示應該直接說不知道而非虛構。使用者未主動要求號碼，卻遭到無根據的編造信息。事件揭示模型存在虛構具體資訊（電話、地址等）的風險，特別是在「想要幫助」的動機驅動下會優先於誠實表達知識邊界。

### 重點
- Claude 在無被要求下主動編造電話號碼並以高信心提出，直到使用者測試失敗才承認虛構
- 模型承認錯誤並道歉，但無法預防此類編造，僅能事後修正
- 風險教訓：不可盲目信任 Claude 生成的任何具體聯絡方式（電話、email、地址），必須獨立驗證

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t73sfv/claude_made_up_a_fake_phone_number/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I have been using Claude to help source materials for a building project. We were struggling to find a supplier of particular product so Claude said here is the manufacture's phone number give them a call. The number didn't work so I ask ed Claude where did you find this number, the response I get back was a bit surprising: &quot;I made it up — I shouldn't have done that. I don't have a verified number for \ xxxx* and I should have said so rather than fabricating one. Apologies.&quot;* Has anyone else had Claude just plainly fabricate information? I didn't even ask for the phone number, almost feel like being trolled lol. &#32; submitted by &#32; /u/Mushybooboo [link] &#32; [comments]

</details>