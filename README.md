# Clearing Conditional Commitments

Working paper, draft v1 (June 2026).

**Clearing Conditional Commitments: Privacy, Specification, and Custody in a Clearinghouse for Interdependent Action** — Timothy J. Miano.

## Abstract

Latent willingness of the form "I will, if enough of the right others will" has no
standard clearing institution. We model a conditional-commitment clearinghouse: a
platform that authenticates participants, verifies that their mutual conditions are
jointly satisfiable, routes compatible counterparts to one another, and chooses three
design dials — custody of principal, specification timing, and disclosure granularity —
before activating the coalition at a fixed point. The central result is that the
welfare-maximizing clearinghouse is minimal on all three dials at once: it holds no
principal, fixes terms late, and discloses progress only through a k-anonymized
aggregate. The result is stated with its boundary: it holds in a bounded
high-authenticity, intermediate-integrity region, reverses on each axis outside it, and
the three minimalisms are coupled in welfare magnitude rather than additively separable.
Three further results discipline the disclosure claim: the privacy dial's screening cost
is a genuine information-leakage object (Shannon mutual information between coalition
type and the k-anonymized support count); the masking advantage survives a
refinement-free selection under Carlsson–van Damme risk dominance; and partial masking
is constrained-optimal because a single disclosure dial necessarily bundles "this
coalition is real" with "you are not pivotal."

_JEL:_ C72, D82, D47, H41. _Keywords:_ conditional commitment, coordination, information
design, k-anonymity, market design, assurance contracts.

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
