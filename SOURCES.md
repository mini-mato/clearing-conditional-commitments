# Sources of truth — paper-ccc-v1

Last updated 2026-06-11.

## Edit these (canon)

| File                                | Canon for                                                                  |
| ----------------------------------- | -------------------------------------------------------------------------- |
| `main.tex`                          | Paper body: all prose, abstract, byline, citations                         |
| `appendix/P1-{statement,proof}.tex` | Proposition 1 (interior masking band) — statement + proof                  |
| `appendix/P2-{statement,proof}.tex` | Proposition 2 (λ-free selection) — statement + proof                       |
| `appendix/P3-{statement,proof}.tex` | Proposition 3 (bundled dial) — statement + proof + C2 falsification record |
| `references.bib`                    | Bibliography (41 entries, citation-verified)                               |
| `figures/make_figs.py`              | Figure generation (imports the numcheck solvers; do not inline)            |
| `companion-intro.md`                | Plain-language introduction                                                |

## Never edit (build artifacts — regenerate instead)

- `main.pdf` — `tectonic main.tex`
- `figures/*.pdf` — `cd figures && uv run --with numpy --with scipy --with matplotlib python make_figs.py`
- `companion-intro.html` — pandoc (see git history for the css invocation)

## Precedence when content conflicts

```
numcheck solver scripts  >  appendix .tex  >  main.tex body  >  companion-intro.md
```

- All numerical values originate in `~/om/docs/lit/conditional-commitment/runs/numcheck/`
  (seeded, re-runnable). A number in prose that disagrees with a script is a transcription
  error in the prose.
- The body must not claim more than the propositions state (conjecture gates travel with
  claims). The companion must not claim more than the paper.

## Word-review cycle (Tim's editing surface)

`review/paper-body.md` is the human editing surface for the paper body — plain markdown,
regenerated from `main.tex` by `review/extract.py`. It is NOT canon; it is an ephemeral
review copy with a frozen baseline (`review/.baseline-paper-body.md`) for diffing.

The cycle:

1. Claude runs `python3 review/extract.py > review/paper-body.md` and freezes the baseline.
2. Tim edits words directly in `review/paper-body.md` (any editor). Rules are in the file
   header: don't retype `⟦…⟧` placeholders (citations/cross-refs — move or delete only),
   don't edit math spans (math changes go via chat).
3. Tim says "merge my edits". Claude diffs the file against the baseline, applies every
   word change to `main.tex` (placeholders anchor the locations), rebuilds the PDF, and
   regenerates the review copy + baseline. A latexdiff receipt is produced on request.
4. A stale review copy (baseline older than main.tex's last prose edit) must be
   regenerated before editing — never merge from a stale copy.

The companion needs no cycle: `companion-intro.md` is already markdown and already canon —
edit it directly.

## Frozen provenance (historical — do not edit, do not cite as current)

- `~/om/docs/propositions-workdir/P{1,2,3}-draft.md` — original proof drafts; the
  verification record (3-lens adversarial passes) refers to these. The `.tex` appendices
  have post-conversion fixes the drafts lack.
- `~/om/docs/2026-06-10-ifwishlist-anchor-paper-v3.md` — the prose skeleton the paper
  was built from. Contains pre-review claim phrasings the paper has since corrected.
- `~/om/docs/2026-06-11-ifwishlist-propositions-v1.md` — paper-facing propositions
  summary at time of drafting; superseded by the appendix statements.
- `review-codex.md` — Codex referee review (2026-06-11); all blocking/major items applied.
- `~/om/docs/2026-06-0*-ifwishlist-toy-model-v*.md` — the v1–v9 numerical memo chain;
  derivation record, calibrated against the scripts.

## Public site

Live at **https://papers.ifwishlist.com** (Cloudflare Pages project `ifwishlist-papers`;
also https://ifwishlist-papers.pages.dev). `noindex` while in draft — remove
`site/_headers` and the meta-robots tag in `site/index.html` when officially published.
To redeploy after content changes:

```bash
cd ~/om/docs/paper-ccc-v1
cp main.pdf site/clearing-conditional-commitments-wp1.pdf
pandoc companion-intro.md --standalone --katex -o site/companion.html  # (css in git history)
npx wrangler pages deploy site --project-name ifwishlist-papers --branch main
```

Note: papers.ifwishlist.com was previously bound to the `ifwishlist-went-to-market`
parked-redirect Worker; that binding was detached 2026-06-11 (re-attach via Workers
custom domains if ever needed).

## Open gates (as of 2026-06-11)

1. Tim's end-to-end read pass (byline confirmed; MIT affiliate confirmed current).
2. Empirics in/out decision → venue (SSRN recommended).
3. Law review companion: queued behind counsel review of money-flows + WP posting.
