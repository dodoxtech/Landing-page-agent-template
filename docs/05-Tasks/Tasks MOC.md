---
title: Tasks MOC
tags: [moc, tasks]
created: 2026-07-02
---

# Tasks MOC

Task notes live in two subfolders:

- `05-Tasks/Todo/` — open tasks (not started or in progress)
- `05-Tasks/Done/` — completed tasks

When a task is finished, move its note from `Todo/` to `Done/` (don't just delete it — keep it as a record).

Use `Templates/Task Template.md` when creating a new task note.

## Open tasks
```dataview
LIST FROM "05-Tasks/Todo"
```

## Completed tasks
```dataview
LIST FROM "05-Tasks/Done"
```

## Links
- [[Home]]
- [[Roadmap]]
