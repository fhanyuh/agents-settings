# Next Enhancements

This file is the working backlog driven by the `e`/`enhance` and `n`/`next` triggers
defined in [AGENTS.md](../AGENTS.md). It is empty until the kit is applied to a real
project — running `e`/`enhance` for the first time will populate it with real
sections and tasks.

## Format

Tasks are grouped under a numbered section per module of the application. Each
section gets exactly 3 tasks:

```
## 1. <Section / Module Name>

- **1.1** [TODO] <clear, specific description of the functional change>
- **1.2** [TODO] <...>
- **1.3** [TODO] <...>
```

When a task is picked up via `n`/`next`, its clarified acceptance criteria (from
AGENTS.md §2a) are appended directly under it as a short note, e.g.:

```
- **1.1** [TODO] <description>
  - Acceptance: <1-3 line resolved scope, from the clarification step>
```

When complete, the status flips to `[DONE]` and the feature is logged in
[docs/feature-list.md](../docs/feature-list.md).

---

*(No sections yet — run `e` / `enhance` to generate the first plan.)*
