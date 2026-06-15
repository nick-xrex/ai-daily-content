---
id: inbox_5280192c
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jun/13/sqlite-column-provenance/#atom-everything"
author: ""
published_at: 2026-06-13T23:05:00+00:00
fetched_at: 2026-06-14T22:00:29.957123+00:00
content_hash: "3040ae3c438fe27754f2743b559baf16eb0e3349644ff56ee5b6d7f578198ec3"
lang: en
caption_quality: None
raw: true
topics: []
---

# Mapping SQLite result columns back to their source `table.column`

Research: Mapping SQLite result columns back to their source `table.column` 
 It would be neat if arbitrary SQL queries in Datasette could be rendered with additional information based on which columns from which tables were included in the results. 
 To build that, we would need to be able to look at a SQL query like select users.name, orders.total from users join orders on orders.user_id = users.id and programmatically identify the table.column for each result - navigating not just joins but also more complex syntax like CTEs. 
 I decided to set Claude Code (Opus 4.8, since Fable is currently banned by the US government ) on the problem. It found several promising solutions - one using apsw , another that uses ctypes to access the SQLite sqlite3_column_table_name() C function (which is not otherwise exposed to Python), and one using clever interrogation of the output of EXPLAIN . 
 
 
 Tags: python , sqlite , datasette