---
id: inbox_9174ea18
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/0114-simon-willison-vibe-coding-and-agentic-engineering-are-4fc0]]"
title: "Vibe coding and agentic engineering are getting closer than I&#39;d like"
url: https://simonwillison.net/2026/May/6/vibe-coding-and-agentic-engineering/#atom-everything
source: simon-willison
published_at: 2026-05-06T14:24:08+00:00
fetched_at: 2026-05-07T01:19:49.902037+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 在 Heavybit 播客中討論了一個令人不安的發現：「Vibe Coding」（非程序員無代碼審查的快速開發）與「Agentic Engineering」（資深工程師利用 AI 工具同時保持高標準）的界線正在模糊。隨著 Claude Code 等 AI 代理證明其可靠性，即使是 25 年資歷的工程師也開始不再逐行審查生成代碼，在生產環境中引發道德困境：若未審查就貿然使用是否符合專業責任。他用另一視角解決此困境：將 AI 代理視為黑盒子服務（如同信任另一工程團隊開發的服務），根據歷史表現決定信任度，只在出現問題時才深入。整個軟體開發週期的基本假設被打破：若代碼產出速度翻 10 倍（200→2000 行/天），上游設計流程與下游測試評審都需重新設計。AI 生成的專案（100+ commits、完整文件、自動化測試）已無法與精心打磨的手工代碼區分，評估標準從「程度有多好」轉向「實際被使用與驗證過」。"
key_points:
  - "Vibe Coding 適合個人工具（失敗成本由自己承擔），但用於生產環境會傷害他人（不負責任）；Agentic Engineering 是資深工程師利用 AI 工具達成 10 倍速度提升且維持高品質的方式"
  - "AI 代理變得可靠後，資深工程師也停止逐行審查（特別是 Claude Code 已證實 JSON API + SQL query 型工作無誤），但 Claude 本身無法承擔專業責任，造成道德困境；解法是將代理視為信任度根據歷史表現累積的黑盒服務"
  - "SDLC 假設被打破：200→2000 行/天的產速改變改變上游設計、下游評審所有流程；AI 生成的成熟專案（commits + docs + tests）無法與手工打磨品區分，評估標準從美觀程度轉向「實際被使用驗證」"
tags: [ai-coding-agents, vibe-coding, agentic-engineering, code-review, sdlc-transformation]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Vibe coding and agentic engineering are getting closer than I'd like

Simon Willison 在 Heavybit 播客中討論了一個令人不安的發現：「Vibe Coding」（非程序員無代碼審查的快速開發）與「Agentic Engineering」（資深工程師利用 AI 工具同時保持高標準）的界線正在模糊。隨著 Claude Code 等 AI 代理證明其可靠性，即使是 25 年資歷的工程師也開始不再逐行審查生成代碼，在生產環境中引發道德困境：若未審查就貿然使用是否符合專業責任。他用另一視角解決此困境：將 AI 代理視為黑盒子服務（如同信任另一工程團隊開發的服務），根據歷史表現決定信任度，只在出現問題時才深入。整個軟體開發週期的基本假設被打破：若代碼產出速度翻 10 倍（200→2000 行/天），上游設計流程與下游測試評審都需重新設計。AI 生成的專案（100+ commits、完整文件、自動化測試）已無法與精心打磨的手工代碼區分，評估標準從「程度有多好」轉向「實際被使用與驗證過」。

### 重點
- Vibe Coding 適合個人工具（失敗成本由自己承擔），但用於生產環境會傷害他人（不負責任）；Agentic Engineering 是資深工程師利用 AI 工具達成 10 倍速度提升且維持高品質的方式
- AI 代理變得可靠後，資深工程師也停止逐行審查（特別是 Claude Code 已證實 JSON API + SQL query 型工作無誤），但 Claude 本身無法承擔專業責任，造成道德困境；解法是將代理視為信任度根據歷史表現累積的黑盒服務
- SDLC 假設被打破：200→2000 行/天的產速改變改變上游設計、下游評審所有流程；AI 生成的成熟專案（commits + docs + tests）無法與手工打磨品區分，評估標準從美觀程度轉向「實際被使用驗證」

**原文：** [simon-willison](https://simonwillison.net/2026/May/6/vibe-coding-and-agentic-engineering/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p>I recently talked with Joseph Ruscio about AI coding tools for Heavybit's High Leverage podcast: <a href="https://www.heavybit.com/library/podcasts/high-leverage/ep-9-the-ai-coding-paradigm-shift-with-simon-willison">Ep. #9, The AI Coding Paradigm Shift with Simon Willison</a>. Here are some of my highlights, including my disturbing realization that vibe coding and agentic engineering have started to converge in my own work.</p>
<p>One thing I really enjoy about podcasts is that they sometimes push me to think out loud in a way that exposes an idea I've not previously been able to put into words.</p>
<h4 id="vibe-coding-and-agentic-engineering-are-starting-to-overlap">Vibe coding and agentic engineering are starting to overlap</h4>
<p>A few weeks after vibe coding was first coined I published <a href="https://simonwillison.net/2025/Mar/19/vibe-coding/">Not all AI-assisted programming is vibe coding (but vibe coding rocks)</a>, where I firmly staked out my belief that "vibe coding" is a very different beast from responsible use of AI to write code, which I've since started to call <a href="https://simonwillison.net/guides/agentic-engineering-patterns/what-is-agentic-engineering/">agentic engineering</a>.</p>
<p>When Joseph brought up the distinction between the two I had a sudden realization that they're not nearly as distinct for me as they used to be:</p>
<blockquote>
<p>Weirdly though, those things have started to blur for me already, which is quite upsetting.</p>
<p>I thought we had a very clear delineation where vibe coding is the thing where you're not looking at the code at all. You might not even know how to program. You might be a non-programmer who asks for a thing, and gets a thing, and if the thing works, then great! And if it doesn't, you tell it that it doesn't work and cross your fingers.</p>
<p>But at no point are you really caring about the code quality or any of those additional constraints. And my take on vibe coding was that it's fantastic, provided you understand when it can be used and when it can't.</p>
<p>A personal tool for you, where if there's a bug it hurts only you, go ahead!</p>
<p>If you're building software for other people, vibe coding is grossly irresponsible because it's other people's information. Other people get hurt by your stupid bugs. You need to have a higher level than that.</p>
<p>This contrasts with agentic engineering where you are a professional software engineer. You understand security and maintainability and operations and performance and so forth. You're using these tools to the highest of your own ability. I'm finding the scope of challenges I can take on has gone up by a significant amount because I've got the support of these tools.</p>
<p>But I'm still leaning on my 25 years of experience as a software engineer.</p>
<p>The goal is to build high quality production systems: if you're building lower quality stuff faster, I think that's bad. I want to build <em>higher</em> quality stuff faster. I want everything I'm building to be better in every way than it was before.</p>
<p>The problem is that as the coding agents get more reliable, I'm not reviewing every line of code that they write anymore, even for my production level stuff.</p>
<p>I know full well that if you ask Claude Code to build a JSON API endpoint that runs a SQL query and outputs the results as JSON, it's just going to do it right. It's not going to mess that up. You have it add automated tests, you have it add documentation, you know it's going to be good.</p>
<p>But I'm not reviewing that code. And now I've got that feeling of guilt: if I haven't reviewed the code, is it really responsible for me to use this in production?</p>
<p>The thing that really helps me is thinking back to when I've worked at larger organizations where I've been an engineering manager. Other teams are building software that my team depends on.</p>
<p>If another team hands over something and says, "hey, this is the image resize service, here's how to use it to resize your images"... I'm not going to go and read every line of code that they wrote.</p>
<p>I'm going to look at their documentation and I'm going to use it to resize some images. And then I'm going to start shipping my own features. And if I start running into problems where the image resizer thing appears to have bugs or the performance isn't good, that's when I might dig into their Git repositories and see what's going on. But for the most part I treat that as a semi-black box that I don't look at until I need to.</p>
<p>I'm starting to treat the agents in the same way. And it still feels uncomfortable, because human beings are accountable for what they do. A team can build a reputation. I can say "I trust that team over there. They built good software in the past. They're not going to build something rubbish because that affects their professional reputations."</p>
<p>Claude Code does not have a professional reputation! It can't take accountability for what it's done. But it's been proving itself anyway - time and time again it's churning out straightforward things and doing them right in the style that I like.</p>
</blockquote>
<p>There's an element of <a href="https://simonwillison.net/2025/Dec/10/normalization-of-deviance/">the normalization of deviance</a> here - every time a model turns out to have written the right code without me monitoring it closely there's a risk that I'll trust it at the wrong moment in the future and get burned.</p>
<h4 id="the-new-challenge-of-evaluating-software">The new challenge of evaluating software</h4>
<blockquote>
<p>It used to be if you found a GitHub repository with a hundred commits and a good readme and automated tests and stuff, you could be pretty sure that the person writing that had put a lot of care and attention into that project.</p>
<p>And now I can knock out a git repository with a hundred commits and a beautiful readme and comprehensive tests of every line of code in half an hour! It looks identical to those projects that have had a great deal of care and attention. Maybe it is as good as them. I don't know. I can't tell from looking at it. Even for my <em>own</em> projects, I can't tell.</p>
<p>So I realized what I value more than the quality of the tests and documentation is that I want somebody to have <em>used</em> the thing. If you've got a vibe coded thing which you have used every day for the past two weeks, that's much more valuable to me than something that you've just spat out and hardly even exercised.</p>
</blockquote>
<h4 id="the-bottlenecks-have-shifted">The bottlenecks have shifted</h4>
<blockquote>
<p>If you can go from producing 200 lines of code a day to 2,000 lines of code a day, what else breaks? The entire software development lifecycle was, it turns out, designed around the idea that it takes a day to produce a few hundred lines of code. And now it doesn't.</p>
<p>It's not just the downstream stuff, it's the upstream stuff as well. I saw <a href="https://simonwillison.net/2026/Jan/24/dont-trust-the-process/">a great talk by Jenny Wen</a>, who's the design leader at Anthropic, where she said we have all of these design processes that are based around the idea that you need to get the design <em>right</em> - because if you hand it off to the engineers and they spend three months building the wrong thing, that's catastrophic.</p>
<p>There's this whole very extensive design process that you put in place because that design results in expensive work. But if it doesn't take three months to build, maybe the design process can be a whole lot riskier because cost, if you get something wrong, has been reduced so much.</p>
</blockquote>
<h4 id="why-i-m-still-not-afraid-for-my-career">Why I'm still not afraid for my career</h4>
<blockquote>
<p>When I look at my conversations with the agents, it's very clear to me that this is moon language for the vast majority of human beings.</p>
<p>There are a whole bunch of reasons I'm not scared that my career as a software engineer is over now that computers can write their own code, partly because these things are amplifiers of existing experience. If you know what you're doing, you can run so much faster with them. [...]</p>
<p>I'm constantly reminded as I work with these tools how hard the thing that we do is. Producing software is a <em>ferociously</em> difficult thing to do. And you could give me all of the AI tools in the world and what we're trying to achieve here is still really difficult. [...]</p>
<p>Matthew Yglesias, who's a political commentator, yesterday <a href="https://twitter.com/mattyglesias/status/2049105745132585161">tweeted</a>, "Five months in, I think I've decided that I don't want to vibecode — I want professionally managed software companies to use AI coding assistance to make more/better/cheaper software products that they sell to me for money." And that feels about right to me. I can plumb my house if I watch enough YouTube videos on plumbing. I would rather hire a plumber.</p>
</blockquote>
<p>On the threat to SaaS providers of companies rolling their own solutions instead:</p>
<blockquote>
<p>I just realized it's the thing I said earlier about how I only want to use your side project if you've used it for a few weeks. The enterprise version of that is I don't want a CRM unless at least two other giant enterprises have successfully used that CRM for six months. [...] You want solutions that are proven to work before you take a risk on them.</p>
</blockquote>
    
        <p>Tags: <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/podcast-appearances">podcast-appearances</a>, <a href="https://simonwillison.net/tags/vibe-coding">vibe-coding</a>, <a href="https://simonwillison.net/tags/coding-agents">coding-agents</a>, <a href="https://simonwillison.net/tags/agentic-engineering">agentic-engineering</a></p>

</details>