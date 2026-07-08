# Agent Instructions

This is the authoritative rules file for any AI coding agent (Claude Code, Cursor,
GitHub Copilot, Aider, etc.) working in a project that uses this starter kit. Agents
that don't read AGENTS.md natively should be pointed at it via their own config file
— see `docs/vibe-coding/` for per-tool instructions. `CLAUDE.md` imports this file.

## 1. Trigger "e" or "enhance"

If the user types "e", "enhance", or requests an enhancement plan:
- Read `/plans/next-enhancements.md` to understand the current platform structure, history, and active tasks.
- Overwrite or update the active tasks list inside `/plans/next-enhancements.md`.
- The plan must cover each main section/module of the application.
- Inside the tasks list, define **exactly 3 new enhancements per section** with:
  1. A unique number (e.g., `1.1`, `1.2`, `1.3`).
  2. A clear, specific description of the functional change.
  3. A status (initially set to `[TODO]`).
- Present this plan to the user in your final summary response.

## 2. Trigger "n", "next", or "n{x}"

If the user types "n", "next", "n{x}" (where `{x}` is a positive integer), or requests execution of the next enhancement task(s):
- Read `/plans/next-enhancements.md` to check the status of tasks.
- If all tasks are `[DONE]` (or none are `[TODO]`), automatically run the **"e" / "enhance"** workflow first.
- Otherwise, select the most impactful `[TODO]` task(s) by strategic value, functional impact, or UX contribution — not just the first in order. If `{x}` is given, select the top `{x}` tasks and execute them sequentially.

### 2a. Clarify before building ("Grill Me" step)

Before implementing a task, check whether its scope or acceptance criteria are
genuinely ambiguous (multiple valid interpretations, unspecified UI/data behavior,
no clear "done" condition). If so:
- Ask clarifying questions **one at a time** until the task is unambiguous — use
  your tool's native mechanism (e.g. Claude Code's `AskUserQuestion`) where available,
  otherwise ask inline and wait for the answer before continuing.
- Record the resolved acceptance criteria as a short 1-3 line note next to the task
  entry in `/plans/next-enhancements.md` before writing any code.
- Skip this step entirely when the task is already unambiguous — don't grill the
  user on obvious work.

- Implement the selected task(s) fully in the codebase, applying the relevant role(s)
  from `SKILLS.md` (Architect, Backend, Frontend, QA, Hardware/Compatibility).
- Once complete:
  1. Update the task's status in `/plans/next-enhancements.md` to `[DONE]`.
  2. Document the new/updated feature in `/docs/feature-list.md` under the right section heading.
- **Verify build integrity** — this is not just "it compiles and runs":
  - QA pass: exercise the golden path and edge cases; run/extend automated tests.
  - Hardware/Compatibility pass: check cross-platform, cross-browser, and resource
    (memory/CPU) assumptions per `SKILLS.md`.
- In your final response, state which task(s) were completed and the exact menu/navigation path to see the new feature.

## 3. File Size & Refactoring Rules

- **256-line threshold**: any code/script file — new, modified, or pre-existing —
  that exceeds 256 lines of code must be split into smaller, modular, logical files.
  This is a repo-wide rule, not just for new work; if you touch a file over the
  threshold, split it as part of that change.
- **Why**: an agent reading a file spends its context budget parsing it before it can
  reason about the task. Small, single-purpose files keep that cost low and keep the
  agent's understanding accurate (see the "smart zone / dumb zone" problem — models
  reason worse as context fills up).
- This applies to AGENTS.md, CLAUDE.md, and SKILLS.md too: keep each under ~250 lines.
  Push detail into linked docs (`docs/`) rather than growing the root files.

## 4. Roles

Every implementation task should be viewed through the lens of the relevant role(s)
defined in `SKILLS.md`: Software Architect, Backend Engineer, Frontend Engineer,
QA/Test Engineer, and Hardware & Performance Compatibility Reviewer. A single agent
plays all roles in sequence unless the harness supports spawning role-specific
subagents (see `CLAUDE.md`).

## 5. Mockup Data & Demo/Live Mode

- Store all mock/sample data in `/data/mockup/` — keep it separate from UI components and styling.
- Provide a mock API layer that reads from `/data/mockup/` and mirrors the real backend contract.
- Add a switcher control (icon) in the UI to toggle **Demo** (mock API + mock data) and **Live** (real API + real data).

## 6. Cloud vs Local (On-Premise)

- Provide a setting to choose **Cloud** or **Local (on-premise)** deployment.
- **Cloud**: use remote/cloud-hosted API endpoints and services.
- **Local**: use on-premise/self-hosted API endpoints and services.
- Persist the selection and route all backend/service calls to the chosen environment.

## 7. Ad-hoc Feature Requests

For direct feature requests not using "e"/"n", implement the feature and document it in `/docs/feature-list.md`.
