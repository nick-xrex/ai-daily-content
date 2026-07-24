---
id: inbox_914e00fd
date: 2026-07-23
source_ref: "[[00-inbox/.../inbox_914e00fd]]"
title: "Tell HN: Namecheap gave my account to an unverified third party"
url: https://news.ycombinator.com/item?id=49028037
source: hackernews
published_at: 2026-07-23T21:05:29+00:00
fetched_at: 2026-07-24T02:50:59.926481+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hackernews 用戶曝露 Namecheap 的重大安全漏洞：當原用戶異議密碼重置時，服務商主動致電驗證身份；但當第三方（該用戶代理的學生社團新領導）打電話聲稱擁有該域名時，Namecheap 卻未進行任何驗證就直接更改帳戶密碼和關聯郵箱。該事件展現了身份驗證流程的致命不一致性 — 對原用戶要求嚴格驗證，對第三方聲稱卻輕易妥協。該用戶已將 12 個關鍵域名遷出 Namecheap。"
key_points:
  - "社交工程成功案例：服務商對原用戶驗證嚴格，對陌生來電者卻無驗證機制"
  - "身份驗證的不一致性是域名劫持的根本漏洞 — 即使是簡單的電話請求也能改變帳戶歸屬"
  - "域名註冊商的安全審計需要檢查驗證流程在不同用戶類型間的一致性"
tags: [security, social-engineering, account-takeover, identity-verification]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Tell HN: Namecheap gave my account to an unverified third party

Hackernews 用戶曝露 Namecheap 的重大安全漏洞：當原用戶異議密碼重置時，服務商主動致電驗證身份；但當第三方（該用戶代理的學生社團新領導）打電話聲稱擁有該域名時，Namecheap 卻未進行任何驗證就直接更改帳戶密碼和關聯郵箱。該事件展現了身份驗證流程的致命不一致性 — 對原用戶要求嚴格驗證，對第三方聲稱卻輕易妥協。該用戶已將 12 個關鍵域名遷出 Namecheap。

### 重點
- 社交工程成功案例：服務商對原用戶驗證嚴格，對陌生來電者卻無驗證機制
- 身份驗證的不一致性是域名劫持的根本漏洞 — 即使是簡單的電話請求也能改變帳戶歸屬
- 域名註冊商的安全審計需要檢查驗證流程在不同用戶類型間的一致性

**原文：** [hackernews](https://news.ycombinator.com/item?id=49028037)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Tell HN: Namecheap gave my account to an unverified third party

I’ve been a NameCheap customer for 13 years. I’ve also helped out an old college club paying for a .com they use (that is registered to me under my name, address, and phone number). During a recent leadership transition, the incoming club lead wanted to make changes to the DNS and didn’t know to contact me. They figured out the domain name was parked at NameCheap, so they initiated a password reset using the domain name. I got a password reset email and immediately filed a NameCheap support ticket saying “I did not initiate this”. They called me to verify I was the one who filed the ticket, and then followed up with a canned email with tips like check your anti-virus. The incoming club leader was persistent though, and called NameCheap support. He convinced them the domain registered in my name and address really belonged to his club, and with no verification or validation whatsoever, NameCheap changed my password, and changed the email address associated with my account. All because someone simply asked nicely on a phone call. Meanwhile in the background, someone advised the new club leader who I was and we were able to connect and get things transferred over. Ultimately I was happy to give them access or even ownership if they wanted (student club turnover being what it is, it’s likely a domain doesn’t get renewed and gets gobbled up by a squatter, which is why I was keeping it current for them). But NameCheap had no way of knowing any of this. As far as NameCheap was aware, this was a personal account of mine. They demonstrated they were perfectly able to pick up a phone and call me (to verify my initial support ticket) but when someone calls them and says “but I really want access to that account” they don’t bother? I’d hesitate to even call this social engineering. It’s clearly a massive vulnerability. I’ve already moved a dozen of my most critical domains out of NameCheap after seeing just how easy it is for a third party to completely take over a NameCheap account: just ask nicely.

</details>