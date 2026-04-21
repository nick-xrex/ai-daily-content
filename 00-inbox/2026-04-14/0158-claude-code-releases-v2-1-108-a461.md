---
id: inbox_9af0a8a9
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.108"
author: "ashwin-ant"
published_at: 2026-04-14T19:12:01+00:00
fetched_at: 2026-04-21T01:58:16.059735+00:00
content_hash: "a46163623d7b1e3a8834ca6468dbd3c6264146f1081abcf4047b5a8aedf91c9b"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.108

<h2>What's changed</h2>
<ul>
<li>Added <code>ENABLE_PROMPT_CACHING_1H</code> env var to opt into 1-hour prompt cache TTL on API key, Bedrock, Vertex, and Foundry (<code>ENABLE_PROMPT_CACHING_1H_BEDROCK</code> is deprecated but still honored), and <code>FORCE_PROMPT_CACHING_5M</code> to force 5-minute TTL</li>
<li>Added recap feature to provide context when returning to a session, configurable in /config and manually invocable with /recap; force with <code>CLAUDE_CODE_ENABLE_AWAY_SUMMARY</code> if telemetry disabled.</li>
<li>The model can now discover and invoke built-in slash commands like <code>/init</code>, <code>/review</code>, and <code>/security-review</code> via the Skill tool</li>
<li><code>/undo</code> is now an alias for <code>/rewind</code></li>
<li>Improved <code>/model</code> to warn before switching models mid-conversation, since the next response re-reads the full history uncached</li>
<li>Improved <code>/resume</code> picker to default to sessions from the current directory; press <code>Ctrl+A</code> to show all projects</li>
<li>Improved error messages: server rate limits are now distinguished from plan usage limits; 5xx/529 errors show a link to status.claude.com; unknown slash commands suggest the closest match</li>
<li>Reduced memory footprint for file reads, edits, and syntax highlighting by loading language grammars on demand</li>
<li>Added "verbose" indicator when viewing the detailed transcript (<code>Ctrl+O</code>)</li>
<li>Added a warning at startup when prompt caching is disabled via <code>DISABLE_PROMPT_CACHING*</code> environment variables</li>
<li>Fixed paste not working in the <code>/login</code> code prompt (regression in 2.1.105)</li>
<li>Fixed subscribers who set <code>DISABLE_TELEMETRY</code> falling back to 5-minute prompt cache TTL instead of 1 hour</li>
<li>Fixed Agent tool prompting for permission in auto mode when the safety classifier's transcript exceeded its context window</li>
<li>Fixed Bash tool producing no output when <code>CLAUDE_ENV_FILE</code> (e.g. <code>~/.zprofile</code>) ends with a <code>#</code> comment line</li>
<li>Fixed <code>claude --resume &lt;session-id&gt;</code> losing the session's custom name and color set via <code>/rename</code></li>
<li>Fixed session titles showing placeholder example text when the first message is a short greeting</li>
<li>Fixed terminal escape codes appearing as garbage text in the prompt input after <code>--teleport</code></li>
<li>Fixed <code>/feedback</code> retry: pressing Enter to resubmit after a failure now works without first editing the description</li>
<li>Fixed <code>--teleport</code> and <code>--resume &lt;id&gt;</code> precondition errors (e.g. dirty git tree, session not found) exiting silently instead of showing the error message</li>
<li>Fixed Remote Control session titles set in the web UI being overwritten by auto-generated titles after the third message</li>
<li>Fixed <code>--resume</code> truncating sessions when the transcript contained a self-referencing message</li>
<li>Fixed transcript write failures (e.g., disk full) being silently dropped instead of being logged</li>
<li>Fixed diacritical marks (accents, umlauts, cedillas) being dropped from responses when the <code>language</code> setting is configured</li>
<li>Fixed policy-managed plugins never auto-updating when running from a different project than where they were first installed</li>
</ul>