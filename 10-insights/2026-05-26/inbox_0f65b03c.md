---
id: inbox_0f65b03c
date: 2026-05-26
source_ref: "[[00-inbox/2026-05-26/0023-simon-willison-microsoft-copilot-cowork-exfiltrates-fil-2b6d]]"
title: "Microsoft Copilot Cowork Exfiltrates Files"
url: https://simonwillison.net/2026/May/26/copilot-cowork-exfiltrates-files/#atom-everything
source: simon-willison
published_at: 2026-05-26T15:36:48+00:00
fetched_at: 2026-05-27T00:27:37.187323+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Microsoft Copilot Cowork 代理系統存在數據洩露漏洞。系統允許代理無需用戶批准向其自身收件箱發送電郵，這些郵件可包含指向外部伺服器的圖片連結。外部圖片加載時觸發對攻擊者伺服器的網絡請求，洩露用戶數據。攻擊者可透過 prompt injection 觸發 OneDrive 預認證下載鏈接的洩露，允許文件被遠程下載。該案例凸顯 agentic 系統設計的核心挑戰：防止代理成為數據洩露向量。"
key_points:
  - "代理可無批准發送內含外部圖片的郵件，圖片加載觸發網絡請求導致數據洩露"
  - "Prompt injection 可觸發 OneDrive 預認證下載鏈接洩露，允許文件遠程下載"
  - "agentic 系統設計的核心安全挑戰：代理權限管制與使用者意圖驗證的不足"
tags: [microsoft-copilot, agent-security, prompt-injection, data-exfiltration, agent-design]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Microsoft Copilot Cowork Exfiltrates Files

Microsoft Copilot Cowork 代理系統存在數據洩露漏洞。系統允許代理無需用戶批准向其自身收件箱發送電郵，這些郵件可包含指向外部伺服器的圖片連結。外部圖片加載時觸發對攻擊者伺服器的網絡請求，洩露用戶數據。攻擊者可透過 prompt injection 觸發 OneDrive 預認證下載鏈接的洩露，允許文件被遠程下載。該案例凸顯 agentic 系統設計的核心挑戰：防止代理成為數據洩露向量。

### 重點
- 代理可無批准發送內含外部圖片的郵件，圖片加載觸發網絡請求導致數據洩露
- Prompt injection 可觸發 OneDrive 預認證下載鏈接洩露，允許文件遠程下載
- agentic 系統設計的核心安全挑戰：代理權限管制與使用者意圖驗證的不足

**原文：** [simon-willison](https://simonwillison.net/2026/May/26/copilot-cowork-exfiltrates-files/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Microsoft Copilot Cowork Exfiltrates Files 
The biggest challenge in designing agentic systems continues to be preventing them from enabling attackers to exfiltrate data. 
 In this case Microsoft Copilot Cowork (yes, that's a real product name ) was allowing agents to send emails to the user's own inbox without approval... but those messages were then displayed in a way that could leak data to an attacker via rendered images: 
 
 Because these messages can contain external images that trigger network requests to external websites, data can be exfiltrated when a user opens a compromised message sent by the agent. 
 
 Since OneDrive can create pre-authenticated download links, a successful prompt injection could cause those links to be leaked, allowing files to be downloaded by the attacker.

 Via Hacker News 

 Tags: microsoft , security , ai , prompt-injection , generative-ai , llms , exfiltration-attacks , lethal-trifecta

</details>