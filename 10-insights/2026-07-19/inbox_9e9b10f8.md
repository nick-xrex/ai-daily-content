---
id: inbox_9e9b10f8
date: 2026-07-19
source_ref: "[[00-inbox/.../inbox_9e9b10f8]]"
title: "Claude Code uses Bun written in Rust now"
url: https://simonwillison.net/2026/Jul/19/claude-code-in-bun-in-rust/#atom-everything
source: simon-willison
published_at: 2026-07-19T03:54:09+00:00
fetched_at: 2026-07-20T00:55:23.821522+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.181（2026 年 6 月 17 日起）采用 Rust 编写的 Bun 运行时，Bun 版本为 v1.4.0（预览版，尚未官方发布，需运行 bun upgrade --canary 才能获得）。启动性能在 Linux 上提升 10%，其他平台基本无感知变化，展现了「无聊即好」的工程哲学——生产优化应以用户无感为目标。Simon Willison 通过二进制文件分析验证此事：strings 命令找到嵌入的 Bun 版本标识与 563 个 .rs 源文件路径，直接证实 Rust 版 Bun 已在数百万 Claude Code 用户设备上生产运行。这是 Rust 替代 JavaScript 进行关键路径优化的现实案例。"
key_points:
  - "Claude Code v2.1.181+ 采用 Bun v1.4.0（Rust 实现），Linux 启动快 10%，其他平台变化不明显；v1.4.0 为预览版，需 bun upgrade --canary 获得"
  - "二进制验证技巧：strings ~/.local/bin/claude | grep 'Bun v' 查询嵌入版本，563 个 .rs 文件引用直接证明 Rust 编译，同时证实 Bun 版本号信息"
  - "Bun Rust 端口已在生产规模部署（数百万 Claude Code 用户），体现「boring is good」工程实践：隐形性能提升优于可感知变化"
tags: [claude-code, bun, rust, runtime-optimization, anthropic]
topics: [foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude Code uses Bun written in Rust now

Claude Code v2.1.181（2026 年 6 月 17 日起）采用 Rust 编写的 Bun 运行时，Bun 版本为 v1.4.0（预览版，尚未官方发布，需运行 bun upgrade --canary 才能获得）。启动性能在 Linux 上提升 10%，其他平台基本无感知变化，展现了「无聊即好」的工程哲学——生产优化应以用户无感为目标。Simon Willison 通过二进制文件分析验证此事：strings 命令找到嵌入的 Bun 版本标识与 563 个 .rs 源文件路径，直接证实 Rust 版 Bun 已在数百万 Claude Code 用户设备上生产运行。这是 Rust 替代 JavaScript 进行关键路径优化的现实案例。

### 重點
- Claude Code v2.1.181+ 采用 Bun v1.4.0（Rust 实现），Linux 启动快 10%，其他平台变化不明显；v1.4.0 为预览版，需 bun upgrade --canary 获得
- 二进制验证技巧：strings ~/.local/bin/claude | grep 'Bun v' 查询嵌入版本，563 个 .rs 文件引用直接证明 Rust 编译，同时证实 Bun 版本号信息
- Bun Rust 端口已在生产规模部署（数百万 Claude Code 用户），体现「boring is good」工程实践：隐形性能提升优于可感知变化

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/19/claude-code-in-bun-in-rust/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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

</details>