---
id: inbox_9e9b10f8
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/19/claude-code-in-bun-in-rust/#atom-everything"
author: ""
published_at: 2026-07-19T03:54:09+00:00
fetched_at: 2026-07-19T22:00:30.526288+00:00
content_hash: "90d38b37f44d04b3f8d7b90e35bf4d05405a9c66d2a85057b9680b6e81279707"
lang: en
caption_quality: None
raw: true
topics: []
---

# Claude Code uses Bun written in Rust now

In Rewriting Bun in Rust Jarred Sumner made the following claim: 
 
 Claude Code v2.1.181 (released June 17th) and later use the Rust port of Bun. Startup got 10% faster on Linux but otherwise, barely anyone noticed. Boring is good. 
 
 I decided to have a poke at my own Claude Code installation to see if I could find evidence that it was using Bun written in Rust. 
 I found these two commands convincing: 
 strings ~/.local/bin/claude | grep -m1 'Bun v1'
 
 For me this outputs Bun v1.4.0 (macOS arm64) . The most recent release of Bun on GitHub is currently v1.3.14 from May 12th, so that v1.4.0 version number in Claude supports them shipping a preview of a not-yet-released Bun version. 
 ( Update : The Rust version has been released as Bun canary - running bun upgrade --canary will install this release .) 
 strings ~/.local/bin/claude | grep -Eo 'src/[[:alnum:]_./-]+\.rs'
 
 This outputs a list of 563 filenames , starting with these: 
 src/runtime/bake/dev_server/mod.rs
src/runtime/bake/production.rs
src/bundler/bundle_v2.rs
 
 It looks like Bun in Rust is indeed being run in production across millions of different devices. Like Jarred said, "Boring is good". 
 Update : Here's a neat trick from Ajan Raj : 
 cat &gt; /tmp/bun-version.ts &lt;&lt;'EOF'
console.log("embedded bun:", Bun.version);
process.exit(0);
EOF
BUN_OPTIONS="--preload=/tmp/bun-version.ts" claude --version
 
 This outputs 1.4.0 for me. 
 Here's the commit from May 17th that updated the version in package.json to 1.4.0. That version hasn't been changed since then, but also hasn't yet made it into a tagged release outside of canary . 

 Tags: bun , rust , anthropic , claude-code , jarred-sumner