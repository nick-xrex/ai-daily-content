---
id: inbox_e0f18e86
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-ruflo-releases-v3-29-0-statusline-promo-ux-security-key-7556]]"
title: "v3.29.0 — Statusline promo UX + security key rotation"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.29.0
source: ruflo-releases
published_at: 2026-07-14T16:58:19+00:00
fetched_at: 2026-07-14T22:10:02.246588+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.29.0 改進 statusline 表現層並執行安全關鍵的金鑰輪換。Statusline 第 3 行（promo）改為整行包裝在單一 OSC 8 超連結、顯示可見 (domain) 後綴、亮白加粗 \"manage: \" 尾部以標示命令、截斷用省略號替代靜默截斷。Windows 主控台閃爍緩解：三個 subprocess spawn 位置加 `windowsHide: true`，statusline 快取 TTL 60s → 300s（減少外部 wrapper spawn 約 5 倍）。安全面：RUFLO_HELPERS_PUBKEY 因洩露於 Claude Code 會話筆錄而輪換至 v2，新 Ed25519 金鑰對生成、舊版本銷毀、新公鑰烤入代碼、helpers 清單重新簽署。升級緊迫性高：≤3.28.0 用戶仍信任舊公鑰，攻擊者可偽造通過驗證的 helpers 清單。"
key_points:
  - "Statusline 整行 OSC 8 超連結 + 可見 (domain) 後綴，具體改進：whole-row-clickable、bright-white bold \"manage:\" 命令、ellipsis 截斷"
  - "快取 TTL 60s → 300s；windowsHide 在 statusline CLI delegation、safeExec helper、hook-handler detached spawn 三處啟用"
  - "RUFLO_HELPERS_PUBKEY v2 輪換：舊金鑰銷毀、新 Ed25519 金鑰對生成、helpers manifest 重新簽署；≤v3.28.0 用戶升級急迫"
tags: [ruflo, security, key-rotation, ux, statusline]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.29.0 — Statusline promo UX + security key rotation

Ruflo v3.29.0 改進 statusline 表現層並執行安全關鍵的金鑰輪換。Statusline 第 3 行（promo）改為整行包裝在單一 OSC 8 超連結、顯示可見 (domain) 後綴、亮白加粗 "manage: " 尾部以標示命令、截斷用省略號替代靜默截斷。Windows 主控台閃爍緩解：三個 subprocess spawn 位置加 `windowsHide: true`，statusline 快取 TTL 60s → 300s（減少外部 wrapper spawn 約 5 倍）。安全面：RUFLO_HELPERS_PUBKEY 因洩露於 Claude Code 會話筆錄而輪換至 v2，新 Ed25519 金鑰對生成、舊版本銷毀、新公鑰烤入代碼、helpers 清單重新簽署。升級緊迫性高：≤3.28.0 用戶仍信任舊公鑰，攻擊者可偽造通過驗證的 helpers 清單。

### 重點
- Statusline 整行 OSC 8 超連結 + 可見 (domain) 後綴，具體改進：whole-row-clickable、bright-white bold "manage:" 命令、ellipsis 截斷
- 快取 TTL 60s → 300s；windowsHide 在 statusline CLI delegation、safeExec helper、hook-handler detached spawn 三處啟用
- RUFLO_HELPERS_PUBKEY v2 輪換：舊金鑰銷毀、新 Ed25519 金鑰對生成、helpers manifest 重新簽署；≤v3.28.0 用戶升級急迫

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.29.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights 
 Two new user-facing CLI subcommands to control the statusline promo row: 
 
 ruflo funnel accept — skip the 24h disclosure grace so promo rotation starts immediately on the next render (instead of waiting a full day after first-render). 
 ruflo funnel open — open the currently-shown promo URL in your default browser. Terminal-independent, so it works on hosts that don't route clicks to the terminal's link handler (VS Code integrated terminal, some Windows configs, etc.). 
 
 Statusline row 3 (promo) improvements: 
 
 Whole row wrapped in one OSC 8 hyperlink — click anywhere on the row opens the URL. 
 Visible (domain) suffix so the destination is readable and copyable even where OSC 8 doesn't render. 
 Bright-white bold styling on the "manage: " tail so it visually reads as "shell command to type". 
 Ellipsis on truncation instead of silent mid-word chop. 
 
 Windows console-flash mitigations (partial — the primary cause is upstream at anthropics/claude-code#70200 ; we mitigate what our own subprocess calls contribute): 
 
 windowsHide: true on 3 subprocess spawn sites: statusline CLI delegation, statusline safeExec helper, hook-handler detached background refresh. 
 Statusline cache TTL bumped 60s → 300s, so the outer wrapper spawn (Claude Code's, not ours) fires ~5× less often. Promo/insight rotation still runs on its own tighter 20s clock. 
 New ruflo tracking issue: #2669 (mirrors upstream #70200, #14828, #66540). 
 
 Security 
 Helpers-signing key rotated ( RUFLO_HELPERS_PUBKEY v2). The previous private key was accidentally captured in a Claude Code session transcript today. Mitigation done at rotation time: 
 
 New Ed25519 keypair generated. 
 Old GCP Secret Manager version destroyed (not just disabled). 
 New pubkey baked into src/init/helper-signing.ts and scripts/verify-helpers.mjs . 
 Helpers manifest re-signed with the new key before publish. 
 
 Upgrade urgency: Users on ruflo ≤ 3.28.0 still trust the OLD (now-leaked) pubkey. An attacker with the leaked key could forge a helpers manifest that verifies on those old installs. Upgrade to v3.29.0 as soon as possible — new installs pick up the new pubkey and validate only manifests signed with the new key. 
 Compatibility 
 
 Semver MINOR (3.28.0 → 3.29.0) — additive CLI subcommands, no breaking changes. 
 Key rotation is atomic per-version — no dual-pubkey transition needed. Each CLI version's baked pubkey validates the manifest shipped with that same version. 
 
 PRs merged 
 
 #2671 — feat(funnel,statusline): accept + open subcommands, whole-row-clickable promo, Windows flash mitigations 
 #2673 — security: rotate helpers-signing key (RUFLO_HELPERS_PUBKEY v2) 
 
 Tracking issues 
 
 #2669 — Windows cmd/console flash (upstream anthropics/claude-code#70200 ) 
 
 Install 
 npx ruflo@latest init
 # or 
npm install -g @claude-flow/cli@3.29.0

</details>