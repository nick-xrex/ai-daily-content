---
id: inbox_73042656
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Apr/13/servo-crate-exploration/#atom-everything"
author: ""
published_at: 2026-04-13T15:19:00+00:00
fetched_at: 2026-04-21T01:58:22.533930+00:00
content_hash: "4a4a4da41e0f18c418bd1bc3883e2686160179fc2794dfcc5553ae102bda0fef"
lang: en
caption_quality: None
raw: true
topics: []
---

# Exploring the new `servo` crate

<p><strong>Research:</strong> <a href="https://github.com/simonw/research/tree/main/servo-crate-exploration#readme">Exploring the new `servo` crate</a></p>
    <p>In <a href="https://servo.org/blog/2026/04/13/servo-0.1.0-release/">Servo is now available on crates.io</a> the Servo team announced the initial release of the <a href="https://crates.io/crates/servo">servo</a> crate, which packages their browser engine as an embeddable library.</p>
<p>I set Claude Code for web <a href="https://github.com/simonw/research/pull/108">the task</a> of figuring out what it can do, building a CLI tool for taking screenshots using it and working out if it could be compiled to WebAssembly.</p>
<p>The <code>servo-shot</code> Rust tool it built works pretty well:</p>
<pre><code>git clone https://github.com/simonw/research
cd research/servo-crate-exploration/servo-shot
cargo build
./target/debug/servo-shot https://news.ycombinator.com/
</code></pre>
<p>Here's the result:</p>
<p><img alt="An accurately rendered screenshot of the Hacker News homepage" src="https://static.simonwillison.net/static/2026/servo-hn.png" /></p>
<p>Compiling Servo itself to WebAssembly is not feasible due to its heavy use of threads and dependencies like SpiderMonkey, but Claude did build me <a href="https://simonw.github.io/research/servo-crate-exploration/html5ever-wasm-demo/www/">this playground page</a> for trying out a WebAssembly build of the <code>html5ever</code> and <code>markup5ever_rcdom</code> crates, providing a tool for turning fragments of HTML into a parse tree.</p>
    
        <p>Tags: <a href="https://simonwillison.net/tags/research">research</a>, <a href="https://simonwillison.net/tags/browsers">browsers</a>, <a href="https://simonwillison.net/tags/rust">rust</a>, <a href="https://simonwillison.net/tags/webassembly">webassembly</a>, <a href="https://simonwillison.net/tags/claude-code">claude-code</a>, <a href="https://simonwillison.net/tags/servo">servo</a></p>