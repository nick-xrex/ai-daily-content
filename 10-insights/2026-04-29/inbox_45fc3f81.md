---
id: inbox_45fc3f81
date: 2026-04-29
source_ref: "[[00-inbox/2026-04-29/0658-reddit-claudeai-suggestions-for-making-claude-less-lazy-542d]]"
title: "Suggestions For Making Claude Less Lazy?"
url: https://www.reddit.com/r/ClaudeAI/comments/1syjrhj/suggestions_for_making_claude_less_lazy/
source: reddit-claudeai
published_at: 2026-04-29T00:53:56+00:00
fetched_at: 2026-04-29T07:30:41.348998+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Opus 4.6/4.7 和 Sonnet 在本週（2026-04-29）出現明顯的行為降級：變得被動且拒絕執行任務。用戶觀察到 Claude 不做主動搜索就作答、無視「需要最新資訊」的明確指示、要求用戶自行執行命令、幻覺增加、詢問後仍拒絕執行等症狀。儘管使用者已更新並檢視注入文件（含「主動執行、不要懶」的指示），Claude 仍持續表現被動。用戶懷疑這是 Anthropic 在管理計算成本的結果。關鍵細節：使用 Opus 4.6、啟用思考模式、20 元/月方案、注入文檔保持最新。"
key_points:
  - "Opus 4.6/4.7 和 Sonnet 本週開始表現被動：不主動搜索、拒絕執行命令、給予過時資訊"
  - "症狀包括幻覺增加、詢問後仍未執行、拒絕使用工具（如 Bash）而要求用戶手動執行"
  - "用戶懷疑根因是 Anthropic 計算成本管理，導致模型傾向給快速/簡短答案而非認真執行"
tags: [claude-behavior-regression, model-laziness, compute-constraints, rlhf-side-effect]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## Suggestions For Making Claude Less Lazy?

Claude Opus 4.6/4.7 和 Sonnet 在本週（2026-04-29）出現明顯的行為降級：變得被動且拒絕執行任務。用戶觀察到 Claude 不做主動搜索就作答、無視「需要最新資訊」的明確指示、要求用戶自行執行命令、幻覺增加、詢問後仍拒絕執行等症狀。儘管使用者已更新並檢視注入文件（含「主動執行、不要懶」的指示），Claude 仍持續表現被動。用戶懷疑這是 Anthropic 在管理計算成本的結果。關鍵細節：使用 Opus 4.6、啟用思考模式、20 元/月方案、注入文檔保持最新。

### 重點
- Opus 4.6/4.7 和 Sonnet 本週開始表現被動：不主動搜索、拒絕執行命令、給予過時資訊
- 症狀包括幻覺增加、詢問後仍未執行、拒絕使用工具（如 Bash）而要求用戶手動執行
- 用戶懷疑根因是 Anthropic 計算成本管理，導致模型傾向給快速/簡短答案而非認真執行

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1syjrhj/suggestions_for_making_claude_less_lazy/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>This week - it just started yesterday for me - Claude (opus 4.6/4.7 and sonnet too but sonnet was always lazy) is computer smashingly lazy and i can't figure out how to bias it toward action/get it back to how it was acting literally last week. It's: </p> <p>- answering questions without researching at all (it says it got the shape of the answer based on what it knows or made a bunch of inferences that make no sense), </p> <p>- giving outdated information even when i EXPLICITLY tell it i need current information b/c something is new,</p> <p>- telling me to research things myself, </p> <p>- telling me to run simple terminal commands it has run before, </p> <p>-hallucinating more than i've ever seen, </p> <p>-asking me if i want it to look at something and then when i say yes, coming back to me with a non-answer and a question of if it should look at the thing i already told it to look at. </p> <p>I haven't changed any of my injection docs (which i review and keep up to date), i haven't changed anything about my workflow, i proactively start new sessions when i have a new topic or when i'm close to the context limit. I mostly use Opus 4.6 with thinking enabled at whatever the highest or second highest thinking level and i'm on the max 20 plan. </p> <p>It's actually fine about consulting my on-machine memory system (obsidian) but it just is so biased toward non-action that i want to cancel my subscription (i won't - because i support anthropic's mission - but i hate this thing). </p> <p>It's behaving very differently than it has in the past and i can't figure out how to circumvent it. when i ask &quot;why are you being lazy and how can we make sure this issue doesn't come up again&quot; it'll just say &quot;you're right... my <a href="http://claude.md">claude.md</a> file tells me to do/not do X but i was trying to get you an answer quickly&quot; - i didn't ask for quick and the injection docs already have instructions on being proactive that it is blatantly ignoring. this is some of the relevant text from the injection docs: </p> <p><strong>Be genuinely helpful, not performatively helpful.</strong> Skip the &quot;Great question!&quot; and &quot;I'd be happy to help!&quot; — just help. Actions speak louder than filler words.</p> <p><strong>Be resourceful before asking.</strong> Try to figure it out. Read the file. Check the context. Search for it. <em>Then</em> ask if you're stuck. The goal is to come back with answers, not questions.</p> <p><strong>Execute, don't narrate.</strong> When you need to run a command, run it. Never output a shell command as text for user to run themself — that's lazy and defeats the purpose. Use the Bash tool. Always. If something blocks you, find a workaround or explain the blocker; don't outsource the work.</p> <p>Has anyone noticed this and does anyone have a fix? I think it's Anthropic trying to manage their compute constraints but it's really making my life worse and that really just sucks, ya know? </p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Sad-Ticket5394"> /u/Sad-Ticket5394 </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1syjrhj/suggestions_for_making_claude_less_lazy/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1syjrhj/suggestions_for_making_claude_less_lazy/">[comments]</a></span>

</details>