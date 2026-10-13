---
name: using-facets
description: Load BEFORE any facet operation — creating, editing, building,
  publishing, adding, updating, or removing a facet, or answering how facets
  work. Checks for the facet CLI and routes the work through 'facet
  instructions'; if the CLI is missing, offers to install it.
---
# Using Facets

Facets are portable bundles of skills, agents, and commands for AI coding tools.
They are managed exclusively by the `facet` CLI. Whenever you are about to
**create, edit, build, publish, add, update, or remove** a facet — or answer a
question about how facets work — do NOT improvise. Route the work through the
CLI, which ships its own agent-facing instructions.

## Step 1 — Check for the CLI

Run:

```sh
facet --version
```

- **Exit code 0 (a version prints)** → the CLI is installed. Go to Step 2.
- **Command not found / non-zero exit** → the CLI is not installed. Go to
  "CLI not installed" below.

## Step 2 — Read the CLI's own instructions, then act

The CLI is the source of truth for its own workflow — never hand-write
`facet.json`, `facets.json`, or `facets.lock` from memory. Get current guidance
straight from the tool:

```sh
facet instructions
```

That prints an overview and a topic index. Then read the topic that matches the
task **before** running any mutating command:

- **Authoring** a facet (writing/changing its `facet.json` and its
  skill/agent/command files):
  ```sh
  facet instructions authoring
  ```
- **Using** facets in a project (adding, updating, removing facets; installing
  adapter tooling):
  ```sh
  facet instructions usage
  ```
- **Manifest** structure and JSON Schema for `facet.json`:
  ```sh
  facet instructions manifest
  ```

Follow the printed instructions. Prefer `--json` on `facet create`,
`facet modify`, and `facet build` when you need to parse results, and always
finish authoring changes with `facet build --verify`.

## CLI not installed

Do NOT attempt to reproduce facet behavior by hand-editing files. Ask the user
whether they want to install the CLI, using the `question` tool with a clear
binary choice:

- **Install the facet CLI** — you run the installer, then continue.
- **Don't install** — stop and explain that facet work can't proceed without it.

If the user chooses to install, run:

```sh
curl -fsSL https://agentfacets.io/install | bash
```

Then re-run `facet --version` to confirm, and continue from Step 2. If the user
declines, stop the facet task and tell them nothing was changed.
