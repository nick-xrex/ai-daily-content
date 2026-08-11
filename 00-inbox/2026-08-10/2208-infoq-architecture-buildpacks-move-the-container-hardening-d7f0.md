---
id: inbox_bebeffd9
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/08/buildpacks-dockerfile-patching/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Mark Silvester"
published_at: 2026-08-10T07:00:00+00:00
fetched_at: 2026-08-10T22:08:47.698702+00:00
content_hash: "d7f0860f839c5081004631d090987afab050ead4c403b4bc6a5149ed3fa9e467"
lang: en
caption_quality: None
raw: true
topics: []
---

# Buildpacks Move the Container Hardening Control Point Away From the Dockerfile

Cloud Native Buildpacks, which graduated within the CNCF in July 2026, move base image choice out of per-service Dockerfiles into a single builder owned by platform engineering, enabling fleet-wide patching. BellSoft's hardened Paketo builder is the latest sign that vendors now treat the builder, not the Dockerfile, as the container security control point. By Mark Silvester