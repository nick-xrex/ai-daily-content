---
id: inbox_ba8f4e2b
date: 2026-05-02
source_ref: "[[00-inbox/.../inbox_ba8f4e2b]]"
title: "A personal opinion about Opus 4.7 - not that bad after all"
url: https://www.reddit.com/r/ClaudeAI/comments/1t1xmh3/a_personal_opinion_about_opus_47_not_that_bad/
source: reddit-claudeai
published_at: 2026-05-02T18:25:15+00:00
fetched_at: 2026-05-04T14:45:24.152430+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "軟體工程師分享 Claude 4.7 使用經驗：初期在 Git merge/stash 等操作上性能下降，但搭配自動模式與豐富專案文檔（10000+ 行）後，一個工作流內完成 3 個新端點、購物車 UX 重構、郵件流程重設、驗證模式統一、.docx 提取技巧、2 次跨分支 merge 和 13 個工單，使用了 1M context 視窗的 60%。性能有改善但穩定性需改進。"
key_points:
  - "Opus 4.7 初期 Git 操作性能下降，後在計劃審查階段反而能發現其他相關問題"
  - "單一工作流完成 3 後端端點 + 購物車重構 + 郵件流程 + 驗證統一 + .docx 提取 + 2 git merge，context 使用率 60%"
  - "Auto mode + 完善文檔基礎（10000+ 行）對實際生產力有質的差異提升"
tags: [opus-4.7, claude-code, auto-mode, git-workflow, context-management]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## A personal opinion about Opus 4.7 - not that bad after all

軟體工程師分享 Claude 4.7 使用經驗：初期在 Git merge/stash 等操作上性能下降，但搭配自動模式與豐富專案文檔（10000+ 行）後，一個工作流內完成 3 個新端點、購物車 UX 重構、郵件流程重設、驗證模式統一、.docx 提取技巧、2 次跨分支 merge 和 13 個工單，使用了 1M context 視窗的 60%。性能有改善但穩定性需改進。

### 重點
- Opus 4.7 初期 Git 操作性能下降，後在計劃審查階段反而能發現其他相關問題
- 單一工作流完成 3 後端端點 + 購物車重構 + 郵件流程 + 驗證統一 + .docx 提取 + 2 git merge，context 使用率 60%
- Auto mode + 完善文檔基礎（10000+ 行）對實際生產力有質的差異提升

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t1xmh3/a_personal_opinion_about_opus_47_not_that_bad/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# A personal opinion about Opus 4.7 - not that bad after all

<!-- SC_OFF --><div class="md"><p>I'll play a bit the role of Devil's lawyer here, but as a software engineer that is building his own product I started to use Opus 4.7 on the first day it was released (as a Max subscription user).<br /> Working with Claude Code daily, sometimes for a couple of hours, I really enjoy the tool but as many of you mentioned it was a bad surprise initially due to its performance. </p> <p>For some of the tasks it performed better but for some tasks that I didn't expect he crumbled up, for example, the most important one was trying to do some merges from some branches to other branches and to stash some changes, like a regular Git workflow, that even the last year November Claude model didn't have any issue to complete seamlessly. </p> <p>After this failure, I decided to change back to 4.6. It wasn't that easy; you need to specify some model code, but I changed it, and I continued implementing as usual. Prepared a heavy plan to implement, but before I started implementing the plan I changed back to 4.7 and asked to review the plan, and surprisingly found a couple of good issues. Not sure if it was because I told him that Codex is gonna review the changes or because of the model, jaja </p> <p>But the surprising part that made me write this post, which is my first post on Reddit btw, besides that a friend challenged me, is that I had a surprisingly very well session with the 4.7. Especially I think the environment around it is helping a lot, like the auto mode. Let me paste you here some summary extracted directly from Claude at the end of the session with what was done. The main point here is that it looked much easier to do this kind of bugfixing work than with the previous versions, mainly because of:<br /> - it looks around and finds bugs that are out not directly related to the current work<br /> - it suggested new tickets to be done as future improvements, giving the impression it has much better understanding. </p> <p>Just for clarification my repo is very well documented. I have over 10,000 lines of documentation written with Claude for Claude and future team-members, so what was achieved in couple hours:</p> <p>- 3 new BE endpoints + per-IP rate limiting + full integration tests</p> <p>- Cart UX: debounced auto-save, optimistic cache, onError rollback</p> <p>- Email confirmation flow rebuilt against a new public-config endpoint</p> <p>- Validation pattern unified into the design system</p> <p>- Wrote a reusable Claude Skill for .docx extraction (offline, PowerShell)</p> <p>- 2 cross-branch git merges with manual conflict resolution</p> <p>- 9 docs touched, 2 new; ~13 follow-up tickets filed</p> <p>- Clean atomic commits + pushes across both repos</p> <p>- ~60% of 1M context window over the whole session</p> <p>Overall I think this is an improvement, better performance but worst stability. Not sure if they provided paches without letting us know but still I'm waiting for her to see Claude 5 / Mythos.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Affectionate_Till148"> /u/Affectionate_Till148 </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t1xmh3/a_personal_opinion_about_opus_47_not_that_bad/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t1xmh3/a_personal_opinion_about_opus_47_not_that_bad/">[comments]</a></span>

</details>