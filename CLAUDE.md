# Project Docs (Obsidian vault)

This repo has a product docs vault under `docs/`, structured for Obsidian. When working on this project, keep it in sync with the rules below — don't create new top-level folders or files outside this structure without asking.

## Folder map & when to update

| Folder | Update when... |
|---|---|
| `docs/01-Overview/Product Overview.md` | The product's vision, target users, or value proposition changes. Rare — only on strategic shifts. |
| `docs/02-Roadmap/Roadmap.md` | A feature moves between Now/Next/Later, or ships (move it to "Done"). |
| `docs/03-Specs/` | A new feature is planned (create a spec from `Templates/Spec Template.md`) or an existing spec's scope/acceptance criteria changes. Add a link in `Specs MOC.md`. |
| `docs/04-Decisions/` | A non-trivial architecture or product decision is made (framework choice, data model, API contract, etc.). Create an ADR from `Templates/ADR Template.md`, named `NNN - Decision Title.md`. Add a link in `Decisions MOC.md`. |
| `docs/05-Tasks/Todo/` | A new task is identified. Create a note from `Templates/Task Template.md`. |
| `docs/05-Tasks/Done/` | A task is completed — move the note here from `Todo/` (don't delete it). |
| `docs/06-Research/` | New user research, competitor analysis, or market findings are gathered. |
| `docs/07-Metrics/` | KPIs/metrics are defined or a new analytics report is produced. |
| `docs/08-Changelog/Changelog.md` | A user-facing change ships — add an entry under `[Unreleased]`, dated when released. |

## Conventions

- All docs are in English.
- Every new note should link back to its section's MOC (e.g. a new spec links to `[[Specs MOC]]`), and the MOC should list the new note.
- Use the templates in `docs/Templates/` when creating specs, ADRs, or tasks — don't freehand the frontmatter.
- Don't restructure the folder layout (rename/add/remove top-level folders) without explicit user approval.

## What NOT to put in docs/

- Code, architecture that's self-evident from reading the source — docs are for decisions, plans, and context that aren't derivable from the code itself.
- Ephemeral notes-to-self; use those only if the user asks for scratch files.
