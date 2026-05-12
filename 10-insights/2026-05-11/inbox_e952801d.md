---
id: inbox_e952801d
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/1800-reddit-claudeai-multi-repo-orchestration-1361]]"
title: "Multi-repo orchestration"
url: https://www.reddit.com/r/ClaudeAI/comments/1ta04ly/multirepo_orchestration/
source: reddit-claudeai
published_at: 2026-05-11T11:12:23+00:00
fetched_at: 2026-05-11T18:18:11.153351+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: ""
key_points:
tags: []
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Multi-repo orchestration



### 重點

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1ta04ly/multirepo_orchestration/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Anyone know of a solution for tying in multiple IDE sessions with a multi-repo project so that they work cooperatively with a single shared inbox/memory? Here is my use case (whether it’s with or without the use of Storybloq): - all sessions are running Storybloq which saves root level /.story tickets and issues or if I have multiple projects I store each of them in /projects/&lt;project\_name&gt;/.story - have three repos open in Cursor with 1-2 sessions each - have a master Cursor session open that at the root level with /Sites/.story I use the master session for any multi-repo orchestration projects I need to do (ie wire up the iOS app with access to the sales and app repo’s APIs, etc) so I can track the different project phases and tickets for both the master project and the individual sub-projects using the Storybloq macOS app. My main problem is that when repo 1, session A is told to communicate with repo 2, session B, it tries to do it in the same session, which then starts to make the session get confused as which directory to work out of since it will CD /repo2/session B to do it. I wanted to create a hook that senses that repo 1, session A has created a prompt/instruction set for repo 2, session B and have that session B detect it is being referenced and start the prompt. I will always leave open a designated “catcher” session so that I can be doing any non-collaborative work in repo 2, session A, leaving session B waiting for the collab request from repo XYZ, session 123. Let me know if this makes sense or not, and I’ll try and clear it up! &#32; submitted by &#32; /u/achilleshightops [link] &#32; [comments]

</details>