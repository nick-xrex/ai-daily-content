---
id: inbox_9cfcb3ef
source: hackernews
source_type: hn
url: "https://github.com/kageroumado/phosphene"
author: "kageroumado"
published_at: 2026-05-20T23:54:06+00:00
fetched_at: 2026-05-22T00:37:45.703738+00:00
content_hash: "ff6d588eebef80b69f14b93cadd06fa93392dbb8cba2a3781a5a9ede71a29de2"
lang: en
caption_quality: None
raw: true
topics: []
---

# Show HN: I reverse engineered Apple's video wallpapers

Ever since Apple introduced their video wallpapers I wanted to be able to put custom videos there. I decided to reverse engineer and see what I can do. I built Phosphene to sell it, but the existing competitors were polished enough that the time it would have taken to catch up wasn&#x27;t going to pay off. So I&#x27;m open-sourcing it. WallpaperExtensionKit.framework is what powers macOS wallpapers. It controls what’s shows in the Settings app. It took a lot of trial and error to replicate the behavior, but the result is that your custom wallpapers appear alongside everything else. I wanted to have an “add” button there too, but I couldn’t find a way to do so, so there’s a companion app that will put your video where it needs to be. Unlike Apple&#x27;s Aerials, the video keeps playing on the desktop (not just the lock screen). The renderer drives AVSampleBufferDisplayLayer directly with PTS-offset gapless looping, and pauses or downshifts based on thermal state, battery level, brightness, and window occlusion. It’s free and works well.