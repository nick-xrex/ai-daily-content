---
id: inbox_c5211870
source: superpowers-releases
source_type: rss
url: "https://github.com/obra/superpowers/releases/tag/v6.2.0"
author: "obra"
published_at: 2026-07-24T00:28:17+00:00
fetched_at: 2026-07-24T01:48:47.472547+00:00
content_hash: "33a8f7ebb408fb4ed559d1cd1721b0cd67a1b0f30ca9ddc627f349b78e3bca35"
lang: en
caption_quality: None
raw: true
topics: []
---

# v6.2.0

v6.2.0 (2026-07-23) 
 Subagent-Driven Development 
 Two structural changes to how SDD tracks progress and closes out review findings, both developed against live eval campaigns. 
 
 The workspace is now plan-scoped. .superpowers/sdd/ had no plan identity and no end-of-life: a follow-up plan in the same working tree could read the previous plan's ledger as its own progress (observed in the wild, with multiple contamination rounds and ad-hoc workarounds). sdd-workspace now requires the plan file and resolves a per-plan directory, .superpowers/sdd/&lt;plan-basename&gt;/ ; task-brief and review-package write into their plan's directory ( review-package gains the plan file as its first argument); the ledger names its plan on its first line; and the workspace is deleted once the final review is clean — git history is the durable record. Baseline evals showed controllers already refused foreign ledgers, but at a cost of 6–13 tool calls of cross-plan git forensics per resume; plan-scoping makes the answer structural instead. (25/25 baseline and GREEN eval runs documented in docs/specs/ and docs/plans/ .) 
 The review-fix loop resumes the implementer. The lifecycle restructure gives fix rounds resume-the-implementer semantics instead of fresh dispatches, adds a scoped re-review prompt ( re-review-prompt.md ) so the re-reviewer checks the fixes rather than re-reading the whole task, and installs a five-round circuit breaker with controller adjudication when it trips. SKILL.md reorganizes by lifecycle, and its Red Flags convert to the house rationalization-table form. 
 
 Skills 
 A branch-wide compression campaign: recap sections, social proof, and benefits-selling prose aimed at a reader who has already invoked the skill are gone, with every load-bearing argument folded into a rationalization-table row or moved to its point of use. Each cut was micro-tested with subagent probes, and the one cut that measurably degraded behavior was reworked rather than shipped. 
 
 testing-anti-patterns.md is now writing-good-tests.md . The TDD reference doc is rebuilt as a positive catalog — six rules that lead with the GOOD example — and absorbs a falsifiability discipline: name the production change that would fail the test, derive expectations independently of the code under test, and a closing mutation check. It closes two holes by name: the string-presence trap (grep-style tests on scripts, skills, and prompts counterfeit falsifiability — the observable is behavior, never text) and the change-detector trap (a constant assertion can fail and still protect nothing), each with a hard stop in the gate function. Trivial code and human prose earn no test; the trigger broadens from "adding mocks" to any test writing. 
 TDD's "Why Order Matters" rebuttals survive as rationalization rows. Deleting the section outright measurably degraded test-first behavior under "just write it, tests after" pressure (control 8/10 → treatment 5/10, corroborated on Claude and Codex), so each prose rebuttal now lives in its Common Rationalizations row — the section is gone but the arguments fire where an agent hits them mid-rationalization. 
 finishing-a-development-branch no longer offers to discard your work. The completion menu dates from when throwing away branches was routine; "Discard this work" next to "Merge" advertised destroying finished, passing work. Discard survives as an explicit-request-only path with the same typed-confirmation ritual. The same pass made PR creation forge-agnostic (your forge's CLI or the URL printed on push, not a blessed list of tools) and fixed a real bug: the worktree path was recomputed after cleanup had already changed directory, so provenance checks never matched and cleanup silently no-oped. 
 Recap and persuasion prose removed across the library. brainstorming , systematic-debugging , dispatching-parallel-agents , verification-before-completion , executing-plans , subagent-driven-development , requesting-code-review , receiving-code-review , using-git-worktrees , writing-plans , and writing-skills all drop their Bottom Line / Key Principles / Real-World Impact / Advantages sections; using-git-worktrees and finishing-a-development-branch convert their guard sections to the house Excuse/Reality rationalization table. 
 
 Windows 
 
 The SessionStart hook now dispatches via Git Bash. The hook's command string starts with a quoted path, which broke both shells Claude Code might hand it to: PowerShell parsed the quoted string as an expression and died with a parser error ( #1751 ), and cmd.exe's quote-stripping rule truncated the command when the profile path contained a metacharacter like ( ( #1918 ) — either way the bootstrap silently never loaded. The hook now declares shell: "bash" , which Claude Code ≥ 2.1.81 resolves to Git for Windows directly, and which surfaces an actionable install prompt when Git Bash is missing. Older Claude Code versions ignore the unknown key and behave as before. Verified end-to-end on Linux, Windows 11 with Git Bash under a hostile path, and Windows 11 without Git Bash. 
 
 Harness Support 
 
 Gemini CLI support is restored. The v6.1.0 removal (on the news that Google had EOLed the Gemini CLI) was premature; the install docs and the gemini-tools.md tool-mapping reference are back while permanent removal gets a proper evaluation. ( #1959 ) 
 
 Fixes 
 
 find-polluter.sh actually finds test files now. find . emits ./ -prefixed paths, so the documented -path "src/**/*.test.ts" pattern matched nothing — and wc -l on empty input then reported "Found 1". Fixed the prefix mismatch ( #2008 , #2011 ), plus two follow-ups: a caller-supplied ./ -prefixed pattern no longer double-prefixes into a never-matching form, and **/ is also matched collapsed so tests directly under the base directory ( src/top.test.ts vs src/**/*.test.ts ) aren't silently skipped. The script gains a deterministic test suite. 
 The Codex package script works beyond macOS. Deterministic-metadata tar flags were bsdtar-only spellings, staged file modes depended on two umasks canceling out, and the test's timestamp assertion parsed bsdtar's column layout in a US timezone. GNU tar now gets equivalent flags producing byte-identical headers, modes are pinned canonical, and the test asserts mtime via tarfile . 
 SDD's skill test no longer flakes. The file's worst case exceeded the runner's per-file ceiling (raised to 900s), and the assert helpers matched free-form model prose case-sensitively; matching is now case-insensitive and assert_order dumps output on failure so the next flake is diagnosable. 
 Docs and test cleanup after the v6.1.0 reference pruning. Dead links to the deleted claude-code-tools.md / copilot-tools.md are replaced with the current architecture ( #1969 ), a dangling #subagent-support anchor in the Antigravity reference is dropped ( #2010 ), and the Antigravity/Pi mapping tests assert only the surviving harness-specific mappings — scoped to the table so they fail again if it's deleted.