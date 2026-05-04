---
id: inbox_b8ef716e
date: 2026-05-02
source_ref: "[[00-inbox/.../inbox_b8ef716e]]"
title: "spent way too long manually steering claude code every session until i stopped doing that"
url: https://www.reddit.com/r/ClaudeAI/comments/1t23l7f/spent_way_too_long_manually_steering_claude_code/
source: reddit-claudeai
published_at: 2026-05-02T22:19:08+00:00
fetched_at: 2026-05-04T14:45:24.156962+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 重度使用者分享持久化配置最佳實踐：將工作風格、代碼結構、錯誤處理偏好寫入持久化設定檔後，可完全消除每次 session 的 20 分鐘 onboarding 成本，使模型即時進入高效工作狀態而非浪費時間「猜測」，最終將工作流時長從 60 分鐘縮至 40 分鐘（40% 提升）。"
key_points:
  - "持久化配置（CLAUDE.md）可消除每次 session 的上下文重申成本，零冷啟動"
  - "實踐結果：session 時長 60 分鐘 → 40 分鐘（省 20 分鐘 onboarding + 實際工作效率提升）"
  - "「模型已知用戶偏好」vs「模型猜測意圖」在生產力上有質的差異"
tags: [claude-code, workflow-optimization, persistent-config, context-management]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## spent way too long manually steering claude code every session until i stopped doing that

Claude Code 重度使用者分享持久化配置最佳實踐：將工作風格、代碼結構、錯誤處理偏好寫入持久化設定檔後，可完全消除每次 session 的 20 分鐘 onboarding 成本，使模型即時進入高效工作狀態而非浪費時間「猜測」，最終將工作流時長從 60 分鐘縮至 40 分鐘（40% 提升）。

### 重點
- 持久化配置（CLAUDE.md）可消除每次 session 的上下文重申成本，零冷啟動
- 實踐結果：session 時長 60 分鐘 → 40 分鐘（省 20 分鐘 onboarding + 實際工作效率提升）
- 「模型已知用戶偏好」vs「模型猜測意圖」在生產力上有質的差異

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t23l7f/spent_way_too_long_manually_steering_claude_code/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# spent way too long manually steering claude code every session until i stopped doing that

<!-- SC_OFF --><div class="md"><p>every session i was basically rewriting the same thing. here is how i like code structured, here is how i want errors handled, do not ask me to confirm every small thing, stay in this directory, etc.</p> <p>took maybe 20 minutes of the actual work time just getting claude back to where i left off. felt like onboarding a new hire every single day.</p> <p>eventually just wrote all of it down once in a persistent config. now claude starts every session already knowing how i work. no re-explaining, no course correcting in the first 10 messages.</p> <p>the difference in actual output quality was noticeable too. when it already knows your preferences it spends less time guessing and more time doing. sessions that used to take an hour were getting done in 40 minutes.</p> <p>if you are not doing this yet and you use claude code regularly it is genuinely worth the 20 minutes to set it up</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/CodinDev"> /u/CodinDev </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t23l7f/spent_way_too_long_manually_steering_claude_code/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t23l7f/spent_way_too_long_manually_steering_claude_code/">[comments]</a></span>

</details>