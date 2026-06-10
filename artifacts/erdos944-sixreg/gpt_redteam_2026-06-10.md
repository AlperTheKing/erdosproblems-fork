# GPT-5.5 Pro cold red-team digest — Erdős #944

Date: 2026-06-10.

Prompt: adversarial audit of the #944 6-regular rigidity package:
local multiplicity, triangle bound, exact 6-cut conflicts, Kempe tether, and
small 6-cut shore exclusion.

## Verdict

GPT-5.5 Pro did not find a mathematical error in claims 1-5, but required
wording and hypothesis corrections.

Accepted after corrections:

1. Local multiplicity is rigorous. State "3-colouring" as a map into a fixed
   3-colour palette; it need not use all colours globally.
2. Triangle bound is rigorous for simple 6-regular targets.
3. Exact 6-cut conflicts is rigorous for a nontrivial partition with both
   shores proper. Each shore is 3-colourable by deleting a vertex on the other
   shore and restricting.
4. Kempe tether is rigorous only in the global graph `G - {e,f}`. Do not
   localize it to one shore without an additional first-crossing argument.
5. Small 6-cut shore exclusion is rigorous. The "proper induced subgraph is
   3-colourable" step must be proved by monotonicity: if `S` is proper, choose
   `v notin S`; then `G[S] subset G-v`, and `G-v` is 3-colourable.

## Single riskiest step

The Kempe tether can be misused. The forced Kempe path is in `G - {e,f}` and
may leave and re-enter a shore. Any later argument treating it as an internal
path of `G[S]` is invalid unless justified by a first-cut-crossing or equivalent
localization argument.

## Literature notes from red-team

- Skottova-Steiner 2025 leave `k=4` open and pose the 6-regular subproblem.
- Their Proposition 5.1 contains the general random-colouring edge-connectivity
  lower-bound idea; cite this for the broad expectation argument.
- Do not cite the local multiplicity, exact 6-cut equality, Kempe tether, or
  small-shore exclusion as named folklore unless a specific source is found.
  They are short enough to prove directly.

Search phrases suggested for final novelty sweep:

- `Kempe chain two monochromatic edges critical graph`
- `vertex-critical graph no critical edge Kempe chain`
- `critical graph edge cut coloring permutation argument`
- `k-vertex-critical no critical edge edge connectivity`

# SECOND cold red-team (wider package) — thread "Cold Review Adversarial Analysis" c/6a29bd3c, 2026-06-10 late

Scope: full Direction-B package (L1.1, C1.2, C1.3, L2.1+C2.2 Kempe tether, L3.1-3.3,
L4.1, T4.3, T5.1-5.3, DICH) + F1-F3 computational facts.

## Verdicts (item-by-item)
- L1.1 VALID/folklore; C1.2 VALID/known (local singleton form of SkSt25 Prop 5.1);
  C1.3 VALID (minor wording); L2.1 VALID ("standard Kempe swap in a new local costume";
  mate-tether possibly new AS A LEMMA but referee sees one-line Kempe argument);
  C2.2 VALID; L3.1 VALID/SkSt idea; L3.2 VALID/known (cut-averaging); L3.3 VALID
  (equality case, "correct and useful"); L4.1 VALID; T4.3 VALID (independently
  reproduced: 21 matrices, 5 types, orbits 3+3+9+3+3); T5.1 VALID (no connectivity
  needed); T5.2 VALID; T5.3 VALID (only type II has row sums (3,3,0)).
- DICH FLAWED AS WRITTEN: "minimum nontrivial atom exactly size 8" NOT proven —
  shores 9,10,... untouched. (NOTE: our twins argument, absent from the audited
  package, kills 8-shores entirely => shores >= 9; sent as follow-up for refereeing.)

## Counterexample hunts (negative = good)
- C1.3: exhaustive n<=6 labelled + atlas n<=7: no failure.
- T5.3: K_{3,3,2}-shore extensions n=9..12 (all outside graphs 1-4 vertices, all
  6-cut-edge placements consistent with T5.2): no target found, no violation.
  K_{3,3,3} (non-target) breaks the rainbow conclusion => target hypothesis essential.

## Novelty layering (per red-team)
- Layer 1 (L1/C1.2/L3.*): known/immediate from SkSt25 Prop 5.1 proof — cite, don't claim.
- Layer 2 (L2.1): valid, technique classical (Kempe-equivalence literature), the
  precise target-local statement may be new as a lemma but is "one-line".
- Layer 3 (T4.3-T5.3): "the genuinely useful part" — elementary but sharp, checkable,
  tailored to SkSt25 Problem 5.2. Kostochka-Yancey / Stiebitz-Tuza-Voigt: no overlap.

## Strongest honest theorem (red-team wording)
Every target has exact 6-cut rigidity (cut matrix = one of the 21 all-diagonals-2
matrices for every cut + side colourings); every nontrivial 6-cut shore >= 8; every
8-shore is induced K_{3,3,2} with both size-3 parts rainbow to the outside.

## Publishability + required fixes
"Partial-progress note: maybe." Fixes: (1) correct DICH wording (or kill 8-shores —
done via twins, pending referee); (2) separate known from new honestly; (3) make
F1-F3 reproducible (graph6 certificates, SMS/nauty commands, verifier code, colouring
count conventions); (4) add a constraint beyond 8-shores (twins => >= 9 + n<=17
super-6-edge-connected corollary is exactly this); (5) Lean cores good, certifying
the enumeration would be the credibility upgrade.
Best framing: "Exact 6-cut obstructions and small-order computations for the
6-regular Dirac k=4 problem."

## Follow-up sent (pending)
Twins-kill referee request + n=14-in-flight publishability + next-theorem triage
(A: exclude 9-shores; B: Kempe-global for super-6-ec candidates; C: n=15-16 with
cut-free pruning).
