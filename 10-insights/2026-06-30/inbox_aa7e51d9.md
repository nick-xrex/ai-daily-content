---
id: inbox_aa7e51d9
date: 2026-06-30
source_ref: "[[00-inbox/2026-06-30/2331-rtk-releases-dev-0-43-1-rc-297-d46c]]"
title: "dev-0.43.1-rc.297"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.1-rc.297
source: rtk-releases
published_at: 2026-06-30T11:17:05+00:00
fetched_at: 2026-07-02T00:18:16.482160+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK v0.43.1-rc.297 强化 openclaw 插件对 rewrite 操作的退出码处理：Exit 0（Allow，自动应用）、Exit 1（Passthrough，无等价操作直接透传）、Exit 2（Deny，阻止调用）、Exit 3（Ask，需用户批准），使用 execFileSync 替代 execSync 防止 shell 注入，返回 [string | null, RewriteVerdict?] 元组供 before_tool_call hook 分别处理，解决 #2202。"
key_points:
  - "四层级 rewrite 退出码完整映射（Allow/Passthrough/Deny/Ask），对应自动应用、无处理、阻止、用户批准四种决策"
  - "采用 execFileSync 防止 shell 注入漏洞，提升安全性"
  - "before_tool_call hook 可根据 RewriteVerdict 作不同反应"
tags: [rtk, openclaw, security, error-handling, shell-injection]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.1-rc.297

RTK v0.43.1-rc.297 强化 openclaw 插件对 rewrite 操作的退出码处理：Exit 0（Allow，自动应用）、Exit 1（Passthrough，无等价操作直接透传）、Exit 2（Deny，阻止调用）、Exit 3（Ask，需用户批准），使用 execFileSync 替代 execSync 防止 shell 注入，返回 [string | null, RewriteVerdict?] 元组供 before_tool_call hook 分别处理，解决 #2202。

### 重點
- 四层级 rewrite 退出码完整映射（Allow/Passthrough/Deny/Ask），对应自动应用、无处理、阻止、用户批准四种决策
- 采用 execFileSync 防止 shell 注入漏洞，提升安全性
- before_tool_call hook 可根据 RewriteVerdict 作不同反应

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.1-rc.297)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(openclaw): handle exit code 3 from rtk rewrite 

 Interpret all RTK rewrite exit codes and respond appropriately:
 - Exit 0 (Allow): auto-apply rewrite
 - Exit 1 (Passthrough): no RTK equivalent, pass through unchanged
 - Exit 2 (Deny): block the call entirely
 - Exit 3 (Ask): rewrite available, require user approval via
 requireApproval with allow-once/deny decisions 

 Uses execFileSync (not execSync) to avoid shell injection. Returns
 a [string | null, RewriteVerdict?] tuple from tryRewrite so the
 before_tool_call hook can react to each verdict type. 

 "allow-always" omitted from allowedDecisions because OpenClaw does
 not auto-persist approval for plugin hooks — see:
 https://docs.openclaw.ai/plugins/plugin-permission-requests#troubleshooting 

 Closes #2202

</details>