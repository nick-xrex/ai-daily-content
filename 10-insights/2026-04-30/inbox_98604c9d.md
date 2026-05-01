---
id: inbox_98604c9d
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-simon-willison-the-zig-project-s-rationale-for-their-fi-fb5f]]"
title: "The Zig project&#39;s rationale for their firm anti-AI contribution policy"
url: https://simonwillison.net/2026/Apr/30/zig-anti-ai/#atom-everything
source: simon-willison
published_at: 2026-04-30T01:24:23+00:00
fetched_at: 2026-05-01T13:03:04.433121+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Zig 程式語言專案實施了業界最嚴格的反 LLM 貢獻政策，禁止所有 LLM 輔助提交。而 Anthropic 在 2025 年 12 月收購的 Bun JavaScript 運行時開發了自己的 Zig fork，最近實現了 4 倍編譯性能提升，但因 Zig 的禁令不計畫將改進上游提交。Zig 副總裁提出「貢獻者撲克」哲學：開源項目應投資「貢獻者」而非單次「貢獻」，LLM 輔助會破壞這種長期人才培養的核心價值。"
key_points:
  - "Zig 禁止所有 LLM 輔助貢獻，Bun fork 實現 4 倍編譯性能但無法上游提交"
  - "「貢獻者撲克」框架：開源項目應透過 PR 審查投資新貢獻者成長，而非單純合併代碼"
  - "Anthropic 收購的 Bun 與開源 Zig 的治理衝突，突顯 AI 輔助對社群協作模式的結構性影響"
tags: [zig, open-source-governance, contributor-retention, ai-ethics, bun-runtime]
topics: []
importance: 5
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## The Zig project's rationale for their firm anti-AI contribution policy

Zig 程式語言專案實施了業界最嚴格的反 LLM 貢獻政策，禁止所有 LLM 輔助提交。而 Anthropic 在 2025 年 12 月收購的 Bun JavaScript 運行時開發了自己的 Zig fork，最近實現了 4 倍編譯性能提升，但因 Zig 的禁令不計畫將改進上游提交。Zig 副總裁提出「貢獻者撲克」哲學：開源項目應投資「貢獻者」而非單次「貢獻」，LLM 輔助會破壞這種長期人才培養的核心價值。

### 重點
- Zig 禁止所有 LLM 輔助貢獻，Bun fork 實現 4 倍編譯性能但無法上游提交
- 「貢獻者撲克」框架：開源項目應透過 PR 審查投資新貢獻者成長，而非單純合併代碼
- Anthropic 收購的 Bun 與開源 Zig 的治理衝突，突顯 AI 輔助對社群協作模式的結構性影響

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/30/zig-anti-ai/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><a href="https://ziglang.org/">Zig</a> has one of the most stringent <a href="https://ziglang.org/code-of-conduct/">anti-LLM policies</a> of any major open source project:</p>
<blockquote>
<p>No LLMs for issues.</p>
<p>No LLMs for pull requests.</p>
<p>No LLMs for comments on the bug tracker, including translation. English is encouraged, but not required. You are welcome to post in your native language and rely on others to have their own translation tools of choice to interpret your words.</p>
</blockquote>
<p>The most prominent project written in Zig may be the <a href="https://bun.com/">Bun</a> JavaScript runtime, which was <a href="https://bun.com/blog/bun-joins-anthropic">acquired by Anthropic</a> in December 2025 and, unsurprisingly, makes heavy use of AI assistance.</p>
<p>Bun operates its own fork of Zig, and recently <a href="https://x.com/bunjavascript/status/2048427636414923250">achieved a 4x performance improvement</a> on Bun compile after adding "parallel semantic analysis and multiple codegen units to the llvm backend". Here's <a href="https://github.com/oven-sh/zig/compare/upgrade-0.15.2%E2%80%A6upgrade-0.15.2-fast">that code</a>. But <a href="https://twitter.com/bunjavascript/status/2048428104893542781">@bunjavascript says</a>:</p>
<blockquote>
<p>We do not currently plan to upstream this, as Zig has a strict ban on LLM-authored contributions.</p>
</blockquote>
<p>(Update: here's <a href="https://ziggit.dev/t/bun-s-zig-fork-got-4x-faster-compilation-times/15183/19">a Zig core contributor</a> providing details on why they wouldn't accept that particular patch independent of the LLM issue - parallel semantic analysis is a long planned feature but has implications "for the Zig language itself".)</p>
<p>In <a href="https://kristoff.it/blog/contributor-poker-and-ai/">Contributor Poker and Zig's AI Ban</a> (<a href="https://lobste.rs/s/ifcyr1/contributor_poker_zig_s_ai_ban">via Lobste.rs</a>) Zig Software Foundation VP of Community Loris Cro explains the rationale for this strict ban. It's the best articulation I've seen yet for a blanket ban on LLM-assisted contributions:</p>
<blockquote>
<p>In successful open source projects you eventually reach a point where you start getting more PRs than what you’re capable of processing. Given what I mentioned so far, it would make sense to stop accepting imperfect PRs in order to maximize ROI from your work, but that’s not what we do in the Zig project. Instead, <strong>we try our best to help new contributors to get their work in, even if they need some help getting there</strong>. We don’t do this just because it’s the “right” thing to do, but also <strong>because it’s the smart thing to do</strong>.</p>
</blockquote>
<p>Zig values contributors over their contributions. Each contributor represents an investment by the Zig core team - the primary goal of reviewing and accepting PRs isn't to land new code, it's to help grow new contributors who can become trusted and prolific over time.</p>
<p>LLM assistance breaks that completely. It doesn't matter if the LLM helps you submit a <em>perfect</em> PR to Zig - the time the Zig team spends reviewing your work does nothing to help them add new, confident, trustworthy contributors to their overall project.</p>
<p>Loris explains the name here:</p>
<blockquote>
<p>The reason I call it “contributor poker” is because, just like people say about the actual card game, “you play the person, not the cards”. In contributor poker, you bet on the contributor, not on the contents of their first PR.</p>
</blockquote>
<p>This makes a lot of sense to me. It relates to an idea I've seen circulating elsewhere: if a PR was mostly written by an LLM, why should a project maintainer spend time reviewing and discussing that PR as opposed to firing up their own LLM to solve the same problem?</p>

    <p>Tags: <a href="https://simonwillison.net/tags/anthropic">anthropic</a>, <a href="https://simonwillison.net/tags/zig">zig</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/ai-ethics">ai-ethics</a>, <a href="https://simonwillison.net/tags/open-source">open-source</a>, <a href="https://simonwillison.net/tags/javascript">javascript</a>, <a href="https://simonwillison.net/tags/ai-assisted-programming">ai-assisted-programming</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/bun">bun</a></p>

</details>