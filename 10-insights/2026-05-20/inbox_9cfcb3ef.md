---
id: inbox_9cfcb3ef
date: 2026-05-20
source_ref: "[[00-inbox/2026-05-20/0037-hackernews-show-hn-i-reverse-engineered-apple-s-vid-ff6d]]"
title: "Show HN: I reverse engineered Apple&#39;s video wallpapers"
url: https://github.com/kageroumado/phosphene
source: hackernews
published_at: 2026-05-20T23:54:06+00:00
fetched_at: 2026-05-22T00:43:18.612098+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開源專案 Phosphene：reverse engineer Apple WallpaperExtensionKit.framework，支援自訂視訊桌布。採用 AVSampleBufferDisplayLayer 直接驅動 PTS-offset gapless looping，根據溫度、電量、亮度、窗口遮擋動態調整暫停或降速。相比 Apple Aerials 的優勢：視訊可在桌面持續播放，非僅限鎖屏。"
key_points:
  - "WallpaperExtensionKit.framework reverse engineering 技術細節：PTS-offset gapless looping 實現無縫循環"
  - "自適應性能管理：根據 thermal state、battery level、brightness、window occlusion 動態調整播放"
  - "macOS 整合深度：自訂桌布與系統內置項並列於 Settings app，透過配套應用程式完成安裝"
tags: [macos-reverse-engineering, video-wallpaper, open-source, performance-optimization]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: I reverse engineered Apple's video wallpapers

開源專案 Phosphene：reverse engineer Apple WallpaperExtensionKit.framework，支援自訂視訊桌布。採用 AVSampleBufferDisplayLayer 直接驅動 PTS-offset gapless looping，根據溫度、電量、亮度、窗口遮擋動態調整暫停或降速。相比 Apple Aerials 的優勢：視訊可在桌面持續播放，非僅限鎖屏。

### 重點
- WallpaperExtensionKit.framework reverse engineering 技術細節：PTS-offset gapless looping 實現無縫循環
- 自適應性能管理：根據 thermal state、battery level、brightness、window occlusion 動態調整播放
- macOS 整合深度：自訂桌布與系統內置項並列於 Settings app，透過配套應用程式完成安裝

**原文：** [hackernews](https://github.com/kageroumado/phosphene)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ever since Apple introduced their video wallpapers I wanted to be able to put custom videos there. I decided to reverse engineer and see what I can do. I built Phosphene to sell it, but the existing competitors were polished enough that the time it would have taken to catch up wasn&#x27;t going to pay off. So I&#x27;m open-sourcing it. WallpaperExtensionKit.framework is what powers macOS wallpapers. It controls what’s shows in the Settings app. It took a lot of trial and error to replicate the behavior, but the result is that your custom wallpapers appear alongside everything else. I wanted to have an “add” button there too, but I couldn’t find a way to do so, so there’s a companion app that will put your video where it needs to be. Unlike Apple&#x27;s Aerials, the video keeps playing on the desktop (not just the lock screen). The renderer drives AVSampleBufferDisplayLayer directly with PTS-offset gapless looping, and pauses or downshifts based on thermal state, battery level, brightness, and window occlusion. It’s free and works well.

</details>