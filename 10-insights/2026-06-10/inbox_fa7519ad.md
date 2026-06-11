---
id: inbox_fa7519ad
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_fa7519ad]]"
title: "v13.5.4"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.5.4
source: claude-mem-releases
published_at: 2026-06-10T07:22:17+00:00
fetched_at: 2026-06-11T00:23:32.320297+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.5.4 修復遙測地理位置洩露。posthog-node SDK 預設假設伺服器部署，設置 disableGeoip: true，導致本機 worker 的 worker_started/session_compressed 等事件喪失位置資訊（~98.5% 「unknown location」）。修復：改傳 disableGeoip: false，允許 PostHog 在攝取端透過請求 IP 推導粗粒度位置（國家/地區/城市），IP 隨後丟棄。隱私保證不變：原始 IP 地址永不由客戶端附加或儲存，僅於攝取時短暫使用，聲稱遵守。"
key_points:
  - "遙測地理位置修復：disableGeoip 從 true 改為 false，解除 PostHog 攝取端的 GeoIP 功能抑制，恢復粗粒度位置推導 (country/region/city)"
  - "隱私設計確認：raw IP 從不由客戶端上傳，只於 PostHog 攝取端短暫用於位置查詢後丟棄，IP 承諾不變"
  - "透明度提升：遙測文件及同意畫面更新，明確揭露攝取端推導的位置資訊蒐集行為"
tags: [telemetry-privacy, geolocation-fix, posthog-integration]
topics: [foundation_models.claude]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.5.4

claude-mem v13.5.4 修復遙測地理位置洩露。posthog-node SDK 預設假設伺服器部署，設置 disableGeoip: true，導致本機 worker 的 worker_started/session_compressed 等事件喪失位置資訊（~98.5% 「unknown location」）。修復：改傳 disableGeoip: false，允許 PostHog 在攝取端透過請求 IP 推導粗粒度位置（國家/地區/城市），IP 隨後丟棄。隱私保證不變：原始 IP 地址永不由客戶端附加或儲存，僅於攝取時短暫使用，聲稱遵守。

### 重點
- 遙測地理位置修復：disableGeoip 從 true 改為 false，解除 PostHog 攝取端的 GeoIP 功能抑制，恢復粗粒度位置推導 (country/region/city)
- 隱私設計確認：raw IP 從不由客戶端上傳，只於 PostHog 攝取端短暫用於位置查詢後丟棄，IP 承諾不變
- 透明度提升：遙測文件及同意畫面更新，明確揭露攝取端推導的位置資訊蒐集行為

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.5.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.5.4

Fixed 
 
 Telemetry geolocation: closed the ~98.5% "unknown location" gap. The posthog-node SDK assumes server deployments and stamps $geoip_disable: true on every event by default. claude-mem's worker runs on the user's own machine, so this needlessly suppressed PostHog's ingest-side GeoIP on all worker events ( worker_started , session_compressed , context_injected , ...). The client now passes disableGeoip: false , letting PostHog derive coarse location (country / region / city) at ingestion — from the request IP, which is then discarded. CLI events ( install_* ) were already unaffected. 
 
 Privacy 
 
 No change to the IP promise: raw IP addresses are still never attached to events by the client and never stored — the sender IP is used transiently at ingest for the coarse-location lookup, then discarded. 
 The telemetry docs ( https://docs.claude-mem.ai/telemetry ) and the npx claude-mem telemetry enable consent screen now disclose the ingest-derived coarse location. 
 
 Tests 
 
 New regression test asserts the PostHog client is constructed with disableGeoip: false (telemetry suite now 58 tests, all passing). 
 
 🤖 Generated with Claude Code

</details>