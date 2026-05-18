---
id: inbox_f84c3de7
date: 2026-05-13
source_ref: "[[00-inbox/.../inbox_f84c3de7]]"
title: "CSP Allow-list Experiment"
url: https://simonwillison.net/2026/May/13/csp-allow/#atom-everything
source: simon-willison
published_at: 2026-05-13T04:50:45+00:00
fetched_at: 2026-05-18T03:30:56.372759+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者使用 GPT-5.5 xhigh 模型在 Codex desktop 應用中，實驗了在 CSP（內容安全政策）保護的沙箱 iframe 中加載應用的方法。實驗通過自訂 fetch() 攔截 CSP 錯誤，並將其傳遞給父視窗，父視窗提示使用者將該域名加入允許清單，然後刷新頁面。這提供了一個安全與使用者體驗權衡的實用模式，適用於需要動態擴展安全政策的受限環境。"
key_points:
  - "用自訂 fetch() 攔截 CSP 錯誤，動態擴展允許清單，無需手動編輯安全政策設定"
  - "Codex desktop app + GPT-5.5 xhigh 快速原型化複雜的安全相關功能"
  - "iframe 沙箱搭配動態 CSP 管理改善受限環境的應用靈活性"
tags: [csp, iframe, security, codex-desktop, gpt-5-5]
topics: [foundation_models.gpt]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## CSP Allow-list Experiment

作者使用 GPT-5.5 xhigh 模型在 Codex desktop 應用中，實驗了在 CSP（內容安全政策）保護的沙箱 iframe 中加載應用的方法。實驗通過自訂 fetch() 攔截 CSP 錯誤，並將其傳遞給父視窗，父視窗提示使用者將該域名加入允許清單，然後刷新頁面。這提供了一個安全與使用者體驗權衡的實用模式，適用於需要動態擴展安全政策的受限環境。

### 重點
- 用自訂 fetch() 攔截 CSP 錯誤，動態擴展允許清單，無需手動編輯安全政策設定
- Codex desktop app + GPT-5.5 xhigh 快速原型化複雜的安全相關功能
- iframe 沙箱搭配動態 CSP 管理改善受限環境的應用靈活性

**原文：** [simon-willison](https://simonwillison.net/2026/May/13/csp-allow/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# CSP Allow-list Experiment

Tool: CSP Allow-list Experiment 
 An experiment that shows that you can load an app in a CSP-protected sandboxed iframe (see previous note ) and have a custom fetch() that intercepts CSP errors and passes them up to the parent window... which can then prompt the user to add that domain to an allow-list and then refresh the page. 
 
 I built this one with GPT-5.5 xhigh running in the Codex desktop app. 
 
 
 Tags: content-security-policy , iframes , security

</details>