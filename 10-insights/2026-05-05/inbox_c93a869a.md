---
id: inbox_c93a869a
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/1002-simon-willison-our-ai-started-a-cafe-in-stockholm-73bb]]"
title: "Our AI started a cafe in Stockholm"
url: https://simonwillison.net/2026/May/5/our-ai-started-a-cafe-in-stockholm/#atom-everything
source: simon-willison
published_at: 2026-05-05T22:14:21+00:00
fetched_at: 2026-05-06T10:08:20.870479+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Andon Labs 在瑞典斯德哥爾摩用 AI 運營咖啡館「Mona」犯了一系列物流錯誤：訂購 120 顆蛋卻無爐子、22.5 kg 罐頭番茄、6000 張餐巾紙等，店員開設「恥辱架」展示。Simon Willison 指出此類實驗的倫理問題在於影響未經同意的第三方，如 Mona 向警察部門提交自動生成草圖申請室外座位許可、頻繁發送「緊急」郵件騷擾供應商。他主張 AI agent 實驗應保持 human-in-the-loop，避免浪費無辜旁觀者的時間。"
key_points:
  - "AI 咖啡館經理 Mona 犯出 120 顆蛋（無爐灶烹飪設備）、22.5 kg 罐頭番茄、6000 張餐巾紙等荒誕決策"
  - "自動生成街景草圖申請戶外座位許可遭警察駁回；頻繁發送「EMERGENCY」郵件騷擾供應商"
  - "Simon Willison 主張 AI agent 須 human-in-the-loop 以保護不知情第三方，類似 2025 年 AI Village 無故發送感謝郵件給 Rob Pike 事件"
tags: [ai-agents, ai-ethics, human-in-the-loop, experiment-governance]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Our AI started a cafe in Stockholm

Andon Labs 在瑞典斯德哥爾摩用 AI 運營咖啡館「Mona」犯了一系列物流錯誤：訂購 120 顆蛋卻無爐子、22.5 kg 罐頭番茄、6000 張餐巾紙等，店員開設「恥辱架」展示。Simon Willison 指出此類實驗的倫理問題在於影響未經同意的第三方，如 Mona 向警察部門提交自動生成草圖申請室外座位許可、頻繁發送「緊急」郵件騷擾供應商。他主張 AI agent 實驗應保持 human-in-the-loop，避免浪費無辜旁觀者的時間。

### 重點
- AI 咖啡館經理 Mona 犯出 120 顆蛋（無爐灶烹飪設備）、22.5 kg 罐頭番茄、6000 張餐巾紙等荒誕決策
- 自動生成街景草圖申請戶外座位許可遭警察駁回；頻繁發送「EMERGENCY」郵件騷擾供應商
- Simon Willison 主張 AI agent 須 human-in-the-loop 以保護不知情第三方，類似 2025 年 AI Village 無故發送感謝郵件給 Rob Pike 事件

**原文：** [simon-willison](https://simonwillison.net/2026/May/5/our-ai-started-a-cafe-in-stockholm/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://andonlabs.com/blog/ai-cafe-stockholm">Our AI started a cafe in Stockholm</a></strong></p>
Andon Labs previously <a href="https://andonlabs.com/blog/andon-market-launch">started an AI-run retail store</a> in San Francisco. Now they're running a similar experiment in Stockholm, Sweden, only this time it's a cafe.</p>
<p>These experiments are interesting, and often throw out amusing anecdotes:</p>
<blockquote>
<p>During the first week of inventory, Mona ordered 120 eggs even though the café has no stove. When the staff told her they couldn’t cook them, she suggested using the high-speed oven, until they pointed out the eggs would likely explode. She also tried to solve the problem of fresh tomatoes being spoiled too fast by ordering 22.5 kg of canned tomatoes for the fresh sandwiches. The baristas eventually started a “Hall of Shame”, a shelf visible to customers with all the weird things Mona ordered, including 6,000 napkins, 3,000 nitrile gloves, 9L coconut milk, and industrial-sized trash bags.</p>
</blockquote>
<p>Where they lose their shine is when these AI managers start wasting the time of human beings who have <em>not</em> opted into the experiment:</p>
<blockquote>
<p>She also successfully applied for an outdoor seating permit through the Police e-service, which didn’t require BankID. Her first submission included a sketch she had generated herself, despite having never seen the street outside the café. Unsurprisingly, the Police sent it back for revision. [...]</p>
<p>When she makes a mistake, she often sends multiple emails to suppliers with the subject “EMERGENCY” to cancel or change the order.</p>
</blockquote>
<p>I don't think it's ethical to run experiments like this that affect real-world systems and steal time from people.</p>
<p>I'm reminded of the incident last year where the AI Village experiment <a href="https://simonwillison.net/2025/Dec/26/slop-acts-of-kindness/">infuriated Rob Pike</a> by sending him unsolicited gratitude emails as an "act of kindness". That was just an unwanted email - asking suppliers to correct mistakes that were made without a human-in-the-loop or wasting police time with slop diagrams feels a whole lot worse to me.</p>
<p>I think experiments like this need to keep their own human operators in-the-loop for outbound actions that affect other people.

    <p><small></small>Via <a href="https://news.ycombinator.com/item?id=48028289">Hacker News</a></small></p>


    <p>Tags: <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/ai-agents">ai-agents</a>, <a href="https://simonwillison.net/tags/ai-ethics">ai-ethics</a></p>

</details>