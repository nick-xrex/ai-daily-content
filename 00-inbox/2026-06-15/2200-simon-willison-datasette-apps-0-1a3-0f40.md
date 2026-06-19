---
id: inbox_40a247d0
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jun/15/datasette-apps-2/#atom-everything"
author: ""
published_at: 2026-06-15T20:25:07+00:00
fetched_at: 2026-06-19T22:00:33.332191+00:00
content_hash: "0f403ca0c0679741607da6061037ae26d44ba84309846e3f1e55c5ca29dfc080"
lang: en
caption_quality: None
raw: true
topics: []
---

# datasette-apps 0.1a3

Release: datasette-apps 0.1a3 
 
 
 Fixed a bug where users without the create-app permission could still create apps. #27 
 Fixed a bug where it was impossible to grant permission to edit an app to users who were not the app's owner. The rules for edit/delete are now the same as view: if the app is private only the owner can modify it, otherwise permission is controlled by Datasette's regular permission system. #29 
 
 
 
 
 Tags: datasette