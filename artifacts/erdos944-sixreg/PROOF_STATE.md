# (appended 2026-06-10 ~14:20) Consult-1 digest (chat "Erdos Dirac Graph Conjecture" c/6a294081)
PENDING claims to verify:
- [P1] Cut Lemma: 4-vertex-critical G, vertex partition with cut size ≤5 ⟹ some cut edge critical.
  (Random S3-permutation of one side's 3-coloring: E[mono]=cut/3<2; 0 impossible ⟹ some π gives exactly 1
  ⟹ that edge critical.) RE-DERIVED, looks sound ⟹ near-T1; NOVELTY CHECK vs SkSt25 needed (they ask the
  6-regular question explicitly ⟹ δ≥6 corollary likely known there — verify before any claim).
- [P2] Corollaries: any (4,1)-target is 6-edge-connected; δ≥6; star of any degree-≤5 vertex contains a
  critical edge (explains SA floor at small n); n ≥ 11 (with Δ ≤ n−5 claim — verify that step); n=11 ⟹
  6-regular, 33 edges (SkSt25's explicit open subquestion).
- [P3] Jensen anatomy: circulant construction; k≥5 needed for nonempty long-distance intervals (+ forced
  periodicity wrap argument); k=4 specialization degenerates. (Citation-level; verify from SkSt25/Jensen.)
- [P4] Candidate: Schrijver SG(2q+2,q) (n=(q+1)²=25,36,49; 4-chromatic vertex-critical) as H-seeds +
  dihedral-orbit extra edges S (δ≥6, kill edge-criticality); α(G−e)≤⌈n/3⌉−1 certificate for non-3-col.
  Edge-transitive families of degree ≤5 ruled out by P1.
Next iterations: (1) verify P1/P2 + check stuck-graph δ in data; (2) build SG(10,4)+orbit-S search;
(3) SMS exhaustive n=11 6-regular (lower-bound product); (4) fetch SkSt25 full text (lemma novelty + their
exact open subquestions). Budgets: iter 5/40, consults 1/12.

# (2026-06-10 ~22:00) Deep-math consult result: RIGIDITY PACKAGE (Direction B)
- [VERIFIED T1] Lemma 1.1 (singleton color class in N(v) under any 3-coloring of G-v => that edge critical;
  re-derived independently). Corollary: targets need every color class >=2 in every neighborhood => delta>=6
  (local form of SkSt25 Prop 5.1, cited honestly).
- [VERIFIED T1] Corollary 1.3 (NEW-looking): c(G) >= (1/2) sum_v max(0, 6-d(v)) critical edges.
- [VERIFIED T1] Lemma 3.1 cut-matrix form; D_pi >= 2 for all pi in targets; |F| >= 6.
- [VERIFIED T0/T1 ★] Theorem 4.3 (NEW-looking): exact 6-cut obstruction — cut matrix must be one of FIVE
  types (row sums (6,0,0),(3,3,0),(4,1,1),(2,2,2)); MACHINE-VERIFIED: exhaustive over all 3x3 sum-6
  matrices: exactly 21 satisfy all-diagonals>=2, exactly 5 canonical types, matching GPT statement 1:1.
- [PENDING] Property A (every edge of 6-regular target in <=4 triangles); Property B (Kempe tethers);
  Property C consequences (no 6-cut shore of size 2..7; size-8 shore forced = K_{3,3,2}; 6-regular target
  super-6-edge-connected or atoms >= K_{3,3,2}). Verify next (incl. test against unique n=13 graph).
- Unique n=13 6-regular 4-vertex-critical graph: critical edges form a HAMILTON CYCLE (13 edges, verified).
- NEXT: (1) read weakest-steps; (2) machine-verify A/B/C on n=13 unique graph; (3) novelty sweep on the
  rigidity package; (4) decision: publishable SECONDARY package (rigidity theorems + n<=13 exhaustion +
  unique graph) vs continue to n=14 with theoretical pruning.

# (2026-06-10 ~22:30) Lean cores repaired and compiled
- `E:\Projects\ErdosProblems\formal-conjectures\erdos944_cores.lean` now compiles with
  `lake env lean erdos944_cores.lean` (clean log: `lean_compile_clean.log`).
- No `sorry`/`admit`/`axiom`/`unsafe` tokens in the file.
- T2 cores currently covered:
  (1) `singleton_edge_critical`, the recolouring core of Lemma 1.1;
  (2) cut-matrix count/membership support (`cut_matrix_classification`,
      `matrix_mem_classification`) for the 6-cut obstruction, with canonical five-type
      reduction still recorded as external exhaustive Python/C++ certificate;
  (3) `turan_count_shore`, the numeric shore bound for sizes 2..7.
- Axiom check sample:
  `singleton_edge_critical` does not depend on any axioms;
  `turan_count_shore` depends only on `[propext, Classical.choice, Quot.sound]`.
  Need rerun/record full axiom print for cut-matrix names after module import path is packaged or by
  temporary in-file `#print` if desired.

# (2026-06-10 ~23:00) GPT-5.5 Pro Property-B answer received and independently re-derived
- GPT correction: the earlier "small shore size 8 may be a K_{3,3,2} atom" endpoint is too weak.
  In a 6-regular 4-vertex-critical graph such a shore is actually impossible, because the two vertices
  in the size-2 part of `K_{3,3,2}` have internal degree 6, no external neighbours, and are non-adjacent
  twins. Non-adjacent twins contradict vertex-criticality.
- [VERIFIED T1] Local multiplicity lemma restated cleanly:
  In any 3-colouring of `G-v`, each colour appears at least once in `N(v)`; if a colour appears exactly
  once, say only at `u`, then `G-uv` is 3-colourable by colouring `v` with that singleton colour.
  Hence every target has no singleton colour class in any `N(v)` under any 3-colouring of `G-v`;
  in the 6-regular case the three colour multiplicities are exactly `(2,2,2)`.
- [VERIFIED T1] Property A / triangle bound:
  In a 6-regular target, no edge `uv` can satisfy `N(u) \ {v} subset N(v)`. In particular every edge
  lies in at most four triangles. If `uv` had five common neighbours, then in any 3-colouring of `G-u`
  the colour of `v` appears exactly once in `N(u)`, forcing `uv` critical by the local multiplicity
  lemma.
- [VERIFIED T1] Exact 6-cut conflict count:
  For a nontrivial partition with both shores proper, a cut `F` of size 6, and fixed 3-colourings of both
  shores, every permutation of the colours on one shore has exactly two monochromatic cut edges.
  Each shore is 3-colourable by deleting a vertex on the other shore and restricting. Then zero conflicts
  would 3-colour `G`, one conflict would make that one edge critical, and the sum over the six colour
  permutations is `2|F| = 12`.
- [VERIFIED T1] Property B / corrected Kempe tether:
  Let a 6-cut gluing permutation have exactly two conflict edges `{e,f}`. If `e = xy` has conflict
  colour `a`, then for every `b != a`, the endpoints `x,y` lie in the same `(a,b)`-Kempe component of
  `G - {e,f}`. Otherwise swapping colours `a,b` in the component of `x` removes the conflict on `e`
  while `f` is deleted, giving a 3-colouring of `G-f`, contradiction.
  Important scope: this is a global tether through `G-{e,f}`, not a purely internal-shore connectivity
  statement. Any later shore-local use must pass through a separate first-cut-crossing argument.
- [VERIFIED T1] Small 6-cut shore exclusion:
  If `G` is 6-regular and `|delta(S)| = 6`, then `e(G[S]) = 3|S|-3`. Since `S` is a proper induced
  subgraph, choose `v notin S`; `G-v` is 3-colourable and `G[S] subset G-v`, so `G[S]` is 3-colourable.
  Thus `e(G[S]) <= floor(|S|^2/3)`.
  This excludes `2 <= |S| <= 7`. For `|S|=8`, equality forces `G[S] = K_{3,3,2}`, and the size-2
  part gives non-adjacent twins of full degree 6, contradicting vertex-criticality. Therefore no
  6-edge-cut shore has size `2..8`.
- [GPT RED-TEAM PASSED WITH WORDING CORRECTIONS] Cold adversarial audit on 2026-06-10 found no mathematical
  counterexample to claims 1-5, but required: fixed 3-colour palette wording; nontrivial/proper shores for the
  cut lemma; Kempe tether only in global `G-{e,f}`; monotonicity proof for `G[S]` 3-colourability.
  Digest: `problems/944/gpt_redteam_2026-06-10.md`.
- [PENDING before publication] Put the corrected package into final write-up, run final novelty sweep, and decide
  which pieces should be Lean-formalized beyond the existing cores.

# (2026-06-10 late) Session continuation: Lean cores + Property A/B/C verification COMPLETE
- LEAN CORES COMPILED CLEAN (erdos944_cores.lean, exit 0, axioms verified):
  * singleton_edge_critical (Lemma 1.1 core): NO axioms at all (fully constructive).
  * cut_matrix_classification (Thm 4.3 count=21 via comps 9 6 enumeration, 3003 weak compositions
    + mem_comps completeness lemma): [propext] only. 7^9 decide replaced by composition encoding.
  * matrix_mem_classification (matrix-form bridge, Equiv.Perm instantiation at 6 explicit perms),
    mem_comps, turan_count_shore: [propext, Classical.choice, Quot.sound]. No sorry, no native_decide.
- PROPERTY B (Kempe tethers) = Lemma 2.1 + Cor 2.2 of GPT Direction-B reply: READ IN FULL, VERIFIED
  line-by-line (swap on mate-component, x' leaves colour 1, no new colour-1 boundary by assumption,
  v gets colour 1 in G-vx => vx critical; boundary patterns (2,2) or (1,1)+(1,1)). T1.
- PROPERTY A VERIFIED: 2+2+2 split (Cor 1.2 + 6-regular) => same-colour pairs are complement edges
  => perfect matching in complement of G[N(v)] => every edge in <=4 triangles. T1.
- PROPERTY C VERIFIED: Thm 5.1 (shores 2..7 impossible) + Thm 5.2 (8-shore => K_{3,3,2}, double
  equality: e(G[A])=21=Turan bound, all degrees exactly 6, part-2 no cut edge, part-3 one each) +
  Thm 5.3 (double-rainbow: unique K_{3,3,2}-colouring => boundary (3,3,0) => only type II) +
  dichotomy (super-6-edge-connected OR atoms >=8 with smallest exactly K_{3,3,2}). T1.
- Lemma 4.1/4.2 alt derivation VERIFIED: D_pi=2 forall pi => 2x2 additive condition => m_ij=(R_i+C_j-2)/3
  => row/col sums congruent mod 3 => row sums in {(6,0,0),(3,3,0),(4,1,1),(2,2,2)} => five types
  I..V with orbit sizes 3+3+9+3+3 = 21 = Lean count. Analytic + machine agreement.
- MACHINE TESTS (new):
  * verify_lemma21_n13.py: unique n=13 graph: 78 vertex-deleted colourings, ZERO of type 2+2+2
    (graph is everywhere-singleton!); 156 Lemma-1.1 predictions, 0 false positives, 13/13 critical
    edges covered. Kempe mechanism vacuous on n=13 (no 2+2+2 colourings) - notable rigidity datapoint.
  * test_lemma21_random.py: Lemma 2.1 as standalone implication stress-tested on random 4-chromatic
    graphs: 19389 tether-failure implications across 451 graphs, 0 counterexamples.
- PRs: deepmind #4218 all CI green (Build+CLA), no human review yet; teorth #313 open, no comments.
- NEXT: cold-context red-team (new GPT thread) -> writeup -> publish (teorth problems.yaml #944
  comment PR + optional formal-conjectures 944.lean).

# (2026-06-11 ~00:10) Verified n=14 closure and 9-shore exclusion
- [VERIFIED NUMERICALLY, DOUBLE CHUNK CHECK] The 6-regular n=14 enumeration is closed:
  two independent native chunk partitions give the same totals.
  * `experiments/sixreg/n14_chunks` (110 residue classes):
    `total=21609301 threecol=42667 notVC=21566634 vcWithCritEdge=0 TARGET=0 badline=0`.
  * `experiments/sixreg/n14_chunks_v2` (73 residue classes):
    `total=21609301 threecol=42667 notVC=21566634 vcWithCritEdge=0 TARGET=0 badline=0`.
  Thus there is no 6-regular 4-vertex-critical graph on 14 vertices at all, hence no
  6-regular `(4,1)` target on `n <= 14`. The redundant live stream rerun
  (`smsg`/`check_stream_mt`) was stopped after this verification.
- [VERIFIED NUMERICALLY + T1 local argument] No 9-vertex shore of a nontrivial
  6-edge-cut can occur in a 6-regular `(4,1)` target.
  * Candidate setup: a 9-shore `A` has `e(G[A]) = 24`, `Delta(G[A]) <= 6`, and
    deficiency vector `b(v) = 6 - deg_A(v)` with total 6.
  * Exhaustive nauty/C++ filter:
    `geng -c -D6 9 24:24 | enum_9shore.exe` classifies 729 connected candidates:
    `711` not 3-colourable, `9` violate the 6-cut boundary-vector condition, `8`
    have a comparable non-neighbour at a `b=0` vertex, and exactly one survives:
    graph6 `HEzftz{`, `b=011101110`, `ncol=6`.
  * Independent Python recount (`verify_9shore_survivor.py`) reproduces the same
    `711/9/8/1` classification and prints the survivor edge list.
  * Kill test (`kill_9shore_survivor.py`): the survivor has internal vertices
    `{0,4,8}`. For each such vertex `v`, all 6 proper 3-colourings of `H-v`
    leave some colour appearing at most once on `N_H(v) = N_G(v)`, contradicting
    the local multiplicity lemma. Hence the survivor cannot embed as a 9-shore.
  Conclusion: in a 6-regular `(4,1)` target every nontrivial 6-edge-cut shore has
  size at least 10, and therefore any such graph on `n <= 19` is
  super-6-edge-connected (only vertex-star 6-cuts).
- Scope warning: the 9-shore exclusion uses 6-regularity (`b(v)=6-deg_A(v)` and
  internal vertices with `N_G(v)=N_A(v)`). Do not state it for general
  `delta >= 6` targets without a separate argument.

# (2026-06-11 ~00:20) SHORE-EXCLUSION MACHINE: 9,10,11,12 ALL EXCLUDED (a=13 running)
- Native pipeline (user directive: no WSL): geng.exe (nauty 2.8.9, clang-built, validated
  vs SMS chain exactly) + enum_shore.cpp filter battery, all NECESSARY conditions:
  [B] b(v)=6-deg in [0,5]; [C] 3-colourable + EVERY colouring's deficiency-weighted
  boundary vector in {(6,0,0),(3,3,0),(4,1,1),(2,2,2)} (T4.3 row sums, beta-independent);
  [T] folklore comparable-nonneighbours at b=0 vertices; [K] GENERALIZED local kill:
  for every v, exists proper colouring of H-v with sum_i max(0,2-cnt_{N_A(v)}(i)) <= b(v)
  (necessity: chi(G-v)=3 colouring needs every colour >=2 on N_G(v) by Lemma 1.1+target,
  cut neighbours supply at most b(v)).
- G[A] connected forced (any component would use all 6 cut edges; a second component
  disconnects G). e(G[A]) = 3a-3 exact (6-regular).
- RESULTS (native C++; a=9,10 also independently verified in Python):
  a=9:  729 cands: 711 not3col, 9 badvec, 8 twins, 1 localKill (H=K333-rainbow-matching,
        g6 HEzftz{, killed: all 6 colourings of H-v leave a colour <=1 on N(v), v in
        {0,4,8}; ALSO 3^8 brute-force confirmed) => 0 SURVIVORS.
  a=10: 18,655: 18,345/197/86/27 => 0 SURVIVORS.
  a=11: 696,208: 687,377/6,013/1,300/1,518 => 0 SURVIVORS.
  a=12: 32,833,744 (110 chunks): 32,484,081/241,863/27,322/80,478 => 0 SURVIVORS.
- THEOREM (current): every nontrivial 6-edge-cut shore in a 6-regular (4,1)-graph has
  >= 13 vertices => every 6-regular target on n <= 25 is super-6-edge-connected.
  (a=13, e=36, ~1.5e9 cands estimated, 110 chunks RUNNING -> would give shores>=14, n<=27.)
- n=14 SLICE CLOSED DOUBLE-VERIFIED (mod-110 + mod-73 identical): 21,609,301 graphs
  (= published count), 0 six-regular 4-VC at n=14 => Problem 5.2 needs n >= 15.
