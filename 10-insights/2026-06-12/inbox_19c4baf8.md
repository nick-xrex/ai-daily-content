---
id: inbox_19c4baf8
date: 2026-06-12
source_ref: "[[00-inbox/.../inbox_19c4baf8]]"
title: "v3.10.44 — CI OOM fix, Windows plugin install"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.44
source: ruflo-releases
published_at: 2026-06-12T20:52:24+00:00
fetched_at: 2026-06-13T04:10:04.849570+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.44 修復兩個關鍵問題。首先 CI OOM（#2348）：rescueAgentdbEmbedder 中存在互相遞迴 generateEmbedding → bridgeGenerateEmbedding → agentdb.embedder.embed（被 monkey-patch）→ generateEmbedding，微任務驅動導致堆內存單調增長至 V8 限制（4GB）。修復改為委託 bridge-free 的 generateLocalEmbedding，並收緊 rescue 探測（要求 backend === 'onnx'）。其次 Windows 插件安裝（#2366）：npm 是 bash shim 無法直接執行，Node 18.20.2+ 拒絕生成 .cmd/.bat，路由改為通過 cmd.exe /d /s /c npm <args>。"
key_points:
  - "monkey-patch 互相遞迴洩漏：generateEmbedding 的 patch 鏈形成閉包，微任務驅動堆單調增長至 SIGABRT，修復隔離為 bridge-free leaf"
  - "Windows npm 跨平台修復：bash shim + CVE-2024-27980 限制要求通過 cmd.exe 包裝，3 個呼叫點（install/uninstall/upgrade）統一路由"
  - "rescue 虛假陽性防衛：原先接受任何非零向量，現在要求 backend === 'onnx' 識別真實嵌入"
tags: [ruflo, ci-oom, windows-support, monkey-patch, cross-platform]
topics: []
importance: 4
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.44 — CI OOM fix, Windows plugin install

Ruflo v3.10.44 修復兩個關鍵問題。首先 CI OOM（#2348）：rescueAgentdbEmbedder 中存在互相遞迴 generateEmbedding → bridgeGenerateEmbedding → agentdb.embedder.embed（被 monkey-patch）→ generateEmbedding，微任務驅動導致堆內存單調增長至 V8 限制（4GB）。修復改為委託 bridge-free 的 generateLocalEmbedding，並收緊 rescue 探測（要求 backend === 'onnx'）。其次 Windows 插件安裝（#2366）：npm 是 bash shim 無法直接執行，Node 18.20.2+ 拒絕生成 .cmd/.bat，路由改為通過 cmd.exe /d /s /c npm <args>。

### 重點
- monkey-patch 互相遞迴洩漏：generateEmbedding 的 patch 鏈形成閉包，微任務驅動堆單調增長至 SIGABRT，修復隔離為 bridge-free leaf
- Windows npm 跨平台修復：bash shim + CVE-2024-27980 限制要求通過 cmd.exe 包裝，3 個呼叫點（install/uninstall/upgrade）統一路由
- rescue 虛假陽性防衛：原先接受任何非零向量，現在要求 backend === 'onnx' 識別真實嵌入

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.44)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.10.44 — CI OOM fix, Windows plugin install

Patch release bundling two fixes that landed since 3.10.43. 
 Fixes 
 #2348 — break embedder-rescue mutual recursion ( #2312 ) 
 v3-ci.yml 's trajectory-graph-edges smoke had been disabled ( continue-on-error: true ) since the test process OOM'd at 4 GB on the Linux runner. Bisection ruled out the suspected SONA endTrajectory / EWC path. The actual cause was a closed cycle: 
 generateEmbedding (bridge-first)
 → bridgeGenerateEmbedding
 → agentdb.embedder.embed ← monkey-patched by rescueAgentdbEmbedder
 → generateEmbedding ← cycle closes here
 
 Microtask-driven, so no stack overflow — just monotonic heap growth to V8's limit, then SIGABRT. memory-bridge.ts 's rescueAgentdbEmbedder now delegates to a new generateLocalEmbedding export (bridge-free leaf chain) rather than the bridge-first generateEmbedding . The rescue probe is also tightened — previously it accepted any non-zero vector as "real," which the deterministic hash fallback also satisfies, so it cheerfully "rescued" a mock with another mock. New probe requires backend === 'onnx' . 
 The CI gate is re-enabled ( continue-on-error: true removed). 
 #2366 — Windows plugin install/uninstall/upgrade (community contribution) 
 On Windows, PluginManager failed every npm lifecycle command with two distinct Node failure modes: 
 
 spawn npm ENOENT — npm on Windows is a bash shim with no .exe , so execFile('npm', ...) can't resolve it. 
 spawn EINVAL — Node refuses to spawn .cmd / .bat files directly since 18.20.2 / 20.12.2 ( CVE-2024-27980 ). 
 
 All three call sites (install, uninstall, upgrade) now route through a runNpm helper that invokes cmd.exe /d /s /c npm &lt;args&gt; on Windows. POSIX path is unchanged. Argument safety is maintained by the existing validatePackageName regex gate plus Node's array-form argument quoting — security-audited for cmd.exe metacharacter injection (the version-spec characters ^ , &lt; , &gt; , = that the regex allows are inert inside Node's quoted args under cmd /s ). 
 Community PR by @danielsOink — thanks! 
 Held from this batch 
 
 #2301 (community, hive-mind --dangerously-skip-permissions ) — fix for the kebab→camel parser drop is correct on the activation half but the --no-auto-permissions deny case fails locally: the parser uses yargs-style negation ( autoPermissions: false ) which the predicate doesn't read. Comment posted on the PR with the proposed third-clause fix; will land in the next batch. 
 #2342 (vitest 1.x → 4.1.8 for GHSA-5xrq-8626-4rwp ) — CONFLICTING against current main; needs rebase + author confirmation of test-suite compatibility with the major version jump. 
 
 Install / upgrade 
 npx ruflo@latest init # 3.10.44 
npx @claude-flow/cli@latest # 3.10.44 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) and all three dist-tags ( latest , alpha , v3alpha ) verified at 3.10.44. 
 Diff 
 main...v3.10.43 — PRs #2348 , #2366 plus the release bump. 
 🤖 Generated with RuFlo

</details>