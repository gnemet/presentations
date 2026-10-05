# presentations

The home of the claude-base platform's public presentation decks — **source and generated files
together, one folder per deck**. A deck that lives here has no other copy anywhere: projects that
want to show it link to this repo (or to its GitHub Pages URL) instead of embedding it.

Open a deck straight from disk (`file://…`) or through GitHub Pages at
<https://gnemet.github.io/presentations/> (deck URLs follow the repo path). Keys: `←/→` navigate,
`?` help, `t` theme, `#talk` in the URL selects the short leaders cut where a deck defines one.

## Decks

| Folder | Deck | Title | Origin |
|---|---|---|---|
| `spec-driven/` | [`presentation-sdd.html`](spec-driven/presentation-sdd.html) · [notes](spec-driven/presentation-sdd-notes.md) | Spec-driven Development (SdD) — módszertan, gyakorlati példával (v5) · HU · ~30 min talk / ~45 min full | moved here from infra-forge `docs/presentation/` on 2026-09-28 (last copy there: `de66d842`); infra-forge's About page links here |
| `request-to-product-kmtr/` | [`request-to-product-kmtr.html`](request-to-product-kmtr/request-to-product-kmtr.html) · [notes](request-to-product-kmtr/request-to-product-kmtr-notes.md) | Kéréstől a termékig — a KMTR tudástár esete (HU, 30 min, 24 slides, talk cut 18) | claude-base session 2026-09-30, frissítve 2026-10-01 (kapuk, éles-alak tanulság, 2. nap többlete) |
| `ai-orchestration-human-gates/` | [`ai-orchestration-human-gates.html`](ai-orchestration-human-gates/ai-orchestration-human-gates.html) · [notes](ai-orchestration-human-gates/ai-orchestration-human-gates-notes.md) | From Intent to Accepted — AI-orchestrated delivery with human gates (EN, 50 min, 33 slides) | moved here from claude-base `docs/presentation/` on 2026-10-05 (companion brief stays there: `ai-orchestration-human-gates.md`) |
| `kovacs-muhely/` | [`kovacs-muhely-01.html`](kovacs-muhely/kovacs-muhely-01.html) · [notes](kovacs-muhely/kovacs-muhely-01-notes.md) | kovacs-muhely (HU, 14 slides) | moved here from kovacs-muhely `docs/presentation/` on 2026-10-05; internal hostnames, ports and database names generalised for the public repo. Content predates the rag3 name retirement — see kovacs-muhely `docs/specs/rag3-name-retirement/` |
| `platform-base-dev-method/` | [`platform-base-dev-method.html`](platform-base-dev-method/platform-base-dev-method.html) | platform-base — Fejlesztési módszer (HU, 18 slides, chalkboard) | **HTML only** — the source `.deck.md` and the notes stay in the private lookin repo (`docs/presentation/platform-base-dev-method.deck.md`, built at lookin `7872fe0`); rebuild there with `OUT_DIR` pointing at this folder. Renamed from `jirada-dev-method` on 2026-10-05; internal hosts, databases and customer names generalised |

Each folder holds `<topic>.deck.md` (the source of truth), `<topic>.html` and `<topic>-notes.md`
(both generated — never hand-edited). Exception: a deck whose source lives in a private repo publishes its `.html` here only (the
row's Origin names the source path and commit).

## Editing a deck

1. Edit `<folder>/<topic>.deck.md`.
2. Rebuild in place with the platform deck pipeline (`/deck build <abs path to the .deck.md>` in
   a claude-base session); it rewrites the `.html` and `-notes.md` beside the source.
3. Run the deck smoke (`claude-base/docs/presentation/render/smoke-deck.mjs <html>`), review dark and
   light screenshots, then commit all three files together and push `main`.

This repo is **public**: keep credentials, internal hostnames, server names and customer data out of
every deck; a deck that needs them belongs behind a project's authenticated route, not here.
