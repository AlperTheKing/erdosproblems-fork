# Erdős #944: 6-Regular `(4,1)` Partial Progress

This artifact package supports the draft PR to `teorth/erdosproblems` for
Erdős problem #944.

## Status

This is **not** a complete solution of Erdős #944. The full `k=4,r=1`
Dirac/Erdős case remains open.

The verified partial result is:

> There is no 6-regular `(4,1)` graph on at most 14 vertices.

The package also records the verified 6-cut rigidity statement:

> In a 6-regular `(4,1)` graph, every nontrivial 6-edge-cut shore has at least
> 15 vertices.

Here `(4,1)` means a 4-vertex-critical graph with no critical edge.
Skottova-Steiner 2025 ask explicitly whether a 6-regular `(4,1)` graph exists
as Problem 5.2.

## Main Files

- `writeup.md`: human-readable proof and verification notes.
- `STATEMENT.md`: precise interpretation of Erdős #944.
- `SURVEY.md`: literature/frontier and novelty notes.
- `PROOF_STATE.md`: proof-state log for the verified lemmas.
- `VERIFICATION_STATUS.md`: compact status and publication checklist.
- `gpt_redteam_2026-06-10.md`: digest of the GPT-5.5 Pro adversarial audit.
- `sixreg/`: C++ checker, CNF files, checker summaries, and n=13 witness.
- `lean/`: Lean 4 core lemmas copied from the local formal-conjectures work.

## Finite Search Summary

```text
n=11: total=266 threecol=3 notVC=263 vcWithCritEdge=0 TARGET=0
n=12: total=7849 threecol=50 notVC=7799 vcWithCritEdge=0 TARGET=0
n=13: total=367860 threecol=849 notVC=367010 vcWithCritEdge=1 TARGET=0
n=14: total=21609301 threecol=42667 notVC=21566634 vcWithCritEdge=0 TARGET=0 badline=0
```

The SMS graph streams are not included here because the n=13/n=14 streams are
large. The CNF files, SMS command shape, checker source, n=14 chunk summaries,
and expected summaries are in `sixreg/README.md`.

## AI Disclosure

This package was produced by an autonomous Codex workflow. GPT-5.5 Pro was used
for mathematical red-teaming; all claims included here were independently
re-derived or checked computationally before promotion to verified status.
