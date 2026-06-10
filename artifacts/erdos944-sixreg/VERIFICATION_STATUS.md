# Erdős #944 verification status

Updated: 2026-06-10 Europe/Istanbul.

## Target

Primary #944 target is the last open Dirac case `k=4,r=1`: a 4-vertex-critical
graph with no critical edge, or a proof none exists.

Current publishable-secondary candidate is narrower:

1. verified exhaustive lower bound for the Skottova-Steiner 2025 Problem 5.2
   subproblem: no 6-regular `(4,1)` graph on `n <= 13`;
2. structural rigidity lemmas for any hypothetical 6-regular target.

This is not yet a full resolution of #944.

## Verified Artifacts

- `formal-conjectures/erdos944_cores.lean`
  - Compiles with `lake env lean erdos944_cores.lean`.
  - Clean log: `problems/944/lean_compile_clean.log`.
  - No `sorry`, `admit`, `axiom`, or `unsafe` tokens.
  - Covers:
    - singleton recolouring core of Lemma 1.1;
    - 6-cut matrix count/membership support;
    - numeric Turan shore inequality for `2 <= a <= 7`.

- `experiments/sixreg/check_stream2.cpp`
  - C++ verifier for SMS graph streams.
  - Checks 3-colourability, vertex-criticality, and existence of critical
    edges.
  - Recompiled with progress reporting every 10,000 graphs.

- GPT-5.5 Pro Property-B answer has been decomposed and independently
  re-derived into T1 lemmas in `PROOF_STATE.md`:
  - 6-regular triangle bound: every edge lies in at most four triangles;
  - exact conflict count for 6-edge cuts: every colour gluing has exactly
    two monochromatic cut edges;
  - corrected Kempe tether lemma in `G - {e,f}`;
  - no 6-edge-cut shore of size `2..8` in a 6-regular target.

- Cold GPT-5.5 Pro red-team completed:
  - digest: `problems/944/gpt_redteam_2026-06-10.md`;
  - verdict: claims 1-5 are sound after wording corrections;
  - riskiest step: never use the Kempe tether as shore-internal without an
    additional localization argument.

- Exhaustive enumerations rechecked with standalone C++ summary files:
  - `n=11`: 266 six-regular graphs.
    - `experiments/sixreg/check_n11_summary2.out`
    - SHA256 `9397F2F65C5422AACAAC6EE78F1BA8794A5B1EF643C7483ADA17EE54433E7D7F`
  - `n=12`: 7,849 six-regular graphs.
    - `experiments/sixreg/check_n12_summary2.out`
    - SHA256 `92465A738543C27BEE01A79B4294A2F2D1066FFE43E535F12E59DC183FE2F4C9`
  - `n=13`: 367,860 six-regular graphs.
    - `experiments/sixreg/check_n13_summary2.out`
    - SHA256 `13EC862D7E79951E8DFF5E4BA52173778C8EA8A79C209C922FBB184DD9C7F8EE`
  - Summary from `RESEARCH_LOG.md`: no 6-regular `(4,1)` graph for `n<=13`;
    exactly one 6-regular 4-vertex-critical graph at `n=13`, and it has
    critical edges.

## Pending / Needs Stronger Evidence

- teorth draft PR #314 is open with a one-line database comment. Reviewer may
  request stronger public artifact links before accepting.
- Decide which parts should get additional Lean coverage beyond the current
  cores.

## Current Blocking Mathematical Question

The immediate blocker is no longer the Kempe package itself; it is packaging
and adversarial verification:

- write the rigidity lemmas cleanly with the red-team wording corrections;
- monitor/respond to teorth PR #314 review;
- decide whether to strengthen with a public artifact repository or a pruned
  `n=14` attack.

## Publication Status

- Draft PR: https://github.com/teorth/erdosproblems/pull/314
- Branch: `AlperTheKing/erdosproblems-fork:erdos944-sixreg-progress`
- Commit: `bce7260`
- Scope: one `data/problems.yaml` comment, status remains `open`.
