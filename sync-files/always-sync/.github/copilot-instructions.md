# jbcom Organization - AI Agent Instructions

> **This file contains ORGANIZATION-WIDE standards.**
> **Repository-specific instructions should be added below the `## Repository-Specific` section.**

## Organization Context

This repository is part of the **jbcom** ecosystem. All repositories share:

- **GitHub Organization**: [jbcom](https://github.com/jbcom)
- **Control Center**: [jbcom/control-center](https://github.com/jbcom/control-center) - Central configuration and sync
- **Portfolio**: [jbcom.github.io](https://jbcom.github.io) - Showcase and documentation

## Project Management

### Linked Projects (Use These!)

All issues and PRs should be linked to the appropriate organization project:

| Project | Purpose | When to Use |
|---------|---------|-------------|
| **Roadmap** | Feature planning and milestones | New features, enhancements |
| **Backlog** | Prioritized work items | Bug fixes, tech debt |
| **Sprint** | Current iteration work | Active development |

### Issue Workflow

1. Create issue with appropriate labels
2. Link to organization project (Roadmap/Backlog)
3. Assign to milestone if applicable
4. Reference in PR when complete

## Repository Settings

### GitHub Settings App

This organization uses the [Settings GitHub App](https://github.com/apps/settings) for repository configuration:

- **Organization settings**: `jbcom/control-center/.github/settings.yml`
- **Repository settings**: `.github/settings.yml` in each repo

**Repository settings EXTEND organization settings.** Use your local `.github/settings.yml` for:
- Repository-specific labels
- Branch protection overrides
- Team permissions

### Rulesets

Organization-wide rulesets enforce:
- `copilot_code_review` - AI-assisted code review on PRs
- Branch protection on `main`

## Code Quality Standards

### Before Any Change

1. Check existing patterns in the codebase
2. Follow repository's established conventions
3. Run tests before AND after changes

### Commit Messages

```
<type>(<scope>): <description>

Types: feat, fix, docs, style, refactor, test, chore
```

### What NOT To Do

- ❌ Refactor unrelated code
- ❌ Add dependencies without justification
- ❌ Skip tests
- ❌ Make breaking changes without discussion

## Getting Help

1. Check `memory-bank/` for project context
2. Check `docs/` for architecture decisions
3. Look at recent PRs for patterns
4. Ask in the issue for clarification

---

## Repository-Specific

<!-- 
Repository maintainers: Add your project-specific instructions below.
This section will NOT be overwritten by organization sync.

Example additions:
- Project-specific commands
- Architecture decisions
- Local development setup
- Team conventions
-->
