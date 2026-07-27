---
id: inbox_a59f8784
date: 2026-07-26
source_ref: "[[00-inbox/2026-07-26/0123-ruflo-releases-v3-32-11-bridgerecordfeedback-wired-to-r-613d]]"
title: "v3.32.11 — bridgeRecordFeedback wired to real intelligence pipeline (#2786 fix-3)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.11
source: ruflo-releases
published_at: 2026-07-26T22:49:38+00:00
fetched_at: 2026-07-27T01:30:01.705800+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.11 修复了 bridgeRecordFeedback 的隐藏故障。原代码调用了不存在的 learningSystem.recordFeedback 和 reasoningBank.recordOutcome 方法，两个无声 catch 块掩盖了 API 不匹配错误。修复改为直接调用真实公共 API intelligence.recordTrajectory(steps, verdict)（与 hooks_post-command 使用相同），同时修正 pattern-store 分支调用正确存在的 LocalReasoningBank.store(pattern) 方法。端到端验证显示从 0 trajectories 提升至 6 trajectories + 3 pattern entries，证明学习系统现在真正记录任务结果。"
key_points:
  - "API 对齐修复：将调用不存在的 learningSystem/reasoningBank 方法改为真实的 intelligence.recordTrajectory() 公共 API"
  - "可观察性提升：从\"无声失败\"到\"有效记录\"，验证结果从 0 trajectories → 6 trajectories + 3 pattern entries"
  - "反模式消除：替换无声 catch { /* API mismatch — skip */ } 为正确 API 调用路径"
tags: [ruflo, bug-fix, intelligence-pipeline, silent-failure-elimination]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.11 — bridgeRecordFeedback wired to real intelligence pipeline (#2786 fix-3)

Ruflo v3.32.11 修复了 bridgeRecordFeedback 的隐藏故障。原代码调用了不存在的 learningSystem.recordFeedback 和 reasoningBank.recordOutcome 方法，两个无声 catch 块掩盖了 API 不匹配错误。修复改为直接调用真实公共 API intelligence.recordTrajectory(steps, verdict)（与 hooks_post-command 使用相同），同时修正 pattern-store 分支调用正确存在的 LocalReasoningBank.store(pattern) 方法。端到端验证显示从 0 trajectories 提升至 6 trajectories + 3 pattern entries，证明学习系统现在真正记录任务结果。

### 重點
- API 对齐修复：将调用不存在的 learningSystem/reasoningBank 方法改为真实的 intelligence.recordTrajectory() 公共 API
- 可观察性提升：从"无声失败"到"有效记录"，验证结果从 0 trajectories → 6 trajectories + 3 pattern entries
- 反模式消除：替换无声 catch { /* API mismatch — skip */ } 为正确 API 调用路径

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.11)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Follow-up patch closing the last remaining item flagged by the 2026-07-26 tracker-sweep agent — the sweep tagged it "architectural" but investigation showed a much smaller surgical fix was available. 
 Fixed 
 
 #2786 fix-3 — bridgeRecordFeedback no longer silently swallows every call. The prior code called learningSystem.recordFeedback / .record and reasoningBank.recordOutcome / .record , but the registry actually wires the LOCAL intelligence classes ( LocalSonaCoordinator / LocalReasoningBank ) via initializeIntelligence() in memory/intelligence.ts — those classes never had those methods, and two catch { /* API mismatch — skip */ } blocks made the failure invisible. Fix: call the real public API intelligence.recordTrajectory(steps, verdict) — same call hooks_post-command already uses. Pattern-store branch also fixed to call LocalReasoningBank.store(pattern) (the one method that actually exists). No mocks, no silent catches on the happy path. 
 
 E2E verification (no mocks) 
 Fresh scratch cwd, memory init + 3× hooks post-task --task ... --store-results true : 
 
 Before: hooks intelligence stats → 0 trajectories 
 After: 6 trajectories on disk + 3 pattern entries ( ~/.claude-flow/neural/stats.json ) 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.11 
 Closes: #2786 (the last remaining fix from the 2026-07-26 sweep).

</details>