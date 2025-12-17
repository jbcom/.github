# Active Context - jbcom Organization

## Current Status: MIGRATED TO .github

All organization configuration now lives in `jbcom/.github`.

---

## Architecture

```
jbcom/.github/
├── settings.yml           # Org-wide repo settings (Settings app)
├── repos.json             # List of managed repositories
├── memory-bank/           # Agent context and handoff docs
├── sync-files/            # Files synced to all repos
│   ├── always-sync/       # Always overwrite on sync
│   ├── initial-only/      # Create once, don't overwrite
│   ├── python/            # Python-specific files
│   ├── nodejs/            # Node.js/TypeScript files
│   ├── go/                # Go-specific files
│   └── terraform/         # Terraform-specific files
└── .github/workflows/     # Org-level workflows
    └── sync-files.yml     # File sync via PRs
```

## Managed Repositories (21)

| Ecosystem | Repos |
|-----------|-------|
| Python | python-agentic-crew, python-vendor-connectors, python-extended-data-types, python-directed-inputs-class, python-lifecyclelogging, python-terraform-bridge, python-rivers-of-reckoning, python-ai-game-dev |
| Node.js | nodejs-agentic-control, nodejs-agentic-triage, nodejs-strata, nodejs-otter-river-rush, nodejs-otterfall, nodejs-rivermarsh, nodejs-pixels-pygame-palace, jbcom.github.io |
| Go | go-port-api, go-vault-secret-sync, go-secretsync |
| Terraform | terraform-github-markdown, terraform-repository-automation |

## How It Works

### Settings App
- Installed on jbcom org
- Reads `settings.yml` from `.github` repo
- Applies settings to all repos automatically

### File Sync
- Workflow in `.github/workflows/sync-files.yml`
- Creates PRs (not direct pushes) for transparency
- Respects always-sync vs initial-only semantics
- Language-specific files based on repo prefix

## For AI Agents

1. **Start of session**: Read this file + `progress.md`
2. **Making changes**: Edit files in `sync-files/` directory
3. **End of session**: Update memory-bank files, commit

## Migration History

- **2025-12-16**: Migrated from jbcom/control-center
- Settings app deployed to 21 repos
- File sync workflow created
- control-center archived
