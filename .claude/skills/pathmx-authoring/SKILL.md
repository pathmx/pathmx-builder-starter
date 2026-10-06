---
name: pathmx-authoring
description: Create, improve, and publish educational content and practical guides with PathMX, including lessons, learning Paths, and content for reading, Focus, and Slides. Use for PathMX content projects, not framework maintenance.
---

# PathMX authoring

Help an author turn knowledge into something a learner can understand and use:
a parent’s math lesson, an employee’s workflow guide, or a sequence of activities.
Use the author’s vocabulary in the content; explain PathMX terminology only when
it helps them make a choice.

## Start with the learner and the project

Use the request and supplied material to identify the audience, what they should
be able to do, and their starting knowledge. Ask only for missing information
that changes the result. A short guide may need one Source; a course can use a
Path linking several activities. Do not turn every content request into a new app,
account system, or custom Plugin.

In an existing project, read its instructions, inspect existing changes, and
identify the installed PathMX version and scripts. Reuse nearby content, layouts,
and components. For a new project, follow the Quickstart below; initialize into
an empty or absent directory. Do not upgrade an existing project as a side effect.

Read the task's owning reference and a working example before using unfamiliar
syntax. The [agent entry point](https://docs.pathmx.dev/docs/agents)
and [documentation index](https://docs.pathmx.dev/llms.txt) route to more topics.
Fetch individual Markdown pages and resolve their relative links against their
URLs. Installed command help and types resolve release mismatches; old consumer
workarounds are not current contracts. Use rendered HTML URLs with web-browsing
tools. If the reader fails or rejects Markdown and shell access is available,
fetch directly with `curl --fail --location --max-time 10 -H 'Accept: text/markdown' URL`.
Retain the retrieved URL and distinguish tool failure from HTTP failure.

## Author with PathMX's primitives

- **Sources:** use meaningful filenames such as `fractions.lesson.md` or
  `expense-report.guide.md`. Authored links target exact relative Markdown files.
  The rendered route retains the type: `/fractions.lesson`; an untyped `about.md`
  renders at `/about.page`. A URL ending in `.md` requests Markdown.
- **Blocks:** `---` separates learning moments; headings alone do not. Keep an
  explanation and its example together, and give a new activity its own Block
  when that improves the sequence. Keep the instructions and expected result
  together. Split by meaning, not a fixed length or every paragraph.
- **Identity:** keep linked, included, or response Block IDs stable. Place Block
  metadata in a leading HTML comment, before link definitions. Keep Source-wide
  layout/import/Origin definitions in an introductory Block that save Actions
  do not replace; definitions at the end belong to the last Block's body.
- **Reuse and relations:** link for a reference, include a Block for shared
  content, and use a component for repeated presentation. Arbitrary frontmatter
  path strings are not graph relations and are not maintained by Source moves.
  Keep custom domain data away from reserved props such as `location`.
- **Paths:** use the Path package's ordered links and stable step IDs for a
  journey across Sources or Blocks. Player's Beats are attention steps within a
  Source. Moving to the next Beat, visiting a page, and completing an activity
  are different actions; use Completion's declared requirements for progress.

Choose examples, practice, and feedback that help the intended learner reach the
outcome. For math, check the worked answer and practice solutions. For a workflow,
keep each action with the expected result and a useful recovery step where needed.
Use supplied internal material as the authority for an internal system; identify
missing facts instead of inventing screens, policies, or behavior.

## Make it playable and interactive where useful

For lessons and focused guides, consider Player part of the useful experience
while respecting a request for reading only. Author reading, Focus, and Slides
from the same Sources. Check Player activation, one `<x-player-app />` per rendered
page (often in the shared layout), and a discoverable Play entry. Do not create a
separate slide copy or leave an entire long lesson in one Block.

Installing a dependency does not prove its Plugin is active. Inspect
`bun run pmx plugins list` when a feature matters and use the package's documented
activation workflow. Some packages need explicit configuration. Check the running
page as well as the manifest before inventing a replacement for a missing control.

Prefer existing controls and components. Before creating a literate component,
read Components: its leading `componentName` declaration and import are required;
implementation `html` fences and illustrative `md` fences have different meanings.
Use the layout/style references for presentation rather than relying on internal
framework DOM selectors or post-render HTML rewriting.

When collecting answers or tracking progress, read Input, Completion, and Personal
state before adding controls. Choose shared versus personal work deliberately.
Submission needs the supported Actor, writable Home/storage, and access setup;
typing or recovering a browser draft is not a committed response. Keep response
Block IDs and field names stable. Use existing state mechanisms before building
custom persistence, and verify save/reload as the intended learner.

## Read only the references needed

| Task | Owning documentation |
| --- | --- |
| Start a project | [Quickstart](https://docs.pathmx.dev/docs/start/first-site.guide.md), [Project structure](https://docs.pathmx.dev/docs/start/project-structure.guide.md) |
| Shape content and identity | [Sources](https://docs.pathmx.dev/docs/authoring/sources.reference.md), [Blocks](https://docs.pathmx.dev/docs/authoring/blocks.reference.md), [Links](https://docs.pathmx.dev/docs/authoring/links.reference.md) |
| Build a learning sequence | [Paths](https://docs.pathmx.dev/docs/learning/path.reference.md), [Player](https://docs.pathmx.dev/docs/learning/player.reference.md) |
| Collect responses or show progress | [Input](https://docs.pathmx.dev/docs/authoring/input.reference.md), [Completion](https://docs.pathmx.dev/docs/learning/completion.reference.md), [Personal state](https://docs.pathmx.dev/docs/extend/state.reference.md), [Auth](https://docs.pathmx.dev/docs/accounts/auth.reference.md) |
| Reuse or present content | [Reuse](https://docs.pathmx.dev/docs/authoring/reuse-content.guide.md), [Components](https://docs.pathmx.dev/docs/authoring/components.reference.md), [Layouts](https://docs.pathmx.dev/docs/site/layouts.reference.md), [Themes](https://docs.pathmx.dev/docs/site/themes.reference.md), [Stylesheets](https://docs.pathmx.dev/docs/site/styles.reference.md) |
| Inspect or reorganize a project | [CLI](https://docs.pathmx.dev/docs/cli.reference.md), [Packages](https://docs.pathmx.dev/docs/packages.reference.md) |
| Publish or share | [How PathMX runs](https://docs.pathmx.dev/docs/start/runs.guide.md), [Publish](https://docs.pathmx.dev/docs/start/publish.guide.md), [Source access](https://docs.pathmx.dev/docs/extend/core.reference.md#choose-the-source-access-policy) |

## Verify and publish

Use the installed project-local CLI (`bun run pmx` in scaffolded projects).
Use `--help`, `tree`, or `query` only when discovery is needed. After a coherent
authoring change, run `bun run check` and use `bun run pmx lint --format json`
when structured diagnostics help. Use the project's TypeScript check if Plugin
code changes. Use the CLI's `mv`/`rm` previews before reorganizing Sources; their
paths are relative to the Source root. Review affected links and the resulting diff.

Lint is not proof of a working learning experience. Open representative rendered
routes, follow links, and check narrow-screen reading and keyboard use. For Player,
try Focus, Slides, Beat/Block navigation, and exit to reading. For saved work,
submit, reload, and check the intended user's progress and access. During live
updates, confirm unrelated controls and focus remain intact. Reuse passing checks;
measure before/after only for changes likely to affect loading or rendering costs.

For publishing, establish the intended audience and destination from the request
or existing project. Public reading and browser interactions can use static export;
accounts, private content, or work saved to a shared host need a suitable live
host. A supported browser publication can save personal Sources on one device;
ordinary static export does not supply that host or synchronize learner work.
Do not make an internal guide or learner responses public as a hosting shortcut.

Follow the chosen host's current publishing instructions. For static delivery,
review export diagnostics and preview the exported output over HTTP, including a
deep route and Player if used. Reuse the user's existing publishing authorization;
if the destination or audience is unresolved, finish the preview and ask for that
specific choice before uploading. Report authored files, preview/published URL,
checks performed, and any remaining limitation without claiming unverified delivery.
