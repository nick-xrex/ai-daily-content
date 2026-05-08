---
id: inbox_77332cae
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t6hgsf/opus_46_does_better_research_gemini_31_has_better/"
author: "/u/ddp26"
published_at: 2026-05-07T17:32:58+00:00
fetched_at: 2026-05-08T07:37:42.332620+00:00
content_hash: "1835dc746f53ff7ef6b35a70f9bd7fcedd03e5ea2434c19761ef0f6d05e6cf9c"
lang: en
caption_quality: None
raw: true
topics: []
---

# Opus 4.6 does better research, Gemini 3.1 has better judgment

Figured this out by running 4 models: Claude Opus 4.6, GPT-5.4, Gemini 3.1 Pro, and Grok 4.20, on a benchmark of 1,417 binary forecasting questions resolving Oct–Dec 2025 with two evaluation conditions: agentic (each model does its own web research with tools) and fixed-evidence (every model receives the same ~12k-character research dossier, compiled using the Bosse et al. 2026 standardization methodology). Note, one limitation is that the fixed-evidence dossiers are themselves LM-produced, so we may be measuring how well each model interprets a particular standardized version of the evidence rather than judgement in the abstract. But that would indicate all four models drifting in the same direction. They didn't. GPT-5.4 and Grok 4.20 barely moved between conditions while Opus and Gemini swapped rank order (the opposite of what a broken or biased eval would produce.) To my knowledge this is the first direct evaluation of frontier models that decomposes performance into these research vs judgment stages. Calibration scores, refinement scores, and per-condition analysis: futuresearch.ai/opus-research-gemini-judgment Benchmark and leaderboard: evals.futuresearch.ai Our interpretation is that Opus is dramatically better at figuring out what to search for, deciding which pages to read, and pulling out the details that matter. But when you remove research tasks, that advantage goes away. When given the same information, Gemini brings sharper judgment over fixed evidence and weights more accurately on forecasting tasks. Calibration scores corroborate this in an interesting way: Opus's calibration drops sharply when search is taken away while Gemini's actually improves with the standardized dossier,. The asymmetry suggests Opus might be using its search trace as scaffolding for probability assignment (i.e., the act of going through the search loop is itself doing some of the epistemic work, separately from the information it surfaces.) This could be an over-interpretation of one benchmark, but I'd be interested if anyone's seen the same pattern in other domains. &#32; submitted by &#32; /u/ddp26 [link] &#32; [comments]