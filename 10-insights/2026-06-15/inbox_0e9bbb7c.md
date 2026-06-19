---
id: inbox_0e9bbb7c
date: 2026-06-15
source_ref: "[[00-inbox/2026-06-15/2200-simon-willison-datasette-apps-0-1a2-d39a]]"
title: "datasette-apps 0.1a2"
url: https://simonwillison.net/2026/Jun/15/datasette-apps/#atom-everything
source: simon-willison
published_at: 2026-06-15T17:26:11+00:00
fetched_at: 2026-06-19T22:10:15.811689+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-apps 0.1a2 發布，包含安全強化和用戶體驗改進。新增 apps-set-csp 權限控制 CSP 自定義，並引入可選插件白名單 allowed_csp_origins 供無特權用戶使用，Datasette Agent 應用創建工具強制執行相同規則（#24）。Stored query picker 現支持鍵盤導航，聚焦時顯示最近三個可訪問查詢，加速應用開發效率。修復：#fragment 鏈接不再被外部鏈接確認模態攔截，?full=1 全屏模式下的確認和日誌面板也已修正（#23、#26）。"
key_points:
  - "新權限 apps-set-csp + allowed_csp_origins 白名單：控制應用自定義 CSP origins，強制非特權用戶遵循安全白名單"
  - "Stored query picker 鍵盤導航及快速訪問：聚焦時顯示最近三個可訪問查詢，加速應用開發工作流"
  - "修復外部鏈接和全屏模式的 bug（#23、#26）"
tags: [datasette-apps, release, csp-security, ux-improvement, stored-queries]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-apps 0.1a2

datasette-apps 0.1a2 發布，包含安全強化和用戶體驗改進。新增 apps-set-csp 權限控制 CSP 自定義，並引入可選插件白名單 allowed_csp_origins 供無特權用戶使用，Datasette Agent 應用創建工具強制執行相同規則（#24）。Stored query picker 現支持鍵盤導航，聚焦時顯示最近三個可訪問查詢，加速應用開發效率。修復：#fragment 鏈接不再被外部鏈接確認模態攔截，?full=1 全屏模式下的確認和日誌面板也已修正（#23、#26）。

### 重點
- 新權限 apps-set-csp + allowed_csp_origins 白名單：控制應用自定義 CSP origins，強制非特權用戶遵循安全白名單
- Stored query picker 鍵盤導航及快速訪問：聚焦時顯示最近三個可訪問查詢，加速應用開發工作流
- 修復外部鏈接和全屏模式的 bug（#23、#26）

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/15/datasette-apps/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-apps 0.1a2 
 
 
 Custom network/CSP origins for apps are now guarded by a new apps-set-csp permission, with an optional allowed_csp_origins plugin allow-list for non-privileged users. The Datasette Agent app creation tool enforces the same rules. #24 
 Stored query picker now supports keyboard navigation and shows the three most recent accessible stored queries when focused. 
 #fragment links inside apps are no longer intercepted by the external-link confirmation modal. #23 
 Fixed link confirmation modal and logging panels in ?full=1 full-screen mode. #26 
 
 
 
 
 Tags: datasette

</details>