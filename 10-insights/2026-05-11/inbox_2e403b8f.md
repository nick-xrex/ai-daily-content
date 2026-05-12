---
id: inbox_2e403b8f
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/0113-reddit-localllama-b9109-preemptive-fix-for-mtp-mmproj-fix-3b18]]"
title: "B9109: preemptive fix for mtp &amp; mmproj fix soon? It appears so"
url: https://www.reddit.com/r/LocalLLaMA/comments/1taihoo/b9109_preemptive_fix_for_mtp_mmproj_fix_soon_it/
source: reddit-localllama
published_at: 2026-05-11T22:20:53+00:00
fetched_at: 2026-05-12T01:22:36.828754+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llama.cpp B9109 提交針對 MTP（多模態 token 預填充）與 mmproj（圖像投影）崩潰進行預防性修復。提交包含三項關鍵改進：(1) spec 支持通過 draft context 處理圖像，解決之前圖像無法通過推測/draft context 的限制；(2) server 修復 mtmd（多模態處理器）的 draft 處理邏輯；(3) spec 支持並行 draft 模型同時運行，為 MTP 在多槽位場景規模化部署提供基礎。此組合表明開發團隊有針對性地推進 MTP + mmproj 兼容性，後續 PR #22673 可能近期推出。"
key_points:
  - "B9109 聚焦三項修復：draft context 支持圖像、mtmd draft 處理、並行 draft 基礎設施"
  - "直接解決 mmproj + MTP 已知崩潰問題，之前圖像無法通過 draft context 處理"
  - "並行 draft 支持為 MTP 規模部署奠基，預示後續關鍵 PR #22673 即將推出"
tags: [llama-cpp, multimodal, mtp, mmproj, draft-context]
topics: []
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## B9109: preemptive fix for mtp & mmproj fix soon? It appears so

llama.cpp B9109 提交針對 MTP（多模態 token 預填充）與 mmproj（圖像投影）崩潰進行預防性修復。提交包含三項關鍵改進：(1) spec 支持通過 draft context 處理圖像，解決之前圖像無法通過推測/draft context 的限制；(2) server 修復 mtmd（多模態處理器）的 draft 處理邏輯；(3) spec 支持並行 draft 模型同時運行，為 MTP 在多槽位場景規模化部署提供基礎。此組合表明開發團隊有針對性地推進 MTP + mmproj 兼容性，後續 PR #22673 可能近期推出。

### 重點
- B9109 聚焦三項修復：draft context 支持圖像、mtmd draft 處理、並行 draft 基礎設施
- 直接解決 mmproj + MTP 已知崩潰問題，之前圖像無法通過 draft context 處理
- 並行 draft 支持為 MTP 規模部署奠基，預示後續關鍵 PR #22673 即將推出

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1taihoo/b9109_preemptive_fix_for_mtp_mmproj_fix_soon_it/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Summary : spec : process images through the draft context — this directly addresses the mmproj + MTP crash. Previously images (mmproj) couldn't be processed through the speculative/draft context at all. This commit adds that capability. That's the actual fix in progress. server : fix mtmd draft processing — mtmd is the multimodal (mmproj) handler. Explicitly fixing draft processing for multimodal means they know about the crash and are targeting it. spec : support parallel drafts — this is infrastructure for running multiple draft models simultaneously, which is required for MTP to work properly at scale with parallel slots. The combination of all three in one build — multimodal draft fix, parallel draft support, and images through draft context — suggests this is a focused push to get MTP + mmproj working together. PR #22673 might not be far behind. &#32; submitted by &#32; /u/Bulky-Priority6824 [link] &#32; [comments]

</details>