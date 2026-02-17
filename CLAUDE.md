# Fork Maintenance

This is a fork of [badlogic/pi-mono](https://github.com/badlogic/pi-mono).

## Syncing with upstream

```bash
# Fetch latest from upstream
jj git fetch --remote upstream

# Rebase your changes on top of upstream/main
jj rebase -b <your-change> -d main@upstream

# Resolve any conflicts, then push to your fork
jj git push --remote origin
```

If `models.generated.ts` conflicts (common — it's auto-generated):

```bash
# Accept upstream's version, then regenerate
jj restore --from main@upstream -- packages/ai/src/models.generated.ts
cd packages/ai && npm run generate-models
```

## Building the coding agent

```bash
# Build only the coding agent and its dependencies (tui -> ai -> agent -> coding-agent)
npm run build:agent
```

The `pi` binary is globally linked via npm, so rebuilding is enough — no reinstall needed.

## Remotes

| Name | URL | Purpose |
|------|-----|---------|
| `origin` | `git@github.com:denolehov/pi-mono.git` | Your fork |
| `upstream` | `git@github.com:badlogic/pi-mono.git` | Original repo |
