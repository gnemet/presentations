# presentations — public presentation decks (source of truth)

> **Level 3.** Platform rules: `../docs/all_rules_for_claude.md` (+ axioms: `../docs/00_axioms.md`).
> Deck rules: `../docs/rules/02_coding_implementation/presentation_decks.md`.

- **One folder per deck, one copy anywhere.** `<folder>/<topic>.deck.md` is the source; `<topic>.html`
  and `<topic>-notes.md` beside it are generated and never hand-edited (A1, A2). No other repo keeps a
  copy — a project that shows the deck links here (owner ruling 2026-09-28). Exception: a deck whose
  source lives in another repo (`repo` + `path` in `decks.yaml`) has only its `.html` here.
- **`decks.yaml` is the published list.** Only listed folders go public; the index page and the
  README deck table are generated from it (`site/*.tmpl`).
- **Publishing = the claude-base pipeline `pipelines/docs/DOCS-publish_presentations.md`.** It rebuilds
  every listed deck, gates it (public-safety scan + deck smoke) and pushes the site to `gh-pages`,
  which is what GitHub Pages serves. A push to `main` alone is not live. Spec:
  `../docs/specs/presentations-publish-pf/`.
- **Folder layout is the owner's choice** (`spec-driven/`, not `docs/presentation/`): this repo is the
  deck home itself, so the doc_type-by-subfolder rule of the umbrella does not apply; RAG ingestion is
  off for this repo (`scripts/repos.yaml`).
- **Public repo.** Before every push scan the deck for credentials, internal hostnames, server names
  and customer data; a deck that needs any of them stays behind an authenticated route in its project.
- **No engine of its own, no DB.** A missing deck capability is a `deck-foundation` spec increment
  in the umbrella (`docs/specs/deck-foundation/`) + foundation-ui, never a script or an edit here.
- Push policy: github-canonical, direct to `main` (`scripts/repos.yaml` in claude-base is the SSOT);
  a deck change is documentation, verified by the build, the smoke and reviewed screenshots.
