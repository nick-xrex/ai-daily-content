---
id: inbox_9d9d5b89
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t4j4s9/programbench_can_we_really_rebuild_huge_binaries/"
author: "/u/klieret"
published_at: 2026-05-05T15:40:52+00:00
fetched_at: 2026-05-06T10:02:16.858293+00:00
content_hash: "7e3cdf62dd57c5a31009624de57dea41efc74bfcd916baa60455d734ec329be6"
lang: en
caption_quality: None
raw: true
topics: []
---

# ProgramBench: Can we really rebuild huge binaries from scratch? (doesn't look like it)

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4j4s9/programbench_can_we_really_rebuild_huge_binaries/"> <img alt="ProgramBench: Can we really rebuild huge binaries from scratch? (doesn't look like it)" src="https://preview.redd.it/0u4039bq8czg1.png?width=140&amp;height=128&amp;auto=webp&amp;s=c4a72fdaa2f31ddc58fcbf309f1bccc3ecab55f5" title="ProgramBench: Can we really rebuild huge binaries from scratch? (doesn't look like it)" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>There's been quite a few case studies recently on agents building whole programs from scratch, but most of them test a single or just a few projects with hand-tuned setups.</p> <p>We've spent the last couple of months formalizing this setting and building a benchmark of 200 tasks while doubling down on testing, cheat prevention, and task diversity.</p> <p>Our agent ONLY gets a target executable and some readme/usage files. The agent must choose a language, design abstraction layers, and architect the entire program. No internet access or any other way of cheating. No decompilation.</p> <p>We've also spent some 50k to generate 6M lines of behavioral tests and then filtered them down to keep the best ones. Because they are just testing executables as a black box, we do not make any assumptions on even the language that the LM uses to implement the program.</p> <p>All of the results are at <a href="http://programbench.com">programbench.com</a> . There's also a big FAQ at the bottom.</p> <p>We've just open-sourced our github, huggingface and docker images.</p> <p>Essentially you can just start evaluating with <code>pip install programbench &amp;&amp; programbench eval &lt;your submission&gt;</code></p> <p>Github is at <a href="https://github.com/facebookresearch/programbench">https://github.com/facebookresearch/programbench</a></p> <p>Sorry that it's just closed source models right now, we have a few open-source models in the pipeline, but so far we've had an even harder time at getting them to behave well with these tasks (open source models tend to be somewhat more overfitted to things like SWE-bench, so they often have a harder time with new benchmarks).</p> <p>We're also planning to open the benchmark for submissions quite soon, similar to what we did on SWE-bench and its variants.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/klieret"> /u/klieret </a> <br /> <span><a href="https://www.reddit.com/gallery/1t4j4s9">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4j4s9/programbench_can_we_really_rebuild_huge_binaries/">[comments]</a></span> </td></tr></table>