---
id: inbox_9ce7b755
date: 2026-04-14
source_ref: "[[00-inbox/.../inbox_9ce7b755]]"
title: "datasette PR #2689: Replace token-based CSRF with Sec-Fetch-Site header protection"
url: https://simonwillison.net/2026/Apr/14/replace-token-based-csrf/#atom-everything
source: (resumed)
published_at: 2026-04-14T23:58:53+00:00
fetched_at: 2026-04-21T02:40:32.031859+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 框架更新了跨站請求偽造（CSRF）防護機制，從基於 Token 的方案改用 Sec-Fetch-Site 請求頭檢驗。這套方法參考 Go 1.25 及 Filippo Valsorda 的資安研究。新方案移除了模板中所有隱藏 CSRF Token 的 input 標籤，廢棄了原有的 `skip_csrf` 外掛鉤點，簡化開發者體驗。該 PR 由 Claude Code 在人工密切指導下完成共 10 個 commit。官方文件已更新升級指南。"
key_points:
  - "Sec-Fetch-Site 請求頭取代 Token 式防護，移除所有 `<input type=\"hidden\" name=\"csrftoken\">` 標籤"
  - "廢棄 skip_csrf 外掛鉤點，統一安全策略實作"
  - "Claude Code 輔助開發，人工複審把關，10 個 commit 重構完成"
tags: [csrf-protection, web-security, datasette, sec-fetch-site, ai-assisted]
topics: []
importance: 3
novelty: 2
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette PR #2689: Replace token-based CSRF with Sec-Fetch-Site header protection

Datasette 框架更新了跨站請求偽造（CSRF）防護機制，從基於 Token 的方案改用 Sec-Fetch-Site 請求頭檢驗。這套方法參考 Go 1.25 及 Filippo Valsorda 的資安研究。新方案移除了模板中所有隱藏 CSRF Token 的 input 標籤，廢棄了原有的 `skip_csrf` 外掛鉤點，簡化開發者體驗。該 PR 由 Claude Code 在人工密切指導下完成共 10 個 commit。官方文件已更新升級指南。

### 重點
- Sec-Fetch-Site 請求頭取代 Token 式防護，移除所有 `<input type="hidden" name="csrftoken">` 標籤
- 廢棄 skip_csrf 外掛鉤點，統一安全策略實作
- Claude Code 輔助開發，人工複審把關，10 個 commit 重構完成

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/14/replace-token-based-csrf/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://github.com/simonw/datasette/pull/2689">datasette PR #2689: Replace token-based CSRF with Sec-Fetch-Site header protection</a></strong></p>
Datasette has long protected against CSRF attacks using CSRF tokens, implemented using my <a href="https://github.com/simonw/asgi-csrf">asgi-csrf</a> Python library. These are something of a pain to work with - you need to scatter forms in templates with <code>&lt;input type="hidden" name="csrftoken" value="{{ csrftoken() }}"&gt;</code> lines and then selectively disable CSRF protection for APIs that are intended to be called from outside the browser.</p>
<p>I've been following Filippo Valsorda's research here with interest, described in <a href="https://words.filippo.io/csrf/">this detailed essay from August 2025</a> and shipped <a href="https://tip.golang.org/doc/go1.25#nethttppkgnethttp">as part of Go 1.25</a> that same month.</p>
<p>I've now landed the same change in Datasette. Here's the PR description - Claude Code did much of the work (across 10 commits, closely guided by me and cross-reviewed by GPT-5.4) but I've decided to start writing these PR descriptions by hand, partly to make them more concise and also as an exercise in keeping myself honest.</p>
<blockquote>
<ul>
<li>New CSRF protection middleware inspired by Go 1.25 and <a href="https://words.filippo.io/csrf/">this research</a> by Filippo Valsorda. This replaces the old CSRF token based protection.</li>
<li>Removes all instances of <code>&lt;input type="hidden" name="csrftoken" value="{{ csrftoken() }}"&gt;</code> in the templates - they are no longer needed.</li>
<li>Removes the <code>def skip_csrf(datasette, scope):</code> plugin hook defined in <code>datasette/hookspecs.py</code> and its documentation and tests.</li>
<li>Updated <a href="https://docs.datasette.io/en/latest/internals.html#csrf-protection">CSRF protection documentation</a> to describe the new approach.</li>
<li>Upgrade guide now <a href="https://docs.datasette.io/en/latest/upgrade_guide.html#csrf-protection-is-now-header-based">describes the CSRF change</a>.</li>
</ul>
</blockquote>


    <p>Tags: <a href="https://simonwillison.net/tags/csrf">csrf</a>, <a href="https://simonwillison.net/tags/security">security</a>, <a href="https://simonwillison.net/tags/datasette">datasette</a>, <a href="https://simonwillison.net/tags/ai-assisted-programming">ai-assisted-programming</a></p>

</details>
