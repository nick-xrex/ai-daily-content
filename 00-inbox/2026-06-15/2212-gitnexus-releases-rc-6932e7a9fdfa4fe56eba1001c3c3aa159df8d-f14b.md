---
id: inbox_fb7cfc67
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F6932e7a9fdfa4fe56eba1001c3c3aa159df8d267"
author: "magyargergo"
published_at: 2026-06-15T11:31:04+00:00
fetched_at: 2026-06-15T22:12:36.549405+00:00
content_hash: "f14b18f9802ec7cb4d38d2e5657ee85544c780d22fd423c7836622453c170877"
lang: en
caption_quality: None
raw: true
topics: []
---

# rc/6932e7a9fdfa4fe56eba1001c3c3aa159df8d267: feat(cfg): PDG/CFG visitors for all supported languages (#2195) (#2197)

test(cfg): validate cfg/visitors literals + drop 3 dead TS node types 
 
 Extend the grammar-literal CI gate (test/helpers/literal-collectors.ts) 
to scan cfg/visitors/*.ts, mapping each visitor file to its grammar via 
the existing basename rule (c-cpp -&gt; C/C++, csharp -&gt; C#, java -&gt; Java, 
go -&gt; Go, typescript -&gt; TS). Closes the gap where the gate never 
validated CFG visitor node-type literals -- the prerequisite for adding 
C-family visitors safely ( #2195 U1). 
 The newly-scanned TS visitor surfaced 3 dead literals absent from every 
grammar it serves (typescript/javascript/tsx all = 0): for_of_statement 
(for-of parses as for_in_statement), async_function_declaration and 
async_arrow_function (async functions are function_declaration / 
arrow_function + an async child). Removed them; behavior-preserving -- 
the cases never matched, bench --check fingerprints unchanged, TS 
visitor unit tests green. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 test(cfg): language-agnostic CFG unit-test harness ( #2195 U1) 
 
 Extract the grammar-agnostic engine from ts-cfg-harness into 
makeCfgHarness(grammar, visitor, filePath) at test/helpers/cfg-harness.ts. 
Function discovery delegates to visitor.isFunction, so the harness carries 
no language-specific node-type knowledge -- each C-family visitor's unit 
tests can drive the real worker-side builder against real source. 
 ts-cfg-harness becomes a thin TS binding re-exporting the same 
parse/collectFunctions/cfgOf/cfgsOf (behavior-preserving: all 5 existing 
consumers -- taint propagate/model-match/summary-harvest/taint-emit + cfg 
harvest -- pass unchanged, 223 tests green). New harness.test.ts proves 
TS-faithfulness and isFunction-delegation via a stub visitor. 
 The bench parameterization (measure.mjs) is sequenced into U7, where the 
first C-family scaling scenario makes the {grammar, visitorFactory} seam 
validatable against a real non-TS language. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 feat(cfg): C and C++ CFG visitor + def/use harvest ( #2195 U2) 
 
 Add createCCfgVisitor/createCppCfgVisitor over a shared CCfgWalk core. 
Grammar introspection confirmed tree-sitter-c and tree-sitter-cpp share 
every control-flow node type/field, so CppCfgWalk extends CCfgWalk with 
only the C++-only nodes (try/catch/throw/for_range_loop/lambda) via a 
visitExtra hook -- no language conditionals (AGENTS no-language-naming). 
Wire both into c-cpp.ts providers. 
 Harvest (c-cpp-harvest.ts): two-phase binding table + per-statement 
defs/uses/mayDefs (no sites[] yet -- U6). Edge kinds match the TS 
contract; functionStartColumn populated; non-terminating loops (for(;;), 
while(1)) emit the structural exit-escape edge so EXIT stays 
reverse-reachable and CDG is not silently skipped -- verified against the 
production post-dominator + control-dependence solvers (for(;;) -&gt; 3 CDG 
edges). buildFunctionCfg returns undefined rather than throwing. 
 23 real-parser regression tests; grammar-literal gate green (literals 
validated against both grammars). Documented gaps: C++ RAII destructors, 
setjmp/longjmp, computed goto (route to EXIT + warn). 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 feat(cfg): C# CFG visitor + def/use harvest ( #2195 U3) 
 
 Add createCsharpCfgVisitor + csharp-harvest over the shared CfgBuilder / 
ControlFlowContext, modeling the C# statement taxonomy: if/else, 
for/foreach/while/do, switch_section (+ switch_expression arms), 
try/catch/catch_filter/finally, using + lock (deterministic finalizers -- 
dispose/release runs on normal AND exception exit, finally-* completion 
edges on crossing jumps), goto/labeled, yield (surface only), return/ 
throw/break/continue. Wire into csharpProvider. 
 Every literal validated against tree-sitter-c-sharp via the introspection 
probe (record_declaration, no else_clause, switch_section, positional 
access where no field exists). Edge kinds match the contract; 
functionStartColumn populated; while(true) keeps EXIT reverse-reachable 
(production CDG probe: 3 edges). buildFunctionCfg returns undefined 
rather than throwing. 
 34 real-parser regression tests; grammar-literal gate green; no 
regression (cfg unit dir 256/256, tsc clean). Documented gaps: yield 
iterator state machine, goto case/default, async suspension points. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 feat(cfg): Java CFG visitor + def/use harvest ( #2195 U4) 
 
 Add createJavaCfgVisitor + java-harvest over the shared CfgBuilder / 
ControlFlowContext: if/else, classic for, enhanced-for, while, do-while, 
classic-vs-arrow switch (switch_block_statement_group fallthrough vs 
switch_rule no-fallthrough), try/catch/finally + try-with-resources 
(auto-close synthesized as a finalizer, closes on normal AND exception 
exit) + synchronized (monitor-release finalizer), labeled break/continue 
to the labeled frame, yield, return/throw/break/continue. Wire into 
javaProvider. 
 Every literal validated against tree-sitter-java via the probe 
(switch_expression covers both switch forms, generic_type, line_comment, 
for init field). Edge kinds match the contract; functionStartColumn 
populated; while(true)/for(;;) keep EXIT reverse-reachable (production 
CDG probe: 3 edges; hazard fixture: 34 CDG edges). buildFunctionCfg 
returns undefined rather than throwing. 
 43 real-parser regression tests; grammar-literal gate green; no 
regression (cfg unit suite 304, tsc clean). Documented gaps: switch-as- 
expression-value inline, yield state machine, async/field-write defs. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 feat(cfg): Go CFG visitor + def/use harvest ( #2195 U5) 
 
 Add createGoCfgVisitor + go-harvest, the highest-divergence target: 
for_statement (all four shapes -- for_clause C-style, while-style, 
range_clause, bare for{}), expression/type switch (no implicit 
fallthrough) + explicit fallthrough_statement, select_statement, defer 
(LIFO finalizer legs at function exit), go (call is straight-line; the 
closure body is its own CFG via isFunction), labeled break/continue/goto, 
multiple-return assigns (a, b := f() defines each LHS). Wire into 
goProvider. 
 CRITICAL (review A2): every non-terminating shape -- for{}, for cond{}, 
select{} with no default -- emits a structural exit-escape edge so EXIT 
stays reverse-reachable and the production CDG is not silently skipped. 
Verified: for{} -&gt; CDG=3, select{} -&gt; CDG=1, for-range -&gt; CDG=2, all 
exitReachable=true. 
 Every literal validated against tree-sitter-go via the probe. 32 
real-parser regression tests; grammar-literal gate green; no regression 
(186 across all 5 visitors + gate, full cfg unit 331, tsc clean). 
Documented gaps: panic/recover unwind, goroutine happens-before. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 feat(cfg): call-site sites[] taint substrate for C-family ( #2195 U6) 
 
 Extend the C/C++/C#/Java/Go harvests with the call-site sites[] taint 
substrate (SiteRecord/SiteArgOccurrence), mirroring the TS shape so the 
shared taint matcher consumes all languages uniformly. Extract the 
grammar-agnostic site machinery into cfg/visitors/call-site-harvest.ts 
(CallSiteFactAccumulator -- names no language); each harvest adds only its 
per-grammar visitCall/walkChain over its call node (C/C++ call_expression, 
C# invocation_expression, Java method_invocation, Go call_expression). 
 INERT BY DESIGN: no C-family taint model exists (registerBuiltinTaintModels 
is TS/JS only), so getSourceSinkConfig returns undefined for these 
languages and the harvested sites produce ZERO TAINTED edges -- the 
positive source-&gt;sink-&gt;TAINTED path is deferred with the model authoring. 
 sites emitted only when non-empty; facts-only attachment, block/edge 
topology unchanged (pre-existing topology + def/use tests byte-identical). 
23 new substrate tests; 574 green across the cfg/taint/emit suites; gate 
green; tsc clean. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 test(cfg): worker-mode PDG integration + bench parameterization ( #2195 U7) 
 
 Prove the five C-family visitors build PDG through the REAL worker 
pipeline. pipeline-pdg.test.ts: per-language (C/C++/C#/Java/Go) temp repo 
run with pdg:true asserts BasicBlock+CFG+REACHING_DEF+CDG all &gt; 0 (CDG&gt;0 
proves EXIT stays reverse-reachable end-to-end through the worker, incl. 
each fixture's non-terminating loop/select); a paired run with pdg off 
asserts == 0, the two flag-off graphs byte-identical (R3), no PDG types 
leak, pinned by a golden snapshot. Counts e.g. Go 151 BB / 56 CDG. 
 Parameterize bench/cfg/measure.mjs by a per-language LANGS registry 
resolved generically via getLanguageGrammar + getProvider(X).cfgVisitor 
(no static import table). Default TS byte-identical -- all 6 TS 
fingerprints unchanged under --check; taint-dense stays TS-only 
(TS_JS_TAINT_MODEL never runs against model-less C-family CFGs). Add a 
go:branchy scenario+baseline (namespaced) -- its fingerprint shape 
(32 blocks/46 edges) matches TS branchy, cross-validating the Go visitor. 
 15 pipeline tests + bench --check PASS (7 scenarios); 354 unit cfg green; 
dist rebuilt clean. Absorbs the bench parameterization deferred from U1. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 feat(cfg): Python CFG visitor + def/use harvest ( #2195 U8) 
 
 Add createPythonCfgVisitor + python-harvest -- the most structurally 
divergent target (indentation blocks, elif, for/while-else, with, try/ 
except/except-group/else/finally, match/case, comprehensions, walrus), 
confirming the shared CfgBuilder/ControlFlowContext core carries no 
brace-family assumptions. for/while else-clause sits on the normal- 
completion edge (not break); with modeled as try/finally dispose; match 
has no fallthrough. Wire into pythonProvider. 
 Every literal validated against tree-sitter-python via the probe. 
while True: keeps EXIT reverse-reachable (production CDG probe: 3 edges; 
fixture: 42 CDG edges). 37 real-parser tests; gate green; no regression 
(cfg unit 391, tsc clean). Gaps: async/generator suspension, comprehension 
scope over-approximation. No sites[] (taint substrate, separate). 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 feat(cfg): PHP CFG visitor + def/use harvest ( #2195 U9) 
 
 Add createPhpCfgVisitor + php-harvest: if/elseif/else (+ alt colon 
syntax), for/foreach/while/do-while, switch (fallthrough) + match (no 
fallthrough), try/catch/finally, break N/continue N (N-th enclosing 
loop), goto, return/throw. Wire into phpProvider. 
 Every literal validated against tree-sitter-php (php_only) via the probe 
(for_statement initialize/condition/update; throw_expression not 
throw_statement; break/continue integer child). while(true) keeps EXIT 
reverse-reachable (production CDG probe: 3 edges; break 2 escapes the 
outer loop). 35 real-parser tests. 
 Also repoint worker-roundtrip's "non-CFG language" gate test from Python 
(which now has a cfgVisitor) to COBOL (the permanent non-goal of the 
rollout) -- a stale assertion the Python commit invalidated. Full 
in-process sweep green (452 across 18 files). Gaps: match inline value, 
goto plain-block. 
 Co-Authored-By: Claude Opus 4.8 (1M context) noreply@anthropic.com 
 
 feat(cfg): Ruby CFG visitor + def/use harvest ( #2195 U10) 
 
 Add createRubyCfgVisitor + ruby-harvest: if/unless/elsif/else + 
statement-modifier forms (x if c, x while c), while/until/for (until 
inverts the sense), case/when + case/in (pattern, no fallthrough), 
begin/rescue/else/ensure (ensure=finally, rescue=catch) + retry 
(loop-back into begin), return/break/next/redo, blocks/lambdas as their 
own closure CFGs. Wire into rubyProvider. 
 Every literal validated against tree-sitter-ruby via the probe (case vs 
case_match, modifier nodes, typed rescue/ensure children). loop do / 
while

[... truncated for safety ...]