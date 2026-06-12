# Clearing Conditional Commitments

Working paper, draft v1 (June 2026).

**Clearing Conditional Commitments: Privacy, Specification, and Custody in a Clearinghouse for Interdependent Action** — Timothy J. Miano.

## Contents

- `main.tex` — paper body (canon for all prose, abstract, citations)
- `appendix/` — Propositions 1–3, statements and proofs
- `references.bib` — bibliography (41 entries, citation-verified)
- `figures/make_figs.py` — figure generation
- `main.pdf`, `figures/*.pdf` — build artifacts, committed for convenience
- `SOURCES.md` — canon/precedence map for the source tree

## Build

```bash
tectonic main.tex
```

Figures regenerate via `make_figs.py`, which imports solver scripts from the
numerical companion (`runs/numcheck/`); those scripts live outside this
snapshot, so figure regeneration requires the full working tree. The committed
`figures/*.pdf` are current.

## Provenance

This is a decoupled snapshot of the canonical working tree (private). The
plain-language companion introduction is published separately and is not part
of this repository. Paths in `SOURCES.md` referring to `companion-intro.*` or
`~/om/docs/lit/...` describe the canonical tree, not this snapshot.
