---
id: inbox_758b07a0
date: 2026-07-08
source_ref: "[[00-inbox/.../inbox_758b07a0]]"
title: "v3.25.4 — re-sign helpers manifest"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.25.4
source: ruflo-releases
published_at: 2026-07-08T02:21:39+00:00
fetched_at: 2026-07-10T00:44:43.366919+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.25.4 是元數據補丁版本，重新簽署 helpers.manifest.json（修復 #2593）。v3.25.3 發佈時本地環境無法訪問 GCP 簽署金鑰致無法自我修復，v3.25.4 在正確環境重新簽署了版本匹配 3.25.4 的 manifest。無源代碼或依賴變更，v3.25.3 所有修復均保留。所有三個 legacy dist-tags（latest、alpha、v3alpha）現指向 v3.25.4。"
key_points:
  - "純元數據補丁：Ed25519 簽名重新簽署，helpers.manifest.json 版本從 3.23.0 升至 3.25.4"
  - "修復原因：v3.25.3 因發佈環境缺乏 GCP 簽署金鑰而無法自我修復"
  - "無實質變更：保留 v3.25.3 的所有 10 項修復和 CI guard"
tags: [ruflo, manifest-signing]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.25.4 — re-sign helpers manifest

Ruflo v3.25.4 是元數據補丁版本，重新簽署 helpers.manifest.json（修復 #2593）。v3.25.3 發佈時本地環境無法訪問 GCP 簽署金鑰致無法自我修復，v3.25.4 在正確環境重新簽署了版本匹配 3.25.4 的 manifest。無源代碼或依賴變更，v3.25.3 所有修復均保留。所有三個 legacy dist-tags（latest、alpha、v3alpha）現指向 v3.25.4。

### 重點
- 純元數據補丁：Ed25519 簽名重新簽署，helpers.manifest.json 版本從 3.23.0 升至 3.25.4
- 修復原因：v3.25.3 因發佈環境缺乏 GCP 簽署金鑰而無法自我修復
- 無實質變更：保留 v3.25.3 的所有 10 項修復和 CI guard

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.25.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.25.4 — re-sign helpers manifest

Metadata-only patch closing the #2593 loop. 
 3.25.3 shipped the CI guard for stale helpers.manifest.json but couldn't self-repair its own release because the GCP signing secret wasn't accessible from the publish environment. 3.25.4 ships a properly-signed manifest at version 3.25.4 that matches the package version. 
 No source or dependency changes. All fixes from 3.25.3 remain — this only re-signs the shipped manifest. 
 Install 
 npx ruflo@3.25.4
npx ruflo@latest
npx claude-flow@v3alpha
npx @claude-flow/cli@alpha
 
 All three legacy dist-tags ( latest , alpha , v3alpha ) point to 3.25.4. 
 Packages 
 
 @claude-flow/cli@3.25.4 
 claude-flow@3.25.4 
 ruflo@3.25.4 
 
 🤖 Generated with RuFlo

</details>