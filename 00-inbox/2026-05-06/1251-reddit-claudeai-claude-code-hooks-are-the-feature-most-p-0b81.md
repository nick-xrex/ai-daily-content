---
id: inbox_41c72661
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t53m01/claude_code_hooks_are_the_feature_most_people/"
author: "/u/EastMove5163"
published_at: 2026-05-06T05:22:58+00:00
fetched_at: 2026-05-06T12:51:31.363056+00:00
content_hash: "0b813d540974d5c8b03478f9e003f5525857da103ccb7252d264d37c12ca85b9"
lang: en
caption_quality: None
raw: true
topics: []
---

# Claude Code hooks are the feature most people skip. Spoiler: they're really useful

<!-- SC_OFF --><div class="md"><p>Hooks let you run shell commands at specific points in Claude's workflow: before it uses a tool, after it edits a file, when a session starts. I set these up a while back and they changed how I work with Claude Code more than almost anything else.</p> <p>My most useful setup: auto-run my test suite after every file edit. Claude makes a change, tests run automatically, Claude sees the output and adjusts. It closes the feedback loop so I'm not manually running tests between every round of edits. The other one I use constantly is auto-formatting on save. Claude edits a file, prettier runs, the file is clean before Claude even moves on.</p> <p>You can also use hooks to block Claude from touching certain directories. If you have a folder that should never be auto-modified, a hook that exits with an error when Claude tries to write there will stop it reliably. Much cleaner than hoping your instructions hold.</p> <p>What lifecycle events are you hooking into, if any? Curious what setups other people have found useful.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/EastMove5163"> /u/EastMove5163 </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t53m01/claude_code_hooks_are_the_feature_most_people/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t53m01/claude_code_hooks_are_the_feature_most_people/">[comments]</a></span>