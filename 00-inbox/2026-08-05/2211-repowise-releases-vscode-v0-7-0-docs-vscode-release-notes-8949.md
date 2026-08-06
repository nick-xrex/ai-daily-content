---
id: inbox_4981a324
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/vscode-v0.7.0"
author: "RaghavChamadiya"
published_at: 2026-08-05T10:47:59+00:00
fetched_at: 2026-08-05T22:11:16.018380+00:00
content_hash: "89498e307c4e3cfe12aedc407acaa29d02275b1e212c3c73f8f4e878a5afe049"
lang: en
caption_quality: None
raw: true
topics: []
---

# vscode-v0.7.0: docs(vscode): release notes for the 0.7.0 extension release (#1304)

docs(vscode): release notes for the 0.7.0 extension release 
 
 packages/vscode/package.json has read 0.7.0 since the v0.37.0 release commit, 
but no vscode-v0.7.0 tag was ever pushed, so the Marketplace is still serving 
0.6.0. The version bump needs no change; what was missing is notes. 
 The extension had no CHANGELOG.md at all, so users going from 0.6.0 to 0.7.0 
get a docs tree that opens differently, an architecture view with one scope 
control, and rebuilt health and refactoring views with nothing anywhere saying 
so. .vscodeignore does not exclude the file, so it packages into the VSIX and 
renders on the Marketplace changelog tab. 
 Scope is what the seven webviews actually bundle. Web-app-only surfaces that 
moved in the same UI pass (Commits, Contributors, Coverage, Dead code, Chat, 
Settings, Files) are deliberately left out, since the extension does not render 
them. 
 
 docs(vscode): fold the sidebar and diagram changes into the 0.7.0 notes 
 
 The notes were written before the docs tree landed its table-of-contents 
pass, and two bullets described a state no 0.6.0 user will ever see. The 
layers-shut default is gone: the top rung opens on load and nothing below 
it does, which holds back the ninety-module first screen without hiding 
the outline to do it. The file corpus moved from above the layer outline 
to the end of the tree. 
 Both surfaces are bundled: the webviews import docs/docs-tree and 
wiki/wiki-markdown directly, so the tree behaviour and the diagram fit 
ship at 0.7.0 either way. Also adds the deep-link expansion, the glyph 
removal on outline rows, and mermaid diagrams fitting their column.