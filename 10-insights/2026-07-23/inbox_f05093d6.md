---
id: inbox_f05093d6
date: 2026-07-23
source_ref: "[[00-inbox/2026-07-23/0148-claude-mem-releases-v13-12-2-the-merge-sweep-af3b]]"
title: "v13.12.2 — The Merge Sweep"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.12.2
source: claude-mem-releases
published_at: 2026-07-23T09:14:21+00:00
fetched_at: 2026-07-24T01:58:32.643591+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.12.2 一次 merge 54 個社群 bug-fix PRs（評估全部 157 個待審 PR）。導入新 merge rubric（docs/merge-rubric.md）制度化標準：只接受根因修復，禁止守衛、斷路器、回退、重試、fail-open 或自癒機制。Windows 修復：zombie 進程 port 偵測、console-flash sweep（bun.exe 直接生成繞過 cmd.exe 的 8191 字元 PATH 限制、pathToFileURL ESM 偵測、UTF-8 BOM 容許、spaced profile 路徑引用修復）。Search & data integrity：Chroma 相關性排名保留（被 recency 靜默覆蓋 → 復原）、type filter、date filter 榮譽、merged-project hydrate、limit 在 reorder 後應用、Chroma watermark gap 持久化、concurrent SQLite 讀鎖。感謝 30+ 社群開發者。"
key_points:
  - "新 merge rubric 制度化根因修復並禁止防禦編程（no guards/circuit-breakers/retries/self-healing），與實驗室 evals 對齐後實施"
  - "Windows 關鍵修復：bun.exe 路徑解析 + 直接生成（繞過 cmd.exe 的 PATH 截斷），pathToFileURL ESM 偵測，spaced profile 引用存活"
  - "Data integrity sweep：Chroma 自動 reorder 會靜默覆蓋相關性排名 → 復原 Chroma relevance ranking；孤立行和 watermark gap 修復防止永遠 stranded；SQLite concurrent 讀嚴格鎖"
tags: [claude-mem, merge-rubric, windows-reliability, data-integrity, community-contribution]
topics: [foundation_models.claude]
importance: 5
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## v13.12.2 — The Merge Sweep

claude-mem v13.12.2 一次 merge 54 個社群 bug-fix PRs（評估全部 157 個待審 PR）。導入新 merge rubric（docs/merge-rubric.md）制度化標準：只接受根因修復，禁止守衛、斷路器、回退、重試、fail-open 或自癒機制。Windows 修復：zombie 進程 port 偵測、console-flash sweep（bun.exe 直接生成繞過 cmd.exe 的 8191 字元 PATH 限制、pathToFileURL ESM 偵測、UTF-8 BOM 容許、spaced profile 路徑引用修復）。Search & data integrity：Chroma 相關性排名保留（被 recency 靜默覆蓋 → 復原）、type filter、date filter 榮譽、merged-project hydrate、limit 在 reorder 後應用、Chroma watermark gap 持久化、concurrent SQLite 讀鎖。感謝 30+ 社群開發者。

### 重點
- 新 merge rubric 制度化根因修復並禁止防禦編程（no guards/circuit-breakers/retries/self-healing），與實驗室 evals 對齐後實施
- Windows 關鍵修復：bun.exe 路徑解析 + 直接生成（繞過 cmd.exe 的 PATH 截斷），pathToFileURL ESM 偵測，spaced profile 引用存活
- Data integrity sweep：Chroma 自動 reorder 會靜默覆蓋相關性排名 → 復原 Chroma relevance ranking；孤立行和 watermark gap 修復防止永遠 stranded；SQLite concurrent 讀嚴格鎖

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.12.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

v13.12.2 — The Merge Sweep 
 54 community bug-fix PRs merged in one pass. Every open PR in the repo (157 total) was evaluated against a strict rubric — now codified in docs/merge-rubric.md : root-cause corrections only, with no guards, circuit breakers, fallbacks, retries, fail-open modes, self-healing machinery, truncation, or bolt-on second systems. 
 Windows 
 
 Zombie-held worker ports now detected correctly, ending infinite startup-failure loops ( #3356 ) 
 Console-flash sweep: windowsHide on every remaining live spawn path — git, npm, IDE detection, Codex installer, worker wrapper, taskkill, MCP launcher ( #3335 , #3320 , #3319 , #3305 , #2921 ) 
 bun.exe resolved to its absolute path and spawned directly, skipping cmd.exe (which silently drops &gt;8191-char PATH) ( #3235 , #3247 ) 
 Worker ESM main detection via pathToFileURL ( #3318 ); UTF-8 BOM tolerated in settings JSON read ( #3307 ) 
 Start-Process argument quoting survives spaced profile paths ( #3293 ); codex.cmd shim quoting fixed ( #3220 ) 
 PowerShell call operator ( &amp; ) added to Cursor/Windsurf hook commands ( #2507 ) 
 Missing Windows credential treated as absent instead of a spurious read failure ( #3265 ); tests run on Windows via fileURLToPath ( #3312 ) 
 
 Search &amp; data integrity 
 
 Semantic search preserves Chroma relevance ranking instead of silently reordering by recency ( #3325 ) 
 type=&lt;custom&gt; and non-category type filters no longer return empty results ( #3281 ); date_from / date_to honored in worker searches ( #3201 ) 
 Merged-project records hydrate correctly on semantic-search ID lookups and worktree adoption patches Chroma by typed doc targets ( #3342 ) 
 getUserPromptsByIds applies limit after relevance reordering ( #3347 ) 
 Chroma watermark gaps persist across bootstrap and live sync — no more permanently stranded rows ( #3364 ); duplicate IDs reconciled in place, stopping unbounded index growth ( #3268 ) 
 Custom observation types preserved instead of being misclassified as bugfix ( #3185 ); files_modified is now evidence-gated from actual write/edit tool events ( #3180 ) 
 Tool payloads no longer double-encoded in observation prompts ( #3150 ) 
 Context generation opens SQLite strictly read-only under concurrent sessions ( #3233 ) 
 MCP tools/list advertises only tools that work in the active runtime ( #3065 ); search routes to the Postgres-backed /v1/search in server runtime when it can serve the query faithfully ( #3082 ) 
 
 Worker &amp; providers 
 
 CLAUDE_MEM_MAX_CONCURRENT_AGENTS actually enforced via atomic slot reservations ( #3294 ) 
 Observations attributed to the current prompt's project after repo/worktree switches ( #3237 ); claimed batches preserved on auth-failure prose instead of being deleted ( #3236 ) 
 Worker startup waits through cold and concurrent readiness windows ( #3238 ) 
 Observer thinking disabled so thinking-only skips can't trigger harness re-prompts ( #3256 ); observer SDK sessions no longer pollute the user's project transcript tree ( #2942 ) 
 CLAUDE_MEM_TIER_SUMMARY_MODEL honored on OpenAI-compatible providers ( #3257 ) 
 Stale default model ids updated: Sonnet/Opus ( #3187 ) and retired Gemini models ( #3283 ) 
 __IMPORTANT MCP tool renamed important_workflow so strict clients can load the server ( #3295 ); tsconfig moduleResolution moved to bundler for TS 6 ( #3296 ) 
 
 Hooks, context &amp; installers 
 
 CLAUDE_MEM_EXCLUDED_PROJECTS honored on session-start injection ( #3358 ); subagents without MCP tools skip file-context injection ( #3341 ) 
 ~ expanded in CLAUDE_MEM_DATA_DIR ( #3350 ) and CLAUDE_CODE_PATH ( #3275 ); Homebrew uvx path shared with the worker preflight ( #3276 ) 
 SessionStart no longer dumps raw JSON at the top of every session ( #3282 ); Codex no longer receives a duplicate context payload ( #3241 ) and transcripts continue after archival ( #3223 ) 
 Worktree compound keys preserved from subdirectories ( #3304 ) 
 Azure AI Foundry auth env preserved through the SDK sanitizer ( #3314 ); invalid corpus names return 400 instead of 500 ( #3251 ) 
 Codex plugin cache actually installs during setup — best-effort wrapper deleted, fail-fast ( #3066 ) 
 mergeSettings and server bootstrap no longer destroy top-level settings keys ( #2928 , #2929 ) 
 version-bump skill frontmatter name matches its directory ( #3313 ) 
 
 Docs 
 
 New docs/merge-rubric.md — the acceptance bar for bug-fix PRs, distilled from this sweep. 
 
 Thanks to everyone who contributed fixes: @rodboev , @stantheman0128 , @huiihao , @jamincollins , @quinnmacro , @justindeisler , @davertor , @BBD-Resources , @povesma , @laihenyi , @LPdsgn , @KJJisBetter , @Steaeavean , @XX888QM , @rapidtackgithub , @SamuelZ12 , @DNA , @girish-kanjiyani7 , @E0993599799 , @eslonaguiar , @desmond-rai , @Reese-max , @Wasabi-221 , @mic2112 , @yaw-sh , @derrickchwong , @SaadSharif4 , @katsugtgz , @manoi-bms , @percy-raskova , @ShiroKSH , @eralpozcan , @anupamme , @SejiL , @remten341 , @danscMax , @jamesdsizemore , and the PostHog bot fleet.

</details>