---
id: inbox_b73dca1a
date: 2026-05-20
source_ref: "[[00-inbox/2026-05-20/0917-substack-pragmatic-engineer-why-rust-is-different-with-alice-ryhl-9bf0]]"
title: "Why Rust is different, with Alice Ryhl"
url: https://newsletter.pragmaticengineer.com/p/why-rust-is-different-with-alice
source: substack-pragmatic-engineer
published_at: 2026-05-20T16:22:00+00:00
fetched_at: 2026-05-21T09:31:47.671110+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google Android Rust 團隊主管 Alice Ryhl 闡明 Rust 的核心優勢。主要三點：(1) 記憶安全消除 C++ 整類漏洞（array off-by-one 在 C++ 變成安全漏洞，Rust 編譯期拒絕）；(2) 編譯器驅動開發——強制 null 檢查、`?` 操作符強制錯誤傳播，重構時改返回類型後編譯器自動檢查所有依賴代碼；(3) 版本管理用 Editions（2015/2018/2021/2024）允許破壞性改變而不強制全生態遷移。學習曲線主要挑戰不是語法而是數據結構設計（如循環引用）。重要里程碑：2025 年 12 月 Rust 在 Linux 內核從實驗轉正式穩定，標誌基礎設施採用開始加速。"
key_points:
  - "編譯器驅動開發把運行時崩潰移到編譯期：強制 null 檢查、錯誤傳播必須顯式，重構自動檢驗下游代碼完整性"
  - "記憶安全是系統級收益：消除 C++ 的 off-by-one / buffer overflow / use-after-free 整類漏洞，不是個案優化"
  - "Editions 版本管理：允許語言演進同時維持向後相容，同一生態可混用不同 edition 的庫——破解版本鎖定僵局"
tags: [rust-compiler-driven, memory-safety, linux-kernel, editions-versioning, error-propagation]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Why Rust is different, with Alice Ryhl

Google Android Rust 團隊主管 Alice Ryhl 闡明 Rust 的核心優勢。主要三點：(1) 記憶安全消除 C++ 整類漏洞（array off-by-one 在 C++ 變成安全漏洞，Rust 編譯期拒絕）；(2) 編譯器驅動開發——強制 null 檢查、`?` 操作符強制錯誤傳播，重構時改返回類型後編譯器自動檢查所有依賴代碼；(3) 版本管理用 Editions（2015/2018/2021/2024）允許破壞性改變而不強制全生態遷移。學習曲線主要挑戰不是語法而是數據結構設計（如循環引用）。重要里程碑：2025 年 12 月 Rust 在 Linux 內核從實驗轉正式穩定，標誌基礎設施採用開始加速。

### 重點
- 編譯器驅動開發把運行時崩潰移到編譯期：強制 null 檢查、錯誤傳播必須顯式，重構自動檢驗下游代碼完整性
- 記憶安全是系統級收益：消除 C++ 的 off-by-one / buffer overflow / use-after-free 整類漏洞，不是個案優化
- Editions 版本管理：允許語言演進同時維持向後相容，同一生態可混用不同 edition 的庫——破解版本鎖定僵局

**原文：** [substack-pragmatic-engineer](https://newsletter.pragmaticengineer.com/p/why-rust-is-different-with-alice)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Alice Ryhl from Google&#8217;s Android Rust team explains why developers love Rust, and what makes the language so powerful for building reliable software.

</details>