---
id: inbox_b8e845cf
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fb3826d6b0e3418096f8fe6c6d5b6f9cbb66990f2"
author: "magyargergo"
published_at: 2026-07-19T15:36:22+00:00
fetched_at: 2026-07-19T22:00:20.700108+00:00
content_hash: "8fe09be83e218dca3d3e5a979517396774a8c058085a8fcf4e0228d415739576"
lang: en
caption_quality: None
raw: true
topics: []
---

# rc/b3826d6b0e3418096f8fe6c6d5b6f9cbb66990f2: fix(ci): unblock the review agent dispatch and publisher lanes (#2567)

fix(ci): unblock the review agent dispatch and publisher lanes 
 
 The first workflow_dispatch validation run surfaced two defects: 
 
 setup-node rejects cache: false (the YAML boolean arrives as the 
string 'false' and v6 fails with "Caching for 'false' is not 
supported"), killing the analyze job before the isolation preflight. 
Omitting the input is the supported way to disable caching. 
 The publisher held only issues: write , but GITHUB_TOKEN needs 
 pull-requests: write to create issue comments on a pull request, 
so even the safe-failure comment died with "Resource not accessible 
by integration". 
 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
Claude-Session: https://claude.ai/code/session_01Va5uu9Ar3e45QZ5xFsG4AZ 
 
 test(ci): align the publisher permission contract with PR commenting 
 
 The workflow contract test pinned the publisher to pull-requests: read, 
which is exactly the permission set that made comment publication fail. 
Encode the corrected scope and assert the publisher still cannot write 
repository contents. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
Claude-Session: https://claude.ai/code/session_01Va5uu9Ar3e45QZ5xFsG4AZ 
 
 Co-authored-by: Claude Fable 5 noreply@anthropic.com