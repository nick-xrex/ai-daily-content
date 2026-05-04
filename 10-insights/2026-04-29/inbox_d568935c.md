---
id: inbox_d568935c
date: 2026-04-29
source_ref: "[[00-inbox/.../inbox_d568935c]]"
title: "Bugs Rust won&#39;t catch"
url: https://corrode.dev/blog/bugs-rust-wont-catch/
source: hackernews
published_at: 2026-04-29T02:19:11+00:00
fetched_at: 2026-05-04T14:41:21.107832+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "深度安全審計揭示 Rust 語言在 uutils（Rust 版 coreutils）實現中未能防止的七大漏洞類別。最常見是時間檢查-時間使用(TOCTOU)競態漏洞，攻擊者可在路徑屬性檢查與後續操作間竄改為符號連結，如刪除檔案後建立同名檔案被重導至 /etc/shadow。不安全字串處理導致非 UTF-8 位元組無聲轉換為替代字符(comm 工具無聲損壞二進制資料)，expect() 在非 UTF-8 檔名上拋出 Panic，造成 cron 工作或 CI 管線意外中斷。其他漏洞還包括權限變更間的競態窗口、路徑字串比較無法識別符號連結或 ../ 繞過、Result 拋棄導致的無聲失敗，以及在進入攻擊者控制的 chroot 環境後才載入使用者資訊的信任邊界漏洞。"
key_points:
  - "Rust 未能防止七大漏洞類別：TOCTOU、不安全字串、Panic、權限競態、路徑比較、錯誤遺失、信任邊界後執行"
  - "TOCTOU 最常見：檢查後遭符號連結替換，remove 後建立可被重導至 /etc/shadow 等敏感位置"
  - "非 UTF-8 位元組無聲轉換(comm)、expect() 拋出 DoS(非 UTF-8 檔名中斷 cron)、Result 捨棄導致無聲失敗"
tags: [rust, security, vulnerabilities, toctou, memory-safety]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Bugs Rust won't catch

深度安全審計揭示 Rust 語言在 uutils（Rust 版 coreutils）實現中未能防止的七大漏洞類別。最常見是時間檢查-時間使用(TOCTOU)競態漏洞，攻擊者可在路徑屬性檢查與後續操作間竄改為符號連結，如刪除檔案後建立同名檔案被重導至 /etc/shadow。不安全字串處理導致非 UTF-8 位元組無聲轉換為替代字符(comm 工具無聲損壞二進制資料)，expect() 在非 UTF-8 檔名上拋出 Panic，造成 cron 工作或 CI 管線意外中斷。其他漏洞還包括權限變更間的競態窗口、路徑字串比較無法識別符號連結或 ../ 繞過、Result 拋棄導致的無聲失敗，以及在進入攻擊者控制的 chroot 環境後才載入使用者資訊的信任邊界漏洞。

### 重點
- Rust 未能防止七大漏洞類別：TOCTOU、不安全字串、Panic、權限競態、路徑比較、錯誤遺失、信任邊界後執行
- TOCTOU 最常見：檢查後遭符號連結替換，remove 後建立可被重導至 /etc/shadow 等敏感位置
- 非 UTF-8 位元組無聲轉換(comm)、expect() 拋出 DoS(非 UTF-8 檔名中斷 cron)、Result 捨棄導致無聲失敗

**原文：** [hackernews](https://corrode.dev/blog/bugs-rust-wont-catch/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Bugs Rust won't catch

</details>