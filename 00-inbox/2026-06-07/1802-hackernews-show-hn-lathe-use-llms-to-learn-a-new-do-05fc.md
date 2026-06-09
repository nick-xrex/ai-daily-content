---
id: inbox_7734ec97
source: hackernews
source_type: hn
url: "https://github.com/devenjarvis/lathe"
author: "devenjarvis"
published_at: 2026-06-07T11:16:46+00:00
fetched_at: 2026-06-08T18:02:26.479463+00:00
content_hash: "05fc37177480ca66b6f3a8885aadbaeda585baca22e0924fbb4490cae175a13b"
lang: en
caption_quality: None
raw: true
topics: []
---

# Show HN: Lathe – Use LLMs to learn a new domain, not skip past it

Hey HN! Lathe is an experiment in using LLMs to teach me something new, instead of doing the work for me. It generates a hands-on, source-backed tutorial for any technical topic you want to learn. Then you work through it yourself by reading and typing the code by hand ( gasp ) in a local UI built for exactly that. It&#x27;s a Go CLI plus LLM agent skills (Claude Code &#x2F; Cursor &#x2F; Codex). You prompt something like &quot;&#x2F;lathe build a 3D slicer in Erlang&quot;, run `lathe serve` to spin up a local webapp, and read it in your browser. Every tutorial comes with the things that have made self-learning a pleasant experience for me in the past: - table of contents that follows along as you scroll
- side-notes that nudge you to think
- exercises for the reader
- sources backing up the content that you can use to take you deeper To help make up for the lack of human brainpower behind the tutorial, you can also ask questions about the content, have another LLM verify the tutorial actually compiles and runs, or extend it with another part (no more &quot;Part 4 of 6&quot; that hasn&#x27;t seen an update since 2021). I didn&#x27;t build lathe to replace human-written tutorials. I built lathe because I _love_ human-written tutorials, but wanted to learn technical domains where no good human-written tutorial exists yet (building a 3D slicer from scratch, making embedded Zig approachable, etc). There&#x27;s a longer story in the README about how I got started with programming through PSP homebrew tutorials, and why losing that to LLMs bugged me enough to build this. I&#x27;m not here to sell you anything (there&#x27;s nothing close to a VC-backed startup here :D). It&#x27;s an LLM, and its output is usually good but not perfect by any means. So far, my experience is that because you&#x27;re the one typing and actually engaged, you catch the weird stuff (and I&#x27;m finding that pushing back on it is its own kind of learning). And yes, it&#x27;s vibecoded, because it&#x27;s low scope, low risk, and scratching a personal itch. I run it on Claude Code + macOS personally, other setups should work but I haven&#x27;t been able to verify them yet. If you can find resources to learn something that was written by a human, read that first. But Lathe is here to fill in the gaps when that isn&#x27;t the case, and I hope it serves as an example where LLMs can help us think better, rather than less. Repo: https:&#x2F;&#x2F;github.com&#x2F;devenjarvis&#x2F;lathe Would love your feedback if you decide to check it out!