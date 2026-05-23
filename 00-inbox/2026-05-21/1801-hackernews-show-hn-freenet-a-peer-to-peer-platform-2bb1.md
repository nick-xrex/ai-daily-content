---
id: inbox_af7ae754
source: hackernews
source_type: hn
url: "https://freenet.org/"
author: "sanity"
published_at: 2026-05-21T14:34:57+00:00
fetched_at: 2026-05-22T18:01:40.468133+00:00
content_hash: "2bb137e6470f919a591723cd01b647eb0c9e1102876bfcf17b118c97835e1d0d"
lang: en
caption_quality: None
raw: true
topics: []
---

# Show HN: Freenet, a peer-to-peer platform for decentralized apps

For the past 5 years or so I&#x27;ve been working on a ground-up redesign of Freenet, my peer-to-peer project from the early 2000s (now renamed Hyphanet). The new Freenet has been up and running since December along with some early applications like River[1], our decentralized group chat and Delta - a decentralized CMS. Users have already started to build their own apps on Freenet including games, and we have some interesting apps in development like Atlas, a search&#x2F;recommendation engine. Architecturally, this new Freenet is a global, decentralized key-value store where keys are webassembly contracts which define what values (aka &quot;state&quot;) are valid for that key, how or when the values can be mutated, and how the state can be efficiently synchronized between peers. We&#x27;ve developed a unique (AFAIK) solution to the consistency problem, every contract must define a &quot;merge&quot; operation for the contract&#x27;s associated state. This operation must be commutative, meaning that you can merge multiple states in any order and you&#x27;ll get the same end result. This approach allows state updates to spread through the network like a virus[2], which typically achieves consistent global state in a few seconds or less. Like the world wide web, Freenet applications can be downloaded from the network itself and run in a web browser - similar to single-page apps on the normal web. However, rather than connecting back to an API running in a datacenter, the webapp connects locally to the Freenet peer and interacts with Freenet contracts and delegates over a local websocket connection. If you&#x27;d like to try Freenet we have convenient installers for the major desktop OSs but not yet mobile, and you can be chatting with other users on River within seconds[3]. Happy to answer any questions, you&#x27;re also welcome to read our FAQ[4], or watch a talk I gave back in March[5]. [1] https:&#x2F;&#x2F;github.com&#x2F;freenet&#x2F;river [2] https:&#x2F;&#x2F;freenet.org&#x2F;about&#x2F;news&#x2F;summary-delta-sync&#x2F; [3] https:&#x2F;&#x2F;freenet.org&#x2F;quickstart&#x2F; [4] https:&#x2F;&#x2F;freenet.org&#x2F;faq&#x2F; [5] https:&#x2F;&#x2F;youtu.be&#x2F;3SxNBz1VTE0