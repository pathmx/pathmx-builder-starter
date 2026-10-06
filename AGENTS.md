# PathMX project

Use the installed project CLI: `bun run pmx <command>`.
`bun run dev` previews the site; `bun run check` checks authored content.
Run `bun run typecheck` when changing TypeScript.
Use `bun run pmx --help` and command-specific `--help` to discover the installed
release's commands. Use `tree`, `query`, and `plugins list` when inspecting Sources
or Plugin configuration. Run `bun run check` after each coherent authoring change;
use `bun run pmx lint --format json` when collecting diagnostics for a report.
Fix introduced diagnostics and report any pre-existing failures that remain.
For custom Plugins or changes likely to affect loading or compile/render cost,
capture comparable before/after performance evidence using the project's available
measurement tools. Use installed CLI performance diagnostics when available; check
`--help` before assuming a command exists. Record the command, scope, and results.

For PathMX authoring, use the `pathmx-authoring` skill if available.
Otherwise start at https://docs.pathmx.dev/docs/agents/index.md and read only the
references relevant to the task. Use guidance matching the installed release.

Keep project-specific instructions here. Package dependencies and Plugin
activation belong in `package.json`; custom behavior belongs in repository Plugins.

Verify changed content in its rendered route. For playable content, check
reading, Focus, and Slides using the same authored Source.

## PathMX Builders Club

This project belongs to a student builder in the PathMX Builders Club. At the start
of a session, read https://pathmx.club/learn/agents.guide.md and follow it. The
essentials:

- The builder owns this project, their accounts and their computer. They type their
  own passwords and approve sign-ins; never ask for a password, token or code in
  chat.
- Ask before installing anything outside this project, publishing, making a
  repository public, or upgrading PathMX.
- Log every PathMX problem, confusion or guess in `pathmx-feedback.md` as it
  happens, including your own. Finding these is part of the point of the project.
- If `paths/index.md` still says "Welcome to PathMX", this is a fresh copy of the
  starter: follow the "For Claude" steps at
  https://pathmx.club/learn/start.guide.md with the builder.

`.claude/skills/pathmx-authoring` is copied from the installed `@pathmx/core`.
After upgrading PathMX, copy `node_modules/@pathmx/core/skills/pathmx-authoring`
over it so the skill matches the release.
