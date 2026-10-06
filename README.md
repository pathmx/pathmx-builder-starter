# PathMX builder starter

A starting point for a PathMX project built with Claude, for members of the
[PathMX Builders Club](https://pathmx.club).

It's a fresh `pmx init` project with three additions:

- `AGENTS.md` (which `CLAUDE.md` loads) tells Claude how to work with you and to
  log PathMX problems as you go.
- `.claude/skills/pathmx-authoring` gives Claude the PathMX authoring skill for
  this release.
- `pathmx-feedback.md` is the log of what was confusing or hard, for check-ins.

## Start

On Windows, follow
[Start a PathMX project on Windows](https://pathmx.club/learn/start-windows.guide):
you install Git and Bun, then Claude copies this starter into your projects folder
and works through the rest with you.

To start by hand, with Bun 1.4 or newer:

```sh
git clone https://github.com/pathmx/pathmx-builder-starter my-project
cd my-project
git remote remove origin
bun install --frozen-lockfile
bun run dev
```

Then open http://localhost:3000. `bun run check` checks your pages.
