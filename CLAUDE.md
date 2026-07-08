@AGENTS.md

# Claude Code Addendum

The rules above are the shared, cross-tool source of truth — keep them in AGENTS.md,
not here, so Cursor/Copilot/other agents stay in sync (see `docs/vibe-coding/`).

Claude-specific notes:

- **Role subagents**: when a task benefits from a fresh, unbiased pass — code review,
  QA verification, architecture check — spawn the relevant `SKILLS.md` role via the
  `Agent` tool instead of continuing in the current context. This mirrors the
  "review in a fresh context window" practice: a context that has been implementing
  a feature is a worse reviewer of that same feature.
- **Clarifying questions** (AGENTS.md §2a): use `AskUserQuestion` for the one-at-a-time
  grilling step, not free-text questions buried in a longer response.
- **Plan mode**: for any `n`/`next` task that touches multiple files or has more than
  one reasonable implementation approach, use `EnterPlanMode` before writing code.
