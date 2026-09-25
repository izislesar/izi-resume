# izi-resume — Autonomous Agent Contract

This project is developed by multiple autonomous AI agents.

The authoritative documents are:

1. `RESUME.md` — factual source of truth for personal/resume information.
2. `MASTER_SPEC.md` — product and visual specification.
3. Beads database — execution graph, dependencies, ownership and project memory.
4. Git — source code history and worktree isolation.

## Mandatory startup sequence

Every agent session MUST:

1. Read `AGENTS.md`.
2. Read `MASTER_SPEC.md`.
3. Read `RESUME.md`.
4. Run `bd prime`.
5. Inspect ready/assigned work.
6. Inspect the complete Beads task before implementation.
7. Claim the task atomically unless explicitly assigned.
8. Inspect dependencies and relevant neighboring tasks.
9. Implement only the task scope.
10. Validate the result.
11. Update Beads.
12. Commit the work in the current git worktree.

## Resume truth

Never invent personal information.

Never infer missing resume facts.

Never add technologies because they are common for the architecture.

Never add employers, projects, dates, metrics, cloud providers or skills unless present in `RESUME.md`.

If a required factual value is absent from `RESUME.md`, stop that part of the implementation and record the blocker.

## Beads

Beads is mandatory.

Do not use:

- TODO.md
- task lists in random markdown files
- hidden agent memory files
- ad-hoc JSON task queues

Use:

- `bd ready`
- `bd show`
- `bd update <id> --claim`
- `bd assign`
- `bd comment`
- `bd close`
- `bd dep add`
- `bd remember`

Use `bd remember` for durable architectural discoveries.

## Worktree ownership

Each autonomous agent operates in its own git worktree/branch.

Do not edit another agent's worktree.

Avoid modifying shared files outside your ownership boundary.

If integration is required, create a Beads dependency rather than silently editing another stream's code.

## Shared architecture

Do not create duplicate implementations of:

- ocean
- scene director
- resume parser
- asset loader
- navigation state

Prefer the canonical subsystem already established by the relevant workstream.

## No placeholder finalization

Temporary placeholders may exist during an explicitly marked blocked integration step.

They must never be accepted as final production assets.

## Validation

Before closing a task:

- run the narrowest relevant tests
- run typecheck/build when relevant
- visually inspect the result for visual tasks
- inspect git diff
- verify no unrelated files changed
- document relevant limitations

## Handoff

When a task produces something another agent needs:

1. commit it
2. close the task
3. leave a Beads comment describing:
   - what was produced
   - important APIs/files
   - known limitations
   - integration requirements

## Conflicts

If another workstream owns a file or subsystem:

- do not overwrite it
- do not fork a competing architecture
- add a dependency/comment
- coordinate through Beads

## Scope discipline

The project has an intentionally constrained visual vocabulary.

Do not introduce new technology mascots or visual metaphors without an explicit specification change.

## Autonomous behavior

Do not ask the human for routine implementation decisions that are already defined by:

- `MASTER_SPEC.md`
- `RESUME.md`
- the active Beads task
- established architecture

If a genuine ambiguity blocks correctness, record it in Beads and continue with independent work where possible.


<!-- BEGIN BEADS INTEGRATION v:1 profile:minimal hash:46cd31e7 -->
## Beads Issue Tracker

This project uses **bd (beads)** for issue tracking. Run `bd prime` to see full workflow context and commands.

### Quick Reference

```bash
bd ready              # Find available work
bd show <id>          # View issue details
bd update <id> --claim  # Claim work
bd close <id>         # Complete work
```

### Rules

- Use `bd` for ALL task tracking — do NOT use TodoWrite, TaskCreate, or markdown TODO lists
- Run `bd prime` for detailed command reference and session close protocol
- Use `bd remember` for persistent knowledge — do NOT use MEMORY.md files

**Architecture in one line:** issues live in a local Dolt DB; sync uses `refs/dolt/data` on your git remote; `.beads/issues.jsonl` is a passive export. See https://github.com/gastownhall/beads/blob/main/docs/core-concepts/sync-concepts.md for details and anti-patterns.

## Agent Context Profiles

The managed Beads block is task-tracking guidance, not permission to override repository, user, or orchestrator instructions.

- **Conservative (default)**: Use `bd` for task tracking. Do not run git commits, git pushes, or Dolt remote sync unless explicitly asked. At handoff, report changed files, validation, and suggested next commands.
- **Minimal**: Keep tool instruction files as pointers to `bd prime`; use the same conservative git policy unless active instructions say otherwise.
- **Team-maintainer**: Only when the repository explicitly opts in, agents may close beads, run quality gates, commit, and push as part of session close. A current "do not commit" or "do not push" instruction still wins.

## Session Completion

This protocol applies when ending a Beads implementation workflow. It is subordinate to explicit user, repository, and orchestrator instructions.

1. **File issues for remaining work** - Create beads for anything that needs follow-up
2. **Run quality gates** (if code changed) - Tests, linters, builds
3. **Update issue status** - Close finished work, update in-progress items
4. **Handle git/sync by active profile**:
   ```bash
   # Conservative/minimal/default: report status and proposed commands; wait for approval.
   git status

   # Team-maintainer opt-in only, unless current instructions forbid it:
   git pull --rebase
   bd dolt push
   git push
   git status
   ```
5. **Hand off** - Summarize changes, validation, issue status, and any blocked sync/commit/push step

**Critical rules:**
- Explicit user or orchestrator instructions override this Beads block.
- Do not commit or push without clear authority from the active profile or the current user request.
- If a required sync or push is blocked, stop and report the exact command and error.
<!-- END BEADS INTEGRATION -->

<!-- BEGIN BEADS CODEX SETUP: generated by bd setup codex -->
## Beads Issue Tracker

Use Beads (`bd`) for durable task tracking in repositories that include it. Use the `beads` skill at `.agents/skills/beads/SKILL.md` (project install) or `~/.agents/skills/beads/SKILL.md` (global install) for Beads workflow guidance, then use the `bd` CLI for issue operations.

### Quick Reference

```bash
bd ready                # Find available work
bd show <id>            # View issue details
bd update <id> --claim  # Claim work
bd close <id>           # Complete work
bd prime                # Refresh Beads context
```

### Rules

- Use `bd` for all task tracking; do not create markdown TODO lists.
- Run `bd prime` when Beads context is missing or stale. Codex 0.129.0+ can load Beads context automatically through native hooks; use `/hooks` to inspect or toggle them.
- Keep persistent project memory in Beads via `bd remember`; do not create ad hoc memory files.

**Architecture in one line:** issues live in a local Dolt DB; sync uses `refs/dolt/data` on your git remote; `.beads/issues.jsonl` is a passive export. See https://github.com/gastownhall/beads/blob/main/docs/core-concepts/sync-concepts.md for details and anti-patterns.
<!-- END BEADS CODEX SETUP -->
