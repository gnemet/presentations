# presentations

Public publishing surface for the claude-base platform's presentation decks — the one place a
deck is reachable from every tier (a laptop, a server, a customer's browser) without a login.

Every deck here is a **generated copy**. Its source — the `<topic>.deck.md` — stays in the
project it explains and is rebuilt there with `/deck build`; only the self-contained `.html` is
copied into this repo. Never edit a deck here: change the source, rebuild, copy again.

Open a deck straight from disk (`file://…`) or through GitHub Pages at <https://gnemet.github.io/presentations/> (deck URLs follow the repo path, e.g. `docs/presentation/presentation-sdd.html`). Keys: `←/→` navigate,
`?` help, `t` theme, `#talk` in the URL selects the short leaders cut where a deck defines one.

## Decks

| Deck | Title | Source (repo · path · commit) |
|---|---|---|
| [`presentation-sdd.html`](docs/presentation/presentation-sdd.html) | Spec-driven Development (SdD) — módszertan, gyakorlati példával (v5) · HU · ~30 min talk / ~45 min full | infra-forge · `docs/presentation/presentation-sdd.deck.md` · `de66d842` (branch `docs/deck-sdd-public`) |

## Adding a deck

1. In the source repo: edit the `.deck.md`, run `/deck build`, commit source + generated files there.
2. Copy the generated `.html` into `docs/presentation/` here (same filename).
3. Add or update the row above with the source repo, path and commit.
4. Commit and push `main`.
