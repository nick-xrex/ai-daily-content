---
id: inbox_c13b71af
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_c13b71af]]"
title: "I turned Claude into a small claims court (with AI lawyers, a judge, and bribes)"
url: https://www.reddit.com/r/ClaudeAI/comments/1t4nf64/i_turned_claude_into_a_small_claims_court_with_ai/
source: reddit-claudeai
published_at: 2026-05-05T18:07:19+00:00
fetched_at: 2026-05-06T13:29:59.479661+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者利用多個 Claude 實例構建模擬小額訴訟法庭應用，包含五種律師角色原型（鯊魚型、十字軍型、教授型、製作人型、弱者型），同一案件因律師類型而產生截然不同的訴訟策略。系統檢索過往判決作為先例注入、支援私密耳語機制（律師與當事人私密通訊）與司法賄賂系統（法官權衡的隱性激勵）。已發展為即時網頁應用（Cloudflare Workers + Durable Objects + Claude）。"
key_points:
  - "五種律師原型在同一案件展現迥異的論證風格：鯊魚型攻擊可信度、教授型引述先例（真實或虛構），說明角色設計對 Claude 輸出多樣性的影響"
  - "動態案例法系統：檢索相似判決並注入上下文，使法庭「自我演化」司法判例，示範檢索增強代理在時間累積中的涌現行為"
  - "隱蔽通訊與激勵機制：耳語系統防止律師公開透露私密策略；賄賂機制在接近判決中發揮微妙作用，展示多元信號在多代理系統中的效應"
tags: [prompt-engineering, multi-agent, role-playing, retrieval-augmented]
topics: [foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## I turned Claude into a small claims court (with AI lawyers, a judge, and bribes)

使用者利用多個 Claude 實例構建模擬小額訴訟法庭應用，包含五種律師角色原型（鯊魚型、十字軍型、教授型、製作人型、弱者型），同一案件因律師類型而產生截然不同的訴訟策略。系統檢索過往判決作為先例注入、支援私密耳語機制（律師與當事人私密通訊）與司法賄賂系統（法官權衡的隱性激勵）。已發展為即時網頁應用（Cloudflare Workers + Durable Objects + Claude）。

### 重點
- 五種律師原型在同一案件展現迥異的論證風格：鯊魚型攻擊可信度、教授型引述先例（真實或虛構），說明角色設計對 Claude 輸出多樣性的影響
- 動態案例法系統：檢索相似判決並注入上下文，使法庭「自我演化」司法判例，示範檢索增強代理在時間累積中的涌現行為
- 隱蔽通訊與激勵機制：耳語系統防止律師公開透露私密策略；賄賂機制在接近判決中發揮微妙作用，展示多元信號在多代理系統中的效應

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t4nf64/i_turned_claude_into_a_small_claims_court_with_ai/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I turned Claude into a small claims court (with AI lawyers, a judge, and bribes)

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1t4nf64/i_turned_claude_into_a_small_claims_court_with_ai/"> <img alt="I turned Claude into a small claims court (with AI lawyers, a judge, and bribes)" src="https://external-preview.redd.it/MzRnY2I3YzAwZHpnMYfmhZhp3MJ-Y_KlGxKTeHXbMLzz8SdLuP2ys7Y9CU_J.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=7c4f28e596736ee53dee3e0c061237f6cb6f2fee" title="I turned Claude into a small claims court (with AI lawyers, a judge, and bribes)" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Two people file opposing sides of a petty dispute. Claude argues both sides as lawyers, another Claude instance judges, spectators throw reactions.</p> <p>Mostly a prompt engineering exercise. A few fun bits:</p> <p>Personas with teeth. Five counsel archetypes. Shark, Crusader, Professor, Impresario, Underdog. The Shark attacks credibility. The Professor cites precedent (real and invented). Same case, different counsel = wildly different trial.</p> <p>Past verdicts as case law. Similar prior rulings get retrieved and injected as precedent. The court develops its own jurisprudence over time. Most unexpectedly fun part.</p> <p>Whispers. Send private strategy to your lawyer between turns. Injected as a separate channel, never reaches opposing counsel. Took iterations to get the lawyer to act on whispers without quoting them aloud.</p> <p>Judicial Gratuities. The judge accepts tips. Neither side sees what the other paid. The judge’s prompt is told the amounts and instructed they may be considered in close calls. (Yes, really.) Verdicts sometimes acknowledge it in the most thinly-veiled way possible.</p> <p>What started as a quick side project turned into a live web experience with live trials, spectators, and even a live court tv guide. </p> <p>Stack: Cloudflare Workers + Durable Objects + Claude. Happy to get into prompts and tech in the comments.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/etaheri"> /u/etaheri </a> <br /> <span><a href="https://v.redd.it/idqthni00dzg1">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t4nf64/i_turned_claude_into_a_small_claims_court_with_ai/">[comments]</a></span> </td></tr></table>

</details>