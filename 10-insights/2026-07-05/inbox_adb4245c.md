---
id: inbox_adb4245c
date: 2026-07-05
source_ref: "[[00-inbox/2026-07-05/2200-gitnexus-releases-release-candidate-v1-6-10-rc-3-5727]]"
title: "Release Candidate v1.6.10-rc.3"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.3
source: gitnexus-releases
published_at: 2026-07-05T15:33:24+00:00
fetched_at: 2026-07-05T22:05:12.562893+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.3 發布，面向早期測試者進行驗證。本次更新引入 CodeBuddy 和 Qoder 兩個 coding-agent 整合，開發者可在 IDE 中直接使用多個 AI agent 協助編程。實現全面 Codex 支援，包括 hooks API 和 plugin marketplace，相比先前的部分支援方案功能完整。修復代理伺服器環境下的安裝阻擋問題，onnxruntime-node 的 postinstall 過程現已能自癒 embeddings，大幅改善離線或受限網路環境的安裝穩定性。該 RC 版本基於 main 分支的 commit cdad478，開發者可透過 `npm install gitnexus@rc` 試用。"
key_points:
  - "新增 CodeBuddy 與 Qoder 兩個 coding-agent 整合，支援 IDE 內直接呼叫多個 AI agent"
  - "完整 Codex 支援，含 hooks 與 plugin marketplace（超越先前部分支援）"
  - "代理伺服器環境下的安裝穩定性修復，onnxruntime-node postinstall 能自癒 embeddings"
tags: [coding-agents, codex-integration, release-candidate]
topics: []
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.3

GitNexus v1.6.10-rc.3 發布，面向早期測試者進行驗證。本次更新引入 CodeBuddy 和 Qoder 兩個 coding-agent 整合，開發者可在 IDE 中直接使用多個 AI agent 協助編程。實現全面 Codex 支援，包括 hooks API 和 plugin marketplace，相比先前的部分支援方案功能完整。修復代理伺服器環境下的安裝阻擋問題，onnxruntime-node 的 postinstall 過程現已能自癒 embeddings，大幅改善離線或受限網路環境的安裝穩定性。該 RC 版本基於 main 分支的 commit cdad478，開發者可透過 `npm install gitnexus@rc` 試用。

### 重點
- 新增 CodeBuddy 與 Qoder 兩個 coding-agent 整合，支援 IDE 內直接呼叫多個 AI agent
- 完整 Codex 支援，含 hooks 與 plugin marketplace（超越先前部分支援）
- 代理伺服器環境下的安裝穩定性修復，onnxruntime-node postinstall 能自癒 embeddings

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.3 \n Target base: 1.6.10 (rc #3 )\n Source commit (main): cdad478 \n Release commit (versioned tree): 4051d8a \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(setup): add CodeBuddy and Qoder coding-agent integrations by @magyargergo in #2368 
 feat: full Codex support — hooks, plugin marketplace, and setup ( #2328 , supersedes #1131 ) by @magyargergo in #2369 
 fix: proxy-blocked installs survive onnxruntime-node postinstall and self-heal embeddings ( #2370 ) by @magyargergo in #2372 
 
 Full Changelog : v1.6.9...v1.6.10-rc.3

</details>