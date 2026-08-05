---
id: inbox_575f8455
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.38.0"
author: "github-actions[bot]"
published_at: 2026-08-04T13:57:53+00:00
fetched_at: 2026-08-04T22:16:03.917685+00:00
content_hash: "97dd08c740ed7623b87884a229ff66e1ed734acf5133cc713426db13955bc897"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.38.0

What's Changed 
 
 feat(generation): measure vocabulary overlap across orientation pages by @swati510 in #1160 
 feat(pages): retired page ids keep resolving by @swati510 in #1163 
 feat(generation): the overview carries the architecture map by @swati510 in #1164 
 feat(generation): stamp layer provenance on the pages a layer groups by @swati510 in #1165 
 feat(pages): a retired page can hand off to the repository's overview by @swati510 in #1166 
 fix(answer): stop the prompt formatter halving every page excerpt it fetches by @swati510 in #1168 
 fix(answer): attach page content on every retrieval, not only the weak ones by @swati510 in #1169 
 feat(docs): the tree groups modules under their layer from the members by @swati510 in #1170 
 feat(generation): layers group the docs tree without a page to hang it off by @swati510 in #1171 
 fix(generation): reject pages that talk to the prompter, and cap the overview's prose by @swati510 in #1172 
 fix(cli): generation checks reach a normal run of init and update by @swati510 in #1178 
 refactor(generation): drop the onboarding prerequisite table nothing reads by @swati510 in #1179 
 feat(answer): meter what one synthesis call costs by @swati510 in #1180 
 perf(answer): embed the question once per call, not once per stage by @swati510 in #1182 
 docs(generation): record what the overlap thresholds actually measure by @swati510 in #1181 
 fix(search): stop asking full-text search for most of the corpus by @swati510 in #1188 
 fix(answer): keep decision vectors and pageless ids out of the answer by @swati510 in #1183 
 feat(docs): the docs tree opens on the shape of the repository, not its contents by @swati510 in #1184 
 feat(docs): the file corpus sits above the layer outline, not under it by @swati510 in #1185 
 fix(docs): the docs tree's outline numbers read as a sequence or not at all by @swati510 in #1186 
 fix(docs): a module with no layer stops being drawn as one by @swati510 in #1187 
 feat(search): index a page's summary and target path by @swati510 in #1189 
 fix(search): drop a tombstoned page from the full-text index by @swati510 in #1190 
 feat(search): centre a hit's evidence snippet on what the query matched by @swati510 in #1191 
 fix(readme): media that actually renders on GitHub by @RaghavChamadiya in #1197 
 fix(embeddings): say which pages lose text at the embedding cap by @swati510 in #1192 
 fix(doctor): reconcile the store against the database again by @swati510 in #1196 
 feat(search): let a page be too thin to be worth indexing by @swati510 in #1198 
 refactor(embeddings): one recipe for every page vector by @swati510 in #1200 
 fix(generation): refuse a structurally-keyed page that has no key by @swati510 in #1201 
 fix(index): tombstone a page whose file is no longer on disk by @swati510 in #1202 
 feat(embeddings): a page below the information floor gets no vector by @swati510 in #1203 
 docs(readme): give the PR bot a section, a picture and a comparison by @RaghavChamadiya in #1205 
 fix(generation): a file page drops the sections it cannot fill by @swati510 in #1206 
 fix(generation): a symbol spotlight drops the importers section when empty by @swati510 in #1207 
 fix(generation): a symbol spotlight carries a render key, and update sweeps it by @swati510 in #1208 
 feat(generation): file pages and spotlights name the questions they answer by @swati510 in #1209 
 fix(generation): add the questions block the tests already assert by @swati510 in #1210 
 fix(ingestion): extract unparenthesized single-parameter arrow functions in JS/TS by @akshatmalik-bruh in #1215 
 feat(generation): module pages stop opening with the same sentence by @swati510 in #1212 
 feat(generation): a module page names its own symbols, not only prose about them by @swati510 in #1211 
 feat(generation): a page says how far it can be trusted by @swati510 in #1213 
 fix(ingestion): filter HTML intrinsic elements from JSX component call targets by @akshatmalik-bruh in #1217 
 docs(readme): cite the 21-repo health validation, drop the PR comment screenshot by @RaghavChamadiya in #1218 
 feat(ingestion): Svelte at the Full tier via a byte-preserving TS projection by @RaghavChamadiya in #1221 
 perf(dead-code): make the dynamic-import package clamp a set lookup by @RaghavChamadiya in #1222 
 feat(health): perf dialects for Kotlin and C++ by @RaghavChamadiya in #1224 
 feat(health): dataflow def/use dialect for C++ by @RaghavChamadiya in #1225 
 perf(dead-code): feed the marker prepasses ingestion's bytes by @RaghavChamadiya in #1223 
 fix(mcp): resolve the embedder API key from persisted config by @RaghavChamadiya in #1230 
 fix(mcp): stop the first tool call racing the lancedb import by @RaghavChamadiya in #1231 
 feat(ingestion): Vue support via a shared single-file-component projection by @RaghavChamadiya in #1232 
 feat(ingestion): HTML at the import tier via script src and link href by @RaghavChamadiya in #1235 
 feat(generation): mine the repository's own vocabulary, ranked and gated by @swati510 in #1233 
 feat(generation): read reStructuredText documents as reStructuredText by @swati510 in #1238 
 fix(tests): restore structlog's global config after every test by @RaghavChamadiya in #1239 
 feat(generation): add configurable synthesis evidence by @serjflint in #1227 
 fix(stats): the punch card's UTC footnote describes, it does not prescribe by @RaghavChamadiya in #1240 
 feat(generation): give onboarding the repository's own vocabulary by @RaghavChamadiya in #1241 
 feat(generation): rank key concepts by what the repository writes about by @RaghavChamadiya in #1242 
 fix(generation): read execution flows by the field names they have by @RaghavChamadiya in #1245 
 feat(generation): the overview counts its packages instead of describing them by @RaghavChamadiya in #1246 
 fix(generation): ground flow narratives in exact source by @serjflint in #1229 
 feat(generation): read reStructuredText documents written under .txt by @RaghavChamadiya in #1247 
 fix(generation): a definition is prose the author wrote, not the markup below it by @RaghavChamadiya in #1248 
 feat(mcp): reach a file page by the words its own file uses, and serve paths a caller can open by @RaghavChamadiya in #1259 
 fix: bound the betweenness pool, keep live update locks, and count failed pages once by @RaghavChamadiya in #1262 
 docs(contributing): document how to claim an issue by @RaghavChamadiya in #1263 
 fix(ts): allow Node.js package exports wildcard to cross directory boundaries by @jyotirmya17 in #1256 
 fix(python): capture correct module path for aliased imports by @jyotirmya17 in #1243 
 docs(examples): add structurizr export walkthrough by @Ayush7614 in #1176 
 refactor(generation): name the per-file vocabulary for what it is by @RaghavChamadiya in #1265 
 refactor(generation): shrink the frozen evidence-files mapping by @serjflint in #1250 
 refactor(generation): validate evidence files in one place by @serjflint in #1251 
 feat(generation): the overview says what the repository does, in its own words by @RaghavChamadiya in #1249 
 fix(tests): stop two update-lock tests asserting the old staleness contract by @RaghavChamadiya in #1267 
 fix(health): teach the Python perf dialect that pathlib is filesystem I/O by @RaghavChamadiya in #1269 
 feat(hooks): measure whether the agent acts on what a hook says by @RaghavChamadiya in #1272 
 perf(cli): stop paying the whole import graph to run one command by @RaghavChamadiya in #1273 
 feat(hooks): the Read hook serves the skeleton instead of recommending it by @RaghavChamadiya in #1275 
 feat(generation): a glossary page, written entirely in the repository's own words by @RaghavChamadiya in #1276 
 fix(hooks): the served skeleton never reached the agent, and the feature had no way in by @RaghavChamadiya in #1278 
 feat(generation): subject chapters, so a subsystem has a page a reader can land on by @RaghavChamadiya in #1282 
 feat(hooks): the search flood is served as its digest, not ranked beside it by @RaghavChamadiya in #1283 
 fix(mcp): hand back the ranked pool the early returns already hold by @RaghavChamadiya in #1284 
 feat(onboarding): Orientation is six pages, and the cut reaches indexes already built by @RaghavChamadiya in #1285 
 perf(telemetry): stop making every command wait out its own telemetry POST by @RaghavChamadiya in #1286 
 docs: publish the measured results, and compare against real peers by @RaghavChamadiya in #1287 
 feat(update): say which orientation page an index has never been offered by @RaghavChamadiya in #1288 
 fix(docker): create /data directory before chown (Blocker 1) by @akshatmalik-bruh in #1266 
 fix(docker): use node:20-bookworm-slim builder for glibc compatibility (Blocker 2) by @akshatmalik-bruh in #1268 
 fix(docker): add .gitattributes to enforce LF line endings for shell scripts (Blocker 3) by @akshatmalik-bruh in #1270 
 docs(cli): document structurizr export in the package README by @Ayush7614 in #1175 
 fix(mcp): let the data-shape fast path read the question, not the whole paste by @RaghavChamadiya in #1289 
 fix(decisions): rank a person above a document, and retire two sources that never landed by @RaghavChamadiya in #1290 
 feat(distill): rewrite safe command chains, and fix what --missed was counting by @RaghavChamadiya in #1291 
 feat(embeddings): the OpenAI embedder honours a configured output width by @serjflint in #1254 
 fix(decisions): stop retiring records on a similarity match, and bound get_why path mode by @RaghavChamadiya in #1293 
 feat(hooks): rank the files the search actually matched, not the index's guess by @RaghavChamadiya in #1296 
 perf(hooks): read the index with stdlib sqlite3 on the three lookups that never needed the ORM by @RaghavChamadiya in #1297 
 release: v0.38.0 - four new languages, orientation rebuilt, search and hooks reworked by @RaghavChamadiya in #1298 
 
 New Contributors 
 
 @serjflint made their first contribution in #1227 
 
 Full Changelog : v0.37.0...v0.38.0