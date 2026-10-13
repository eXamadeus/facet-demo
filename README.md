# Demo for Agent Facets

This is a demo repo for the agent facets CLI tool: `facet`

## Git hooks

Hooks in `.githooks/` run `facet install` automatically whenever `facets.json`
or `facets.lock` changes as the result of a `git pull`, `merge`, `rebase`, or
branch checkout. `core.hooksPath` is local config, so each clone needs it set
once:

```sh
git config core.hooksPath .githooks
```
