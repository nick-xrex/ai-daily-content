---
id: inbox_f473f357
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/May/23/on-the-dl/#atom-everything"
author: ""
published_at: 2026-05-23T20:24:48+00:00
fetched_at: 2026-05-24T03:48:40.676501+00:00
content_hash: "a688c36561d13e52d49ad21229386eb79fed6fe3105aff49dda58e1ac9caba37"
lang: en
caption_quality: None
raw: true
topics: []
---

# On the <dl>

On the &lt;dl&gt; 
I learned a few new-to-me things about the &lt;dl&gt; element from this article by Ben Meyer: 
 
 A &lt;dt&gt; can be followed by multiple &lt;dd&gt; 
 You can optionally group the &lt;dt&gt; and &lt;dd&gt; elements in a &lt;div&gt; for styling - but only a &lt;div&gt; . 
 You can label them using ARIA. 
 They've been called "description lists", not "definition lists", since an HTML5 draft in 2008 . 
 
 So this is valid: 
 &lt; h2 id =" credits " &gt; Credits &lt;/ h2 &gt; 
 &lt; dl aria-labelledby =" credits " &gt; 
 &lt; div &gt; 
 &lt; dt &gt; Author &lt;/ dt &gt; 
 &lt; dd &gt; Jeffrey Zeldman &lt;/ dd &gt; 
 &lt; dd &gt; Ethan Marcotte &lt;/ dd &gt; 
 &lt;/ div &gt; 
 &lt;/ dl &gt; 

 Here's a useful note from Adrian Roselli on screen reader support for description lists .

 Via Hacker News 

 Tags: css , html , screen-readers , web-standards