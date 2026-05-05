---
id: inbox_dba28d41
date: 2026-05-04
source_ref: "[[00-inbox/2026-05-04/0819-reddit-claudeai-claude-is-now-confusing-users-for-subjec-e623]]"
title: "Claude is now confusing users for subject in its thinking. What is happening?"
url: https://www.reddit.com/r/ClaudeAI/comments/1t3j6gl/claude_is_now_confusing_users_for_subject_in_its/
source: reddit-claudeai
published_at: 2026-05-04T14:22:41+00:00
fetched_at: 2026-05-05T08:46:40.674731+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude 用戶在前景研究（prospect research）任務中發現模型在思考（thinking）階段出現嚴重錯誤。模型混淆使用者身份和研究對象：用戶詢問拿破崙時，模型思考內容反而寫成「用戶在義大利戰役的成功」，或將「用戶與內伊元帥開發的軍事戰略」混為一談。原文應為「拿破崙與內伊元帥」等歷史人物，但模型將使用者本人誤認為軍事主體。此現象在同一對話中重複出現至少 2 次以上。即使用戶明確指正錯誤、要求更加小心，模型隨後仍再犯相同錯誤多次。用戶推測模型可能在最近 24 小時內發生了推理性能退化。"
key_points:
  - "模型 thinking 階段混淆用戶和研究對象身份，例如『用戶與內伊元帥開發戰略』（應為『拿破崙與內伊』）"
  - "同一對話中錯誤重複出現多次，使用者明確指正後仍未改善並再犯"
  - "問題侷限於 thinking 顯示內容，暗示上下文追蹤在內部推理階段出現故障"
tags: [claude-thinking, context-confusion, reasoning-bug]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude is now confusing users for subject in its thinking. What is happening?

Claude 用戶在前景研究（prospect research）任務中發現模型在思考（thinking）階段出現嚴重錯誤。模型混淆使用者身份和研究對象：用戶詢問拿破崙時，模型思考內容反而寫成「用戶在義大利戰役的成功」，或將「用戶與內伊元帥開發的軍事戰略」混為一談。原文應為「拿破崙與內伊元帥」等歷史人物，但模型將使用者本人誤認為軍事主體。此現象在同一對話中重複出現至少 2 次以上。即使用戶明確指正錯誤、要求更加小心，模型隨後仍再犯相同錯誤多次。用戶推測模型可能在最近 24 小時內發生了推理性能退化。

### 重點
- 模型 thinking 階段混淆用戶和研究對象身份，例如『用戶與內伊元帥開發戰略』（應為『拿破崙與內伊』）
- 同一對話中錯誤重複出現多次，使用者明確指正後仍未改善並再犯
- 問題侷限於 thinking 顯示內容，暗示上下文追蹤在內部推理階段出現故障

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t3j6gl/claude_is_now_confusing_users_for_subject_in_its/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Earlier today while doing prospect research, I noticed Claude's thinking had confused <em>me</em> for the prospect I was asking about. Then it happened again in a different chat.</p> <p>I can't share the block for privacy reasons, but I had Claude rewrite it as if I was asking about Napoleon:</p> <blockquote> <p><em>Now I'm seeing the real issue with paragraph 2. The original version emphasized the military strategy the user and Ney developed during the Italian Campaign</em></p> </blockquote> <p>It's so weird. I've never seen this before.</p> <p>And just now, after telling it to be careful about this, it did it several more times again. Another example:</p> <blockquote> <p><em>What's actually happening here is that the user's success with the Italian Campaign comes from accumulated military strategy built over years at the artillery school in Auxonne</em></p> </blockquote> <p>Is anyone else noticing this? I swear Claude got nerfed hard in the last 24 hours.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Friskyinthenight"> /u/Friskyinthenight </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3j6gl/claude_is_now_confusing_users_for_subject_in_its/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3j6gl/claude_is_now_confusing_users_for_subject_in_its/">[comments]</a></span>

</details>