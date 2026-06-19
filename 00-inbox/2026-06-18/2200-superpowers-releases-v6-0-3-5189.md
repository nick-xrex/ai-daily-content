---
id: inbox_9b3424e8
source: superpowers-releases
source_type: rss
url: "https://github.com/obra/superpowers/releases/tag/v6.0.3"
author: "obra"
published_at: 2026-06-18T22:45:19+00:00
fetched_at: 2026-06-19T22:00:30.970747+00:00
content_hash: "5189c5467495b0ce02d0a8cefad058191be43c1f9e865c407a99303c1e452b6a"
lang: en
caption_quality: None
raw: true
topics: []
---

# v6.0.3

Subagent-Driven Development 
 
 SDD scratch files moved out of .git/ . Claude Code treats .git/ as a protected path and denies agent writes there, so an implementer subagent writing its report into .git/sdd/ got blocked mid-run. Task briefs, implementer reports, review diffs, and the progress ledger now live in a self-ignoring .superpowers/sdd/ directory in the working tree — kept out of git status and out of commits, and resolved per worktree by a shared sdd-workspace helper. One caveat: because the workspace is git-ignored working-tree scratch, git clean -fdx will delete the progress ledger; recover from git log if that happens. ( #1780 )