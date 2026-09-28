# presentations — public deck publishing repo

> **Level 3.** Platform rules: `../docs/all_rules_for_claude.md` (+ axioms: `../docs/00_axioms.md`).
> Deck rules: `../docs/rules/02_coding_implementation/presentation_decks.md`.

- **Copies only.** Every `docs/presentation/*.html` is generated from a `.deck.md` that lives in
  the deck's own project repo. Never edit an `.html` here — rebuild in the source repo with
  `/deck build` and copy the result (A1: the `.deck.md` is the single source; A2).
- **Public repo.** Whatever lands here is world-readable. Before copying a deck, scan it for
  credentials, internal hostnames and customer data; a deck that needs any of them stays in its
  source repo's authenticated `/about/` route instead.
- **No engine, no build, no DB.** A missing deck capability is a `deck-foundation` spec increment
  in `foundation-ui`, never a script or an edit in this repo.
- **Provenance in `README.md`.** Each deck's row names its source repo, path and commit; update the
  row in the same commit as the copy.
- Push policy: github-canonical, direct to `main` (`scripts/repos.yaml` in claude-base is the SSOT).
