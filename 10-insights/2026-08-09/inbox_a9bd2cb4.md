---
id: inbox_a9bd2cb4
date: 2026-08-09
source_ref: "[[00-inbox/2026-08-09/2203-gitnexus-releases-rc-81100e2c7481632a444c96434b4edd82a4380-4b40]]"
title: "rc/81100e2c7481632a444c96434b4edd82a4380bed: fix(python): resolve calls through `__init__.py` re-exports (#2864)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F81100e2c7481632a444c96434b4edd82a4380bed
source: gitnexus-releases
published_at: 2026-08-09T11:21:06+00:00
fetched_at: 2026-08-10T04:27:24.214510+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 修正 Python 套件透過 __init__.py 重新匯出的呼叫圖解析遺漏（#2864）。原本 `from pkg.impl import target_fn` 在 pkg/__init__.py 被重新匯出後，呼叫端無法建立 CALLS 邊；此為 Python 套件的常見公開界面宣告模式，遺漏導致大量呼叫邊消失。修正引入 `reexportsName` 旗標區分模組層級發佈 vs 函式/類別內部本地綁定；並改進重新匯出閉包：(1) 捨棄模稜兩可名稱（多來源衝突無法判斷執行分支，全數捨棄避免錯誤決策）(2) 排除名稱空間重分類草稿 (3) 將 transitiveVia 鏈深度上限設 32（性能優化 67ms/145MB → 25ms/40MB）。測試驗證：12.4k 檔案混合儲存庫呼叫邊 +7,027（294,416→301,443）、執行流 300→813；先前 100% 孤立模組 shared/db/event_writer.py 現正確報告呼叫者。"
key_points:
  - "`reexportsName` 旗標機制區分作用域：僅模組頂層 from m import x 發佈名稱，函式/類別內部匯入不發佈（避免假重新匯出）"
  - "重新匯出閉包三項改進：模稜兩可名稱捨棄（resolves CPython ambiguity）、名稱空間重分類排除、transitiveVia 深度上限 32（SCC 中高深度鏈 Theta(depth²) 優化）"
  - "12.4k Python/Go/TypeScript 混合儲存庫：+7,027 呼叫邊（294,416→301,443）、執行流 +513（300→813）；消除 orphaned module 誤判"
tags: [python-imports, re-export-resolution, call-graph, scope-tracking, depth-capping]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## rc/81100e2c7481632a444c96434b4edd82a4380bed: fix(python): resolve calls through `__init__.py` re-exports (#2864)

GitNexus 修正 Python 套件透過 __init__.py 重新匯出的呼叫圖解析遺漏（#2864）。原本 `from pkg.impl import target_fn` 在 pkg/__init__.py 被重新匯出後，呼叫端無法建立 CALLS 邊；此為 Python 套件的常見公開界面宣告模式，遺漏導致大量呼叫邊消失。修正引入 `reexportsName` 旗標區分模組層級發佈 vs 函式/類別內部本地綁定；並改進重新匯出閉包：(1) 捨棄模稜兩可名稱（多來源衝突無法判斷執行分支，全數捨棄避免錯誤決策）(2) 排除名稱空間重分類草稿 (3) 將 transitiveVia 鏈深度上限設 32（性能優化 67ms/145MB → 25ms/40MB）。測試驗證：12.4k 檔案混合儲存庫呼叫邊 +7,027（294,416→301,443）、執行流 300→813；先前 100% 孤立模組 shared/db/event_writer.py 現正確報告呼叫者。

### 重點
- `reexportsName` 旗標機制區分作用域：僅模組頂層 from m import x 發佈名稱，函式/類別內部匯入不發佈（避免假重新匯出）
- 重新匯出閉包三項改進：模稜兩可名稱捨棄（resolves CPython ambiguity）、名稱空間重分類排除、transitiveVia 深度上限 32（SCC 中高深度鏈 Theta(depth²) 優化）
- 12.4k Python/Go/TypeScript 混合儲存庫：+7,027 呼叫邊（294,416→301,443）、執行流 +513（300→813）；消除 orphaned module 誤判

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F81100e2c7481632a444c96434b4edd82a4380bed)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(python): resolve calls through __init__.py re-exports 
 
 A call to a name imported from a package never resolved when the package's 
 __init__.py re-exported it rather than defining it: 
 pkg/impl.py def target_fn(x): ...
pkg/__init__.py from pkg.impl import target_fn
caller.py from pkg import target_fn
 def calls_it(): return target_fn(21) # no CALLS edge
 
 caller.py gets no CALLS edge. Both IMPORTS hops are recorded, and all four 
functions are extracted as nodes — only the call binding is missing. Because 
 __init__.py re-exports are how Python packages declare a public surface, this 
misses a large fraction of real call edges, and the failure is silent: the 
defining file looks like dead code with zero callers. 
 The re-export closure that should carry this already exists and is fully general 
( buildReexportClosures — SCC over the re-export subgraph, bounded fixpoint for 
cycles, transitive via chains). Python just never fed it: the subgraph admits 
only kind: 'reexport' and kind: 'wildcard' , and Python emits neither for 
 from m import x . 
 Python has no dedicated re-export form. A module-level from pkg.impl import X 
binds X locally AND publishes it as pkg.X , so it is both a named import and a 
re-export. Emitting kind: 'reexport' would be wrong — that form drops the local 
binding, which Python's does create. Instead add an optional reexportsName flag 
to the named / alias variants, alongside the existing provider-specific 
 importedSymbolKind / targetIncludesImportedName flags, and admit flagged 
imports into the closure subgraph. Languages with an explicit form keep emitting 
 kind: 'reexport' and leave the flag unset, so nothing changes for them — a 
negative-control test asserts a plain named import still does not resolve. 
 Verified on a fixture covering the three shapes (direct, top-level-via-re-export, 
function-local-via-re-export): 1 of 3 CALLS edges resolved before, 3 of 3 after. 
 On a 12.4k-file Python/Go/TypeScript repository: edges 294,416 -&gt; 301,443 
(+7,027) and execution flows 300 -&gt; 813. A previously "100% orphaned" module 
( shared/db/event_writer.py ) now correctly reports its caller. 
 5 new finalize tests (single hop, 3-hop chain, alias keying, cycle termination, 
and the negative control) plus 6 updated Python fixture shapes. 
 npx tsc --noEmit clean in both packages; full unit suite shows no regression 
against baseline (remaining failures are pre-existing load-sensitive flakes in 
analyzer-identity / evidence-provenance-helper / skip-git-cli / hooks, each 
verified passing in isolation). 
 
 fix(python): set reexportsName only for module-level imports 
 
 interpretPythonImport flagged every from m import x as republishing the 
name, but only a module-level statement does. A from m import X inside a 
 def or class body binds locally and puts nothing in the module namespace, 
so flagging it fabricates a re-export of a name no importer can reach: 
 # pkg/__init__.py
def loader():
 from pkg.impl import InternalHelper
# caller.py
from pkg import InternalHelper # CPython: ImportError
 
 resolved to def:pkg.impl.InternalHelper . Worse, with declaration-order 
first-wins in the closure, a scope-blind entry could claim a name ahead of the 
real module-level import and give a WRONG def for legal, running code. 
 interpretImport receives a CaptureMatch , which is {name, range, text} 
with no syntax node, so the scope is not recoverable there — and it is not 
recoverable downstream either: pass3CollectImports applies no scope filter 
and ImportEdgeDraft.fromScope is hardcoded to the module scope. The decision 
therefore moves up to import-decomposer.ts , which still holds the live 
 import_from_statement node, and rides down as an @import.publishes marker. 
Computed once per statement, not once per imported name, with the existing 
 findAncestorBeforeBoundary helper. 
 Only function_definition and class_definition suppress publication. 
 if / try / for / with do NOT — Python has no block scope — so the 
predicate is an ancestor walk for those two node types and nothing else. 
Verified against CPython 3.11 in both directions; both are now pinned by 
tests, including the counterpart control that a branch-nested import still 
republishes. 
 Also corrects the docblock in scope-extractor.ts that sent this change the 
wrong way. It claims pass 3 attaches imports "not to any Scope — finalize 
reconstructs the owning scope via provider.importOwningScope during Phase 
2". Finalize does no such thing: importOwningScope is declared on 
 LanguageProvider and implemented by a dozen providers, and 
 grep -rnE "\.importOwningScope\b" gitnexus/src/ returns exactly one hit — 
that doc comment. Nothing invokes it. 
 Co-Authored-By: Claude Opus 5 (1M context) noreply@anthropic.com 
Claude-Session: https://claude.ai/code/session_01Rzsb6mdGtbu66BG1EaF6Zz 
 
 fix(shared): stop guessing ambiguous and namespace re-exports; bound the via chain 
 
 Four changes to the re-export closure, all reachable only now that Python 
feeds it. 
 
 
 AMBIGUOUS NAMES ARE DROPPED, NOT GUESSED. populateFileClosure documented 
"declaration order first-wins for duplicates of the same exported name", 
which is sound only where a duplicate export is illegal — two 
 export { X } from ... is a TypeScript compile error, so the rule never 
fires. Python has no such guarantee: 
 from .v1 import Client # legacy, left behind
from .v2 import Client # the actual public Client
 
 CPython binds v2 (verified on 3.11); first-wins attributed every 
 from pkg import Client in the repo to the DEAD implementation, and 
 impact("Client") pointed at the wrong file. Last-wins is not the fix 
either: for the equally common try: / except ImportError: and 
 if sys.version_info pairs exactly one branch runs, and which one is not 
decidable here. Both directions are wrong on real code, so the entry is 
dropped — the importer stays unresolved, which is exactly the pre- #2864 
answer, and the file-level IMPORTS edge is untouched. 
 collectAmbiguousReexports runs as a PRE-PASS over data phase 0 froze, 
so the poisoned set is constant across the fixpoint. That matters: a set 
that grew mid-fixpoint would need retraction to propagate to files that 
already inherited the name, would make myClosure.size &gt; before an 
unsound progress signal, and would invalidate the |SCC| + 1 cap. As a 
pre-pass the closure map stays monotone and every existing termination 
argument survives unchanged. Only two flagged drafts resolving to two 
DIFFERENT in-workspace files count; duplicates of one target are 
harmless, and unresolvable targets never entered the closure. 
 Checked in both loops. Named re-exports take precedence over wildcards, 
so suppressing only the named loop would hand the name to a later 
 import * and reinstate an arbitrary winner through the back door. 
 
 
 NAMESPACE-RECLASSIFIED DRAFTS ARE EXCLUDED. The admission guards tested 
 draft.source.kind while tryFinalize tests the post-reclassification 
 draft.base.kind . Python's from . import logger is emitted as named , 
reclassified to namespace by isNamespaceImport , and was still 
admitted — republishing whatever def shared the module's simple name. For 
a logger.py holding a module-level logger = logging.getLogger(...) , 
importers of from pkg import logger bound to that Variable instead of 
the module. Reproduced end to end. Both predicates now take the draft and 
test base.kind ; this is a no-op for TS/Rust, whose only 
 isNamespaceImport implementation is Python's. 
 
 
 transitiveVia IS CAPPED AT 32. Each hop copies the inherited path, so 
an unbounded chain is Theta(depth^2) in time AND retained memory, and 
Theta(|SCC|^2) for a cycle whose chain tracks it. MAX_REEXPORT_DEPTH = 100 covered this until fc919ad removed it — correct for the shallow 
TypeScript barrels that were then the only input, and invisible until the 
input class changed. Measured at depth 400: 67 ms / 145 MB uncapped vs 
25 ms / 40 MB capped. 32 against a real-world worst case of ~6 for 
 __init__.py chains. Safe because ImportEdge.transitiveVia has no 
production reader — it is diagnostic provenance, emitted and typed but 
dropped by graph emission. 
 
 
 localDefs ARE INDEXED BY SIMPLE NAME. findExportByName linearly 
scanned a target's defs on every call, and the phase-3 fixpoint rescans 
the same target once per iteration. Memoized on the array identity, which 
 FinalizeFile documents as static input. Worth 12-14% where lookups 
repeat and neutral elsewhere. 
 
 
 The 46-line algorithm docblock was also ORPHANED by the helpers inserted 
between it and buildReexportClosures — AST-verified, that function had zero 
jsdoc blocks, so the cross-reference elsewhere in the file landed on an 
undocumented function. Helpers move below it (declarations hoist), and its 
step 1, precedence and complexity sections are rewritten: they still claimed 
regular imports do not contribute to the export surface, and justified the 
via-copy cost by TypeScript barrels being shallow. 
 The reexportsName contract consolidates onto ParsedImport , where its 
" kind: 'reexport' would drop the local binding" rationale is corrected — 
 materializeBindings creates a module-scope binding for every linked edge, 
re-export included. The real reasons are that origin flips, changing 
evidence weight and priority, and that it misreports Python's syntax. 
 Co-Authored-By: Claude Opus 5 (1M context) noreply@anthropic.com 
Claude-Session: https://claude.ai/code/session_01Rzsb6mdGtbu66BG1EaF6Zz 
 
 test(shared): add a re-export closure scaling guard to CI 
 
 No bench covered buildReexportClosures at all. Until #2864 its input was 
TypeScript barrel files — a handful of shallow edges — and it admitted only 
 reexport and wildcard drafts. It now admits every module-level Python 
 from m import x , measured ~20x more edges on the CPython stdlib and cyclic 
SCCs where there were none. The pass went from "rarely runs" to "runs over 
the whole named import graph" with nothing watching it. 
 The regression this guards has already happened once: fc919ad removed 
 MAX_REEXPORT_DEPTH , which was correct for shallow barrels and stayed 
invisible for as long as the input stayed shallow. 
 The depth arm is an EXACT structural assertion — build a chain far past the 
cap, assert the longest emitted transitiveVia is exactly MAX_VIA_LENGTH . 
It started as a depth_ratio timing arm and that was a bad gate: sampled 
five times capped it scored 2.71-3.52 and three times uncapped 5.87-7.65, so 
the ranges nearly touch and one uncapped run came in UNDER budget. A gate 
that passes a third of the time on a broken build is worse than none, because 
it gets read as evidence. The structural form fails 3/3 with 401 vs 32. 
 width_ms stays a timing arm with a deliberately loose budget, because a 
structural check cannot see a constant factor: restoring a per-lookup linear 
scan of localDefs leaves every array length untouched while making every 
real analyze slower. 
 Both arms drive finalize through INDEXED hooks. Reusing the unit tests' 
 defaultHooks is the trap — its resolveImportTarget does files.some(...) 
per import, which is O(imports x files) in the FIXTURE and swamps the pass so 
completely that removing the cap measures as no change at all. 
 Co-Authored-By: Claude Opus 5 (1M context) noreply@anthropic.com 
Claude-Session: https://claude.ai/code/session_01Rzsb6mdGtbu66BG1EaF6Zz 
 
 fix(cache): bump SCHEMA_BUMP 53 -&gt; 60 for ParsedImport.reexportsName 
 
 reexportsName is a new field on ParsedImport , and parsedfile-store.ts 
serializes the whole ParsedFile generically — so it is part of the cached 
shape even though it is not a capture, which is the easy-to-miss variant of 
the rule parse-cache.ts states as a MUST. (The @import.publishes marker 
added alongside it moves the capture output too, so this qualifies twice; the 
python captures golden confirms the drift.) 
 Without the bump, a warm parsedfile-cache replays pre-fix Pars

[... truncated for safety ...]

</details>