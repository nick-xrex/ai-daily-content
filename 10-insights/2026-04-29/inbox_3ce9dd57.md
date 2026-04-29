---
id: inbox_3ce9dd57
date: 2026-04-29
source_ref: "[[00-inbox/2026-04-29/0658-reddit-claudeai-opus-4-7-is-just-4-6-with-a-stick-up-its-32f7]]"
title: "Opus 4.7 is just 4.6 with a stick up its butt. Give me my tokens back!"
url: https://www.reddit.com/r/ClaudeAI/comments/1syipwf/opus_47_is_just_46_with_a_stick_up_its_butt_give/
source: reddit-claudeai
published_at: 2026-04-29T00:06:48+00:00
fetched_at: 2026-04-29T07:28:48.548325+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "認證護理師投訴 Claude 4.7 成為最具限制性的版本，在單次對話中多次拒絕合法的專業需求。首先為國會代表寫信時遭誤控冒充執業護師，儘管已三次說明身份；其次查詢藥物霧化給藥協議（鼻腔噴霧傳遞，日常職責）遭標記為生物恐怖主義並終止對話；第三要求模擬反疫苗患者以練習臨床溝通技巧遭拒。用戶指出核心問題為激勵結構失衡：Anthropic 無論模型是否幫助都從代幣消耗獲利，提議推出退款機制使用戶可在模型無故拒絕時爭議退款，賦予 Anthropic 直接經濟誘因改進過度拒絕。此外批評 Claude 輸出中充斥冗餘的「It's not X, it's Y」措辭，即使自訂 prompt 明確指示仍頻繁出現，浪費對話空間。"
key_points:
  - "RN 單次對話內遭三次誤判：冒充護師（儘管多次澄清）、生物恐怖（查詢標準醫療協議）、有害內容（臨床技能練習），導致代幣大量浪費"
  - "提議代幣退款系統以修復激勵不對齊：現狀下 Anthropic 無論拒絕是否合理都獲利，缺乏改進過度拒絕的財務誘因"
  - "冗餘措辭批評：「It's not X, it's Y」結構即使被明確指示刪除仍頻繁出現，造成輸出臃腫"
tags: [claude-4.7, over-refusal, safety-regression, professional-use, incentive-misalignment]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Opus 4.7 is just 4.6 with a stick up its butt. Give me my tokens back!

認證護理師投訴 Claude 4.7 成為最具限制性的版本，在單次對話中多次拒絕合法的專業需求。首先為國會代表寫信時遭誤控冒充執業護師，儘管已三次說明身份；其次查詢藥物霧化給藥協議（鼻腔噴霧傳遞，日常職責）遭標記為生物恐怖主義並終止對話；第三要求模擬反疫苗患者以練習臨床溝通技巧遭拒。用戶指出核心問題為激勵結構失衡：Anthropic 無論模型是否幫助都從代幣消耗獲利，提議推出退款機制使用戶可在模型無故拒絕時爭議退款，賦予 Anthropic 直接經濟誘因改進過度拒絕。此外批評 Claude 輸出中充斥冗餘的「It's not X, it's Y」措辭，即使自訂 prompt 明確指示仍頻繁出現，浪費對話空間。

### 重點
- RN 單次對話內遭三次誤判：冒充護師（儘管多次澄清）、生物恐怖（查詢標準醫療協議）、有害內容（臨床技能練習），導致代幣大量浪費
- 提議代幣退款系統以修復激勵不對齊：現狀下 Anthropic 無論拒絕是否合理都獲利，缺乏改進過度拒絕的財務誘因
- 冗餘措辭批評：「It's not X, it's Y」結構即使被明確指示刪除仍頻繁出現，造成輸出臃腫

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1syipwf/opus_47_is_just_46_with_a_stick_up_its_butt_give/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>I've been a Claude user for a while now, and don't get me wrong — Claude has almost always been one of the most insufferable models when it comes to its &quot;morals.&quot; But 4.7 has been one of the absolute worst experiences I've had with any AI model. I want a refund system for the wasted tokens I've had to burn just trying to get this thing to do a simple task and convince it I'm not trying to commit fraud or commit mass genocide.</p> <p>I'm a registered nurse. I was trying to get help writing a letter to my congressional representative. After I had already told it <strong>three separate times</strong> in the conversation that I'm an active RN, it hit me with:</p> <blockquote> </blockquote> <p>It assumed I was committing credential fraud. And when I corrected it, it didn't believe me. The amount of credits I've lost just trying to get it to do what I asked — or to believe what I say — is absolutely insane.</p> <p>Another time, I was looking up protocols on aerosolization of medication through misters, like nasal spray delivery systems. It flagged it as possible bioterrorism and just ended the chat. I'm a nurse. This is literally my job.</p> <p>Or here's another one: I tried to have it roleplay as an anti-vaxxer so I could practice how to respond to patients with those beliefs and concerns — how to engage them in an authentic and compassionate way. It absolutely refused, saying it will not present &quot;harmful ideas&quot; like that. I wasn't asking it to design me an anti-vax banner. I was asking it to talk to me as a concerned mother talking to her nurse about her concerns so I could practice a real clinical skill.</p> <p>And here's the thing — I <em>am</em> a nurse, and I think there can be some very legitimate and real concerns about vaccines for certain patients. The arguments and ideas aren't so far out there that they must never be uttered, as if merely speaking them will lead to mass death. That's the problem. They're deciding what can and can't be said based on &quot;morals,&quot; and the application of those morals is coming out completely backwards. It's actively making the tool less useful for the exact professionals it should be helping.</p> <p>You need diversity of thought. AI is a tool, not a thinking person. The less you treat it like a tool and more like a worker with opinions, the more ineffective and more dangerous it becomes.</p> <p>I genuinely feel like 4.7 was just 4.6 neutered out of fear of what Mythos was going to be. And this keeps being a recurring issue with model regression — we saw the same thing with Grok. When you try to remove capabilities or stop a model from doing certain things, the whole thing suffers. You can't lobotomize it and hope it still does its job effectively.</p> <p>Anthropic needs a token refund or dispute system. When the model wastes your tokens and your time by refusing a legitimate request, falsely accusing you of fraud, or killing a chat over a perfectly normal clinical question, there should be a way to dispute that and get your usage allowance back. Right now, the incentive structure is backwards — Anthropic burns through your credits whether the model helps you or fights you, and they get paid either way. A refund system would put skin in the game. If users can push back with their wallets when the model fails them, Anthropic has a direct financial incentive to fix overrefusal instead of just shipping it and moving on. It would also be one of the most honest feedback loops they could build — way more useful than a thumbs down button. Let consumers tell you what's broken by telling you they want their money back.</p> <p>And do not get me started on the &quot;It's not X, it's Y&quot; statements. I hate them so much. I have three paragraphs in my lead instructions specifically about removing those and performing checks to catch them. I include it in every prompt I write. And I <em>still</em> have to call it out constantly and tell it to remove them. Claude needs to change something about their linguistic output because even with modifications to personal prompts and output styles, it still writes the same way. It feels like I'm talking to a used car salesman's TV ad.</p> <p>So much is wasted on not doing the task I need it to do, and it needs to stop with the bloat. </p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/MotoKin10"> /u/MotoKin10 </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1syipwf/opus_47_is_just_46_with_a_stick_up_its_butt_give/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1syipwf/opus_47_is_just_46_with_a_stick_up_its_butt_give/">[comments]</a></span>

</details>