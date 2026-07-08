# Agents Settings

**Agents Settings** is a reusable starter kit of governance files for running a
project with autonomous AI coding agents (Claude Code, Cursor, GitHub Copilot,
Aider, and others). It contains no application code — copy its files into a new
project's root to instantly bootstrap the workflow, roles, and rules below.

---

## 🚀 How It Works

Development is driven by two triggers issued by the user, plus an onboarding step
that runs ahead of them when needed — all defined in full in [AGENTS.md](AGENTS.md).

### 0. Adopting Into an Existing Project (auto / `i` / `init`)
Dropped into a codebase that already has files/history, the kit auto-detects that on
the first `e`/`n` run and audits the real stack, build/test commands, folder
structure, and existing conventions before doing anything else — no separate step
needed on a new project, though typing `i`/`init` forces a re-audit any time (e.g.
after a big refactor). See AGENTS.md §0.

### 1. Enhancement Planning (`e` / `enhance`)
Reads `plans/next-enhancements.md`, then defines exactly 3 numbered `[TODO]`
enhancements per section/module and presents the plan.

### 2. Task Execution (`n` / `next` / `n{x}`)
Picks the most impactful `[TODO]` task(s), clarifies ambiguous scope one question at
a time before writing code (the "Grill Me" step — see AGENTS.md §2a), implements the
task through the roles in [SKILLS.md](SKILLS.md), verifies build integrity (QA +
Hardware/Compatibility passes), marks the task `[DONE]`, and documents it in
`docs/feature-list.md`.

Every code file is capped at 256 lines before it must be split — see AGENTS.md §3.

---

## 📁 Repository Structure

* **[AGENTS.md](AGENTS.md)** — cross-tool workflow rules and triggers (read by Cursor,
  Copilot, Aider, etc. — see `docs/vibe-coding/`).
* **[CLAUDE.md](CLAUDE.md)** — imports AGENTS.md; adds Claude Code-specific notes
  (subagent use, plan mode, AskUserQuestion).
* **[SKILLS.md](SKILLS.md)** — the five roles an agent applies to every task: Software
  Architect, Backend Engineer, Frontend Engineer, QA/Test Engineer, and Hardware &
  Performance Compatibility Reviewer.
* **`plans/`**
  * **`plans/next-enhancements.md`** *(updated dynamically)* — the active enhancement
    plan and task statuses.
* **`docs/`**
  * **`docs/feature-list.md`** *(updated dynamically)* — structured log of shipped features.
  * **`docs/vibe-coding/`** — per-tool integration guides:
    [Antigravity CLI](docs/vibe-coding/antigravity-cli.md) | [Antigravity IDE](docs/vibe-coding/antigravity-ide.md) |
    [Cursor Composer](docs/vibe-coding/cursor-composer.md) | [Cursor IDE](docs/vibe-coding/cursor-ide.md) |
    [GitHub Copilot Workspace](docs/vibe-coding/copilot-workspace.md) | [VS Code IDE](docs/vibe-coding/vs-code.md) |
    [OpenHands Agent](docs/vibe-coding/openhands-agent.md) | [OpenCode IDE](docs/vibe-coding/opencode-ide.md) |
    [Aider CLI](docs/vibe-coding/aider-cli.md)
* **`data/mockup/`** — mock/sample data for Demo mode (AGENTS.md §5), kept separate
  from application code.

---

## 🧰 Using This as a Starter Kit

1. Copy `AGENTS.md`, `CLAUDE.md`, `SKILLS.md`, `plans/`, `docs/`, and `data/mockup/`
   into the root of your new project.
2. **New project**: just type `e`/`enhance` and let the agent draft
   `plans/next-enhancements.md` from scratch. **Existing project**: the agent
   auto-detects real files/history on the first `e`/`n` run and audits the actual
   stack/structure/conventions first (or type `i`/`init` to force that audit anytime)
   — see AGENTS.md §0.
3. Point your tool at `AGENTS.md` if it doesn't read it automatically — see
   `docs/vibe-coding/` for the exact file/setting each tool needs.
4. Start driving work with `e` and `n` as described above.

---

## 🛠️ Contribution Guidelines

* Keep docstrings, comments, and existing tests intact unless requested otherwise.
* Always verify the build and runtime integrity before finalizing tasks.
* Ensure documentation updates are clean, structured, and consistent with the
  existing documentation format.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
