---
id: inbox_9ce7b755
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Apr/14/replace-token-based-csrf/#atom-everything"
author: ""
published_at: 2026-04-14T23:58:53+00:00
fetched_at: 2026-04-21T01:58:22.527618+00:00
content_hash: "a2f8571045606dfa414edefb066f61bce058a9cdd53bd392d8620bdf8b4339c6"
lang: en
caption_quality: None
raw: true
topics: []
---

# datasette PR #2689: Replace token-based CSRF with Sec-Fetch-Site header protection

<p><strong><a href="https://github.com/simonw/datasette/pull/2689">datasette PR #2689: Replace token-based CSRF with Sec-Fetch-Site header protection</a></strong></p>
Datasette has long protected against CSRF attacks using CSRF tokens, implemented using my <a href="https://github.com/simonw/asgi-csrf">asgi-csrf</a> Python library. These are something of a pain to work with - you need to scatter forms in templates with <code>&lt;input type="hidden" name="csrftoken" value="{{ csrftoken() }}"&gt;</code> lines and then selectively disable CSRF protection for APIs that are intended to be called from outside the browser.</p>
<p>I've been following Filippo Valsorda's research here with interest, described in <a href="https://words.filippo.io/csrf/">this detailed essay from August 2025</a> and shipped <a href="https://tip.golang.org/doc/go1.25#nethttppkgnethttp">as part of Go 1.25</a> that same month.</p>
<p>I've now landed the same change in Datasette. Here's the PR description - Claude Code did much of the work (across 10 commits, closely guided by me and cross-reviewed by GPT-5.4) but I've decided to start writing these PR descriptions by hand, partly to make them more concise and also as an exercise in keeping myself honest.</p>
<blockquote>
<ul>
<li>New CSRF protection middleware inspired by Go 1.25 and <a href="https://words.filippo.io/csrf/">this research</a> by Filippo Valsorda. This replaces the old CSRF token based protection.</li>
<li>Removes all instances of <code>&lt;input type="hidden" name="csrftoken" value="{{ csrftoken() }}"&gt;</code> in the templates - they are no longer needed.</li>
<li>Removes the <code>def skip_csrf(datasette, scope):</code> plugin hook defined in <code>datasette/hookspecs.py</code> and its documentation and tests.</li>
<li>Updated <a href="https://docs.datasette.io/en/latest/internals.html#csrf-protection">CSRF protection documentation</a> to describe the new approach.</li>
<li>Upgrade guide now <a href="https://docs.datasette.io/en/latest/upgrade_guide.html#csrf-protection-is-now-header-based">describes the CSRF change</a>.</li>
</ul>
</blockquote>


    <p>Tags: <a href="https://simonwillison.net/tags/csrf">csrf</a>, <a href="https://simonwillison.net/tags/security">security</a>, <a href="https://simonwillison.net/tags/datasette">datasette</a>, <a href="https://simonwillison.net/tags/ai-assisted-programming">ai-assisted-programming</a></p>