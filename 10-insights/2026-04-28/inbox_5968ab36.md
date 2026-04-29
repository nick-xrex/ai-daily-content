---
id: inbox_5968ab36
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0657-medium-stackademic-metrics-clickhouse-and-the-simple-setup-3f75]]"
title: "Metrics, ClickHouse, and the “Simple” Setup That Wasn’t"
url: https://blog.stackademic.com/metrics-clickhouse-and-the-simple-setup-that-wasnt-fc123e6b190f?source=rss----d1baaa8417a4---4
source: medium-stackademic
published_at: 2026-04-28T07:02:19+00:00
fetched_at: 2026-04-29T07:17:47.380553+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: ""
key_points:
tags: []
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Metrics, ClickHouse, and the “Simple” Setup That Wasn’t



### 重點

**原文：** [medium-stackademic](https://blog.stackademic.com/metrics-clickhouse-and-the-simple-setup-that-wasnt-fc123e6b190f?source=rss----d1baaa8417a4---4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<blockquote>Part 1: Why I walked away from Telegraf and shifted my mental model on observability.</blockquote><p>Collecting metrics is easy. Shipping them to an analytical database without losing your mind? That’s the hard part.</p><figure><img alt="" src="https://cdn-images-1.medium.com/max/1024/1*7nmyRyNNVfA6gvevEvTKcg.png" /></figure><p>We’ve all been there. You start with a straightforward requirement: <em>“Collect system metrics (CPU, memory, GPU) and store them in ClickHouse for analysis.”</em> It’s a classic observability use case. You collect, you send, you query. Simple, right?</p><p>But as I quickly learned, there is a massive gap between “running a tool” and “building a system.”</p><h3>The Initial Approach: The Telegraf Trap</h3><p>I started where most people do: <strong>Telegraf</strong>.</p><p>It’s the industry standard for a reason. It’s plugin-based, mature, and has a massive community. This was also my formal introduction to TOML configuration. At first, the mindset was: <em>“I just need to write a config and hit run.”</em></p><p>But configuration isn’t just syntax — it’s the DNA of your system’s behavior.</p><p>My goals were modest:</p><ol><li>Capture host-level metrics.</li><li>Monitor GPU performance.</li><li>Pipe it all into <strong>ClickHouse</strong> for high-speed OLAP queries.</li><li>Prepare it for dashboard.</li></ol><h3>Where the Gears Started Grinding</h3><p>On paper, Telegraf is a Swiss Army knife. In practice, I found myself trying to cut down a tree with a corkscrew. I hit four specific walls:</p><ul><li><strong>The ClickHouse Gap:</strong> There wasn’t a native, “it-just-works” output plugin for ClickHouse that handled the schema the way I envisioned.</li><li><strong>The “Black Box” Problem:</strong> Debugging why a metric didn’t arrive where it should have felt unintuitive.</li><li><strong>Rigidity:</strong> As my requirements grew, my TOML file became a brittle monolith.</li><li><strong>Tool vs. Task:</strong> I was spending 80% of my time fighting the tool and only 20% thinking about my data.</li></ul><h3>The Shift: From Configs to Pipelines</h3><p>This is where the lightbulb finally flickered on. I had been thinking in a linear, static way:</p><p>Write config → Run tool → Expect output</p><p>That’s a recipe for brittle infrastructure. I needed to stop thinking about “tools” and start thinking about <strong>Data Flow</strong>. I needed a mental model that looked like this:</p><p>Data source → Transformation → Destination</p><p>The problem wasn’t that Telegraf was “bad” — it was that I lacked control over the <strong>Transformation</strong> step. I needed a system that treated data like a moving stream, not a static delivery.</p><h3>Why I Switched to Vector</h3><p>I realized that for a ClickHouse-backed pipeline, I needed three things: <strong>Granular control, visibility, and flexibility.</strong></p><p>That search led me to <strong>Vector</strong>. Unlike traditional collectors, Vector doesn’t just “send” data; it builds a directed acyclic graph (DAG) of your information. It treats configuration as a <strong>pipeline</strong>.</p><h3>Coming up in Part 2…</h3><p>In the next post, I’ll dive into the technical implementation of Vector, why the <em>sources → transforms → sinks</em> model is a game-changer for ClickHouse, and how my architecture finally stabilized.</p><p><strong>The lesson so far?</strong> Tools don’t solve problems - understanding systems does.</p><img alt="" height="1" src="https://medium.com/_/stat?event=post.clientViewed&amp;referrerSource=full_rss&amp;postId=fc123e6b190f" width="1" /><hr /><p><a href="https://blog.stackademic.com/metrics-clickhouse-and-the-simple-setup-that-wasnt-fc123e6b190f">Metrics, ClickHouse, and the “Simple” Setup That Wasn’t</a> was originally published in <a href="https://blog.stackademic.com">Stackademic</a> on Medium, where people are continuing the conversation by highlighting and responding to this story.</p>

</details>