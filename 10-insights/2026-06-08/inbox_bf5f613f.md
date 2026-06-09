---
id: inbox_bf5f613f
date: 2026-06-08
source_ref: "[[00-inbox/2026-06-08/2202-hackernews-show-hn-gitdot-a-better-github-open-sour-e640]]"
title: "Show HN: Gitdot – A better GitHub. Open-source, written in Rust"
url: https://gitdot.io/
source: hackernews
published_at: 2026-06-08T16:52:11+00:00
fetched_at: 2026-06-09T22:16:35.226603+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Gitdot 是一款用 Rust 編寫的開源 GitHub 替代方案，已支援用戶註冊、組織創建、私有與公開倉庫創建及 GitHub 倉庫導入（含只讀鏡像和完整遷移）。網站設計靈感來自 CLI 工具（fzf、broot、vim 等），採用鍵盤驅動即時導航，性能目標為 100ms 首次內容繪製（FCP）。目前尚缺 issues、PRs 和 CI 功能，團隊表示軟體開發確實困難，但樂於分享現有進展。"
key_points:
  - "Rust 編寫、CLI 設計風格的 GitHub 替代品，採用鍵盤驅動導航而非傳統 Web UI"
  - "已實現：用戶/組織管理、倉庫創建推拉、GitHub 倉庫導入；缺失 issues、PRs、CI"
  - "性能目標 FCP 100ms，強調即時響應和鍵盤優化體驗"
tags: [github-alternative, rust, open-source, cli-design, dev-tools]
topics: []
importance: 3
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: Gitdot – A better GitHub. Open-source, written in Rust

Gitdot 是一款用 Rust 編寫的開源 GitHub 替代方案，已支援用戶註冊、組織創建、私有與公開倉庫創建及 GitHub 倉庫導入（含只讀鏡像和完整遷移）。網站設計靈感來自 CLI 工具（fzf、broot、vim 等），採用鍵盤驅動即時導航，性能目標為 100ms 首次內容繪製（FCP）。目前尚缺 issues、PRs 和 CI 功能，團隊表示軟體開發確實困難，但樂於分享現有進展。

### 重點
- Rust 編寫、CLI 設計風格的 GitHub 替代品，採用鍵盤驅動導航而非傳統 Web UI
- 已實現：用戶/組織管理、倉庫創建推拉、GitHub 倉庫導入；缺失 issues、PRs、CI
- 性能目標 FCP 100ms，強調即時響應和鍵盤優化體驗

**原文：** [hackernews](https://gitdot.io/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What works now: user signups, org creations, private&#x2F;public repos, and importing GitHub repositories (both as read-only mirrors and full migrations). So basically, you can create, push and pull to a repo, but we don&#x27;t have many features quite yet (issues, PRs, CI). What is a bit unique is: 1) we built it in Rust and 2) the website is a little odd. Its design is inspired by CLIs (e.g., fzf, broot, vim) instead of web apps, and as such, lacks some affordances that you might typically expect in favor of keyboard-driven instant navigations (we have the very ambitious goal of an FCP of 100ms). In case you&#x27;re curious, here&#x27;s how we we built it: https:&#x2F;&#x2F;gitdot.io&#x2F;designs We recognize that we&#x27;re making some bold claims here and are also well aware that we have much to learn. Building software is still hard, and that&#x27;s a fact we seem to relearn everyday. But we wanted to share what we built so far nonetheless. Cheers, thank y&#x27;all for reading, and till the next
—paul &amp; mikkel.

</details>