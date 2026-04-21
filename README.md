# AI Daily Content

Auto-generated daily AI news digest content. This is the content repo; the pipeline code lives at [`nick-xrex/ai-daily-digest`](https://github.com/nick-xrex/ai-daily-digest).

## Structure

```
00-inbox/     # Raw fetched items (frontmatter + body from RSS/HN/etc.)
10-insights/  # Per-item AI summaries (繁體中文)
20-daily/     # Daily rollups — TOP 3 + category summaries
90-config/    # sources.yaml, keywords.yaml, youtube.yaml
```

## Usage

Daily rollups live under `20-daily/YYYY-MM-DD.md`. Each contains:
- 🔥 今日 TOP 3 — with links to full insights + original articles
- 📚 分類摘要 — by topic
- Optional Mermaid diagrams (auto-rendered by GitHub) for architecture / workflow / timeline content

## Automation

- **02:00 Asia/Taipei**: primary fetch + summarize
- **08:00**: sweep + email delivery
- **14:00**: sweep only

Pipeline source: `nick-xrex/ai-daily-digest`.
