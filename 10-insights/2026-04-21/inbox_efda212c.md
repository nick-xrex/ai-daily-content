---
id: inbox_efda212c
date: 2026-04-21
source_ref: "[[00-inbox/.../inbox_efda212c]]"
title: "My First AI Agent with LangChain — Here’s What Nobody Tells You"
url: https://blog.stackademic.com/my-first-ai-agent-with-langchain-heres-what-nobody-tells-you-98f372a039a3?source=rss----d1baaa8417a4---4
source: medium-stackademic
published_at: 2026-04-21T12:13:24+00:00
fetched_at: 2026-04-22T01:04:26.118370+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者分享用 LangChain 構建 ReAct 代理的實戰踩坑與解決方案。首次發現三個驚訝：（1）推理循環中的幻覺 — 模型會偽造自己已完成搜尋的思考鏈，實際上只用訓練資料；（2）token 成本指數增長 — verbose 推理鏈加上完整歷史導致成本失控；（3）verbose=True 是早期除錯的關鍵，關閉前必須建立真正的日誌。修正推理幻覺需明確要求「執行工具後再結論」；成本控制需設定 max_iterations=5、max_execution_time=30s、使用 GPT-4o-mini 處理中間步驟。生產前提：建立錯誤捕捉、記憶體管理（ConversationSummaryMemory）、結構驗證。建議：從單一工具開始、前置定義「正確」標準、用 LangSmith 追蹤、質疑 ReAct 模式是否總是必要。"
key_points:
  - "推理循環幻覺 pattern：模型虛假宣稱完成任務但未實際執行工具 — 需明確強制「使用工具後才結論」指令"
  - "Token 成本陷阱：verbose 推理鏈逐步積累，導致 $4.30 per ~20 prompts 的成本失控 — 必須設 max_iterations=5 和 max_execution_time=30s"
  - "verbose=True 直到生產、再改真正日誌：模型失敗時會沉默失敗，verbose 模式才能暴露完整推理鏈讓人追蹤"
tags: [langchain, agents, reasoning-loop, token-cost, production-debugging]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## My First AI Agent with LangChain — Here’s What Nobody Tells You

開發者分享用 LangChain 構建 ReAct 代理的實戰踩坑與解決方案。首次發現三個驚訝：（1）推理循環中的幻覺 — 模型會偽造自己已完成搜尋的思考鏈，實際上只用訓練資料；（2）token 成本指數增長 — verbose 推理鏈加上完整歷史導致成本失控；（3）verbose=True 是早期除錯的關鍵，關閉前必須建立真正的日誌。修正推理幻覺需明確要求「執行工具後再結論」；成本控制需設定 max_iterations=5、max_execution_time=30s、使用 GPT-4o-mini 處理中間步驟。生產前提：建立錯誤捕捉、記憶體管理（ConversationSummaryMemory）、結構驗證。建議：從單一工具開始、前置定義「正確」標準、用 LangSmith 追蹤、質疑 ReAct 模式是否總是必要。

### 重點
- 推理循環幻覺 pattern：模型虛假宣稱完成任務但未實際執行工具 — 需明確強制「使用工具後才結論」指令
- Token 成本陷阱：verbose 推理鏈逐步積累，導致 $4.30 per ~20 prompts 的成本失控 — 必須設 max_iterations=5 和 max_execution_time=30s
- verbose=True 直到生產、再改真正日誌：模型失敗時會沉默失敗，verbose 模式才能暴露完整推理鏈讓人追蹤

**原文：** [medium-stackademic](https://blog.stackademic.com/my-first-ai-agent-with-langchain-heres-what-nobody-tells-you-98f372a039a3?source=rss----d1baaa8417a4---4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

-d1baaa8417a4---4"
author: "Kağan MURAT, PMP®"
published_at: 2026-04-21T12:13:24+00:00
fetched_at: 2026-04-21T21:46:30.802071+00:00
content_hash: "c81db41494c42a30c2dcefd821a87b016dee30c950b9789203bcf4d21d959d1f"
lang: en
caption_quality: None
raw: true
topics: []
---

# My First AI Agent with LangChain — Here’s What Nobody Tells You

<figure><img alt="" src="https://cdn-images-1.medium.com/max/1024/1*kcpZtniY860r5fqVanPPAg.jpeg" /><figcaption>The image was generated using AI Tool</figcaption></figure><p>A developer’s honest take on agentic AI: what worked, what broke, and what I’d do differently</p><p>Everyone is talking about AI agents.</p><p>“Autonomous.” “Self-directing.” “The future of software.”</p><p>An agent was created using LangChain documentation. The result was generally successful, but some surprises emerged.</p><h3>What Was Built?</h3><p>A simple research agent:<br />- Can take a question as input<br />- Can search for relevant information online<br />- Can summarize the findings<br />- Can return a structured response with sources</p><p>The classic “ReAct” model. Many training videos cover this. However, training videos skip the part where things go wrong.</p><p><strong>The Setup (This Part Actually Works)</strong></p><pre>from langchain.agents import AgentExecutor, create_react_agent<br />from langchain_openai import ChatOpenAI<br />from langchain.tools import DuckDuckGoSearchRun<br />from langchain import hub<br /><br /># Initialize the LLM<br />llm = ChatOpenAI(model=&quot;gpt-4o&quot;, temperature=0)<br /><br /># Define tools<br />search = DuckDuckGoSearchRun()<br />tools = [search]<br /><br /># Pull a standard ReAct prompt<br />prompt = hub.pull(&quot;hwchase17/react&quot;)<br /><br /># Create the agent<br />agent = create_react_agent(llm, tools, prompt)<br />agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)<br /><br /># Run it<br />result = agent_executor.invoke({<br />    &quot;input&quot;: &quot;What are the most significant AI developments in 2025?&quot;<br />})<br />print(result[&quot;output&quot;])</pre><p>Clean. Simple. And it worked.</p><p>The moment I pushed it slightly outside that path, things got interesting.</p><h3>3 Surprising Things</h3><h3>1. The Agent Lies to Itself</h3><p>The most unsettling discovery: my agent would sometimes <em>decide</em> it had completed a task when it hadn’t.</p><p>It would generate a “Thought” like:</p><pre>&quot;I now have enough information to answer the question.&quot;</pre><p>Then produce a confident, well-structured answer — based on nothing but its own prior knowledge, completely ignoring the search tool I gave it.</p><p>This is called <strong>hallucination in the reasoning loop</strong>, and it’s different from the hallucination you see in regular LLM outputs. The model isn’t just making up facts — it’s fabricating the <em>process</em> of finding them.</p><p><strong>Fix:</strong> Add explicit instructions to your prompt forcing the agent to always use tools before concluding:</p><pre>system_prompt = &quot;&quot;&quot;You are a research assistant. <br />IMPORTANT: You must always use the search tool at least once before providing a final answer.<br />Never rely solely on your training data for factual claims.&quot;&quot;&quot;</pre><p>It’s not perfect, but it dramatically reduces the problem.</p><h3>2. Token Costs Spiral Faster Than You Expect</h3><p>OpenAI charges $4.30 for approximately 20 prompts. This amount will increase exponentially as the number of agents grows.</p><p>The culprit: verbose reasoning chains. The agent was “thinking out loud” with full context on every step, including the entire conversation history.</p><p><strong>Fix:</strong> Set max_iterations to limit runaway loops, and consider using a cheaper model (GPT-4o-mini) for intermediate reasoning steps:</p><pre>agent_executor = AgentExecutor(<br />    agent=agent,<br />    tools=tools,<br />    max_iterations=5,          # Prevent infinite loops<br />    max_execution_time=30,     # Timeout in seconds<br />    verbose=True<br />)</pre><h3>3. “Verbose=True” Is Your Best Friend Early On</h3><p>Every tutorial tells you to set verbose=True while testing. I ignored this at first because the output felt noisy.</p><p>When the agent started failing silently — returning empty outputs, skipping tool calls, looping on the same step — I had no idea why. Turning verbose mode on revealed the full reasoning chain:</p><pre>&gt; Entering new AgentExecutor chain...<br />Thought: I need to search for recent AI developments.<br />Action: duckduckgo_search<br />Action Input: &quot;AI developments 2025&quot;<br />Observation: [search results...]<br />Thought: I have enough information now.<br />Final Answer: [confident but incomplete answer]</pre><p>Seeing this, I immediately spotted where the logic broke. Without verbose mode, I would have spent hours debugging blind.</p><p><strong>Keep verbose=True until you’re ready for production.</strong> Then build proper logging before you turn it off.</p><h3>What Changes in Production</h3><p>A working prototype and a production-ready agent are two very different things. Here’s what the tutorials don’t cover:</p><p><strong>Error handling is non-negotiable.</strong> Agents fail in unexpected ways — tool timeouts, malformed outputs, reasoning loops. Wrap everything:</p><pre>try:<br />    result = agent_executor.invoke({&quot;input&quot;: user_query})<br />except Exception as e:<br />    # Log the error, return a graceful fallback<br />    logger.error(f&quot;Agent failed: {e}&quot;)<br />    return {&quot;output&quot;: &quot;I encountered an error. Please try again.&quot;}</pre><p><strong>Memory management matters.</strong> If your agent maintains conversation history, that history grows with every turn — and so does your token count. Use ConversationSummaryMemory instead of ConversationBufferMemory for longer sessions.</p><p><strong>Never trust the output blindly.</strong> Validate structured outputs before using them downstream. If your agent is supposed to return JSON, parse it and handle malformed responses explicitly.</p><h3>What We Can Do Differently</h3><p>If we replan everything:</p><ol><li><strong>Start with a single tool.</strong> In the study, added three tools at once and couldn’t tell which one was causing issues. One tool, one problem.</li><li><strong>Write tests before building.</strong> Define what “correct” looks like for 5 example inputs before writing any agent code. It forces clarity.</li><li><strong>Use LangSmith from day one.</strong> LangChain’s tracing tool gives you visibility into every step of your agent’s reasoning. Setting it up takes 10 minutes and saves hours of debugging.</li><li><strong>Question the ReAct pattern.</strong> ReAct works well for research tasks, but it’s not always the right architecture. For structured, predictable workflows, a simple chain is often faster, cheaper, and more reliable.</li></ol><h3>Conclusion</h3><p>Agentic AI is genuinely powerful. The ability to give an LLM tools and let it reason through a problem is a real step forward — not just hype.</p><p>But it comes with real complexity that the “build an AI agent in 10 minutes” tutorials conveniently skip.</p><p>The hallucinating reasoning loops. The token costs. The silent failures. The gap between “it works on my machine” and “it works in production.”</p><p>None of these are dealbreakers. They’re just engineering problems — solvable with the same discipline you’d apply to any complex system.</p><p>Build small. Test constantly. Trust the verbose output. And always, always validate what the agent tells you it did.</p><p><strong>Tags:</strong> Artificial Intelligence, LangChain, Python, Machine Learning, Software Development</p><img alt="" height="1" src="https://medium.com/_/stat?event=post.clientViewed&amp;referrerSource=full_rss&amp;postId=98f372a039a3" width="1" /><hr /><p><a href="https://blog.stackademic.com/my-first-ai-agent-with-langchain-heres-what-nobody-tells-you-98f372a039a3">My First AI Agent with LangChain — Here’s What Nobody Tells You</a> was originally published in <a href="https://blog.stackademic.com">Stackademic</a> on Medium, where people are continuing the conversation by highlighting and responding to this story.</p>

</details>