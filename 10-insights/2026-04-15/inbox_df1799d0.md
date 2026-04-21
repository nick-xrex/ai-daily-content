---
id: inbox_df1799d0
date: 2026-04-15
source_ref: "[[00-inbox/.../inbox_df1799d0]]"
title: "Zig 0.16.0 release notes: &#34;Juicy Main&#34;"
url: https://simonwillison.net/2026/Apr/15/juicy-main/#atom-everything
source: (resumed)
published_at: 2026-04-15T01:59:21+00:00
fetched_at: 2026-04-21T02:39:16.465712+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: ""
key_points:
tags: []
topics: []
importance: 1
novelty: 1
deep_dive_candidate: false
deep_dive_approved: false
---

## Zig 0.16.0 release notes: "Juicy Main"



### 重點

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/15/juicy-main/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://ziglang.org/download/0.16.0/release-notes.html#Juicy-Main">Zig 0.16.0 release notes: &quot;Juicy Main&quot;</a></strong></p>
Zig has <em>really good</em> release notes - comprehensive, detailed, and with relevant usage examples for each of the new features.</p>
<p>Of particular note in the newly released Zig 0.16.0 is what they are calling "Juicy Main" - a dependency injection feature for your program's <code>main()</code> function where accepting a <code>process.Init</code> parameter grants access to a struct of useful properties:</p>
<div class="highlight highlight-source-zig"><pre><span class="pl-k">const</span> <span class="pl-v">std</span> <span class="pl-k">=</span> <span class="pl-k">@import</span>(<span class="pl-s">"std"</span>);

<span class="pl-k">pub</span> <span class="pl-k">fn</span> <span class="pl-en">main</span>(<span class="pl-v">init</span>: <span class="pl-k">std.process.Init</span>) <span class="pl-k">!</span><span class="pl-k">void</span> {
    <span class="pl-c">/// general purpose allocator for temporary heap allocations:</span>
    <span class="pl-k">const</span> <span class="pl-v">gpa</span> <span class="pl-k">=</span> <span class="pl-v">init</span>.<span class="pl-v">gpa</span>;
    <span class="pl-c">/// default Io implementation:</span>
    <span class="pl-k">const</span> <span class="pl-v">io</span> <span class="pl-k">=</span> <span class="pl-v">init</span>.<span class="pl-v">io</span>;
    <span class="pl-c">/// access to environment variables:</span>
    <span class="pl-v">std</span>.<span class="pl-v">log</span>.<span class="pl-v">info</span>(<span class="pl-s">"{d} env vars"</span>, .{<span class="pl-v">init</span>.<span class="pl-v">environ_map</span>.<span class="pl-v">count</span>()});
    <span class="pl-c">/// access to CLI arguments</span>
    <span class="pl-k">const</span> <span class="pl-v">args</span> <span class="pl-k">=</span> <span class="pl-k">try</span> <span class="pl-v">init</span>.<span class="pl-v">minimal</span>.<span class="pl-v">args</span>.<span class="pl-v">toSlice</span>(
        <span class="pl-v">init</span>.<span class="pl-v">arena</span>.<span class="pl-v">allocator</span>()
    );
}</pre></div>

    <p><small></small>Via <a href="https://lobste.rs/s/4vvozb/zig_0_16_0_release_notes">Lobste.rs</a></small></p>


    <p>Tags: <a href="https://simonwillison.net/tags/zig">zig</a></p>

</details>
