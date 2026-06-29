---
id: inbox_2127c190
source: rtk-releases
source_type: rss
url: "https://github.com/rtk-ai/rtk/releases/tag/v0.43.0"
author: "rtk-release-bot[bot]"
published_at: 2026-06-28T09:02:08+00:00
fetched_at: 2026-06-28T22:06:14.006750+00:00
content_hash: "64d1e5aeabd7a358844e44e90b603a55b0c887feaf426fa876f51524004f7d0f"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.43.0

0.43.0 (2026-06-28) 
 Features 
 
 oc: add Openshift CLI support with shared k8s filtering ( c7f493b ) 
 pulumi: add CLI filters for preview/up/destroy/refresh/stack ( ced70c6 ) 
 
 Bug Fixes 
 
 aws: guard the s3 ls and s3 sync/cp text emits ( 25a095e ) 
 core: never-worse output guard ( af81b08 ) 
 diff: report modified-only diffs and follow diff exit convention ( 3a73bcd ) 
 docker: make the agent's command authoritative for the guard baseline ( b52db52 ) 
 dotnet: keep raw fallback when parsed failures incomplete ( 5e7eab5 ) 
 dotnet: stop duplicating failures on failing test runs ( 2d9dc1a ), closes #2501 
 git: propagate exit code on git status failure in compact path ( 756c2a4 ) 
 git: propagate exit code when commit fails instead of reporting ok ( e36dd8c ), closes #2494 
 grep: correctly handle all flag shapes and never exceed raw output ( ee9e2f8 ) 
 grep: run the invoked engine instead of substituting rg for grep ( eafadce ) 
 grep: surface the engine error and exit code, add nothing ( 05f3c54 ) 
 grep: use portable --null in system grep fallback (BSD/macOS) ( abe7d42 ) 
 hook: rewrite pytest under uv run ( c8722bd ) 
 hook: treat uv run as a transparent prefix ( 34441dd ) 
 pipe: apply the never-worse guard ( 9d9ad7c ) 
 pulumi: keep Owner and version in pulumi-stack filter ( 5cfe4d5 ) 
 pulumi: keep stack identity in pulumi-stack filter ( 1f6e36b ) 
 read: make guard baseline faithful to cat/cat -n output ( 9a2ad90 ) 
 tests: resync &amp; list oc as passthrough for test ( 444f1c0 ) 
 vitest: add passthrough recovery hint ( f9469d1 ) 
 vitest: preserve explicit reporters ( e3f60e9 )