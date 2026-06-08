# homebrew-tap

Homebrew tap for [jophira](https://github.com/jophira) formulae and casks.

## Usage

```bash
brew tap jophira/tap
```

Then install any formula or cask:

```bash
brew install jophira/tap/<formula>
```

## Contents

| Name | Type | Description |
|------|------|-------------|
| `weft` | Formula | Composable AI rules manager — manage, layer, and sync AI rule sources across teams and tools |

---

## weft

**weft** manages AI coding tool rules across multiple sources and harnesses. Maintain separate rule repositories (personal, team, company) and compose them into a single layered profile applied to whichever AI coding tool you are using.

### Install

```bash
brew install jophira/tap/weft
```

### What it does

- **Merges sources** — overlay personal rules on top of team rules; later sources win on conflict
- **Normalises harnesses** — one source tree writes `CLAUDE.md` for Claude Code, `AGENTS.md` for Codex, `.mdc` for Cursor, `global_rules.md` for Windsurf, and more
- **Watches for changes** — `weft profile use` applies and re-applies whenever source files change
- **Per-project rules** — any directory named `projects` or `project-rules` in your source is auto-discovered; all `.md` files inside are injected into the assembled `CLAUDE.md` grouped by project, so the AI loads the right rules for the active project
- **Write-back** — edits you make in `~/.claude/CLAUDE.md` are propagated back to the owning source repo on next startup
- **MCP server** — `weft mcp serve` exposes the full API to any MCP-aware agent

### Quick start

```bash
# Register your rules repo
weft source add personal ~/.rules/personal

# Combine sources into a named profile
weft profile create main --sources personal

# Activate — merges, applies to all harnesses, watches for changes
weft profile use main
```

### Per-project rules

Place `<!-- weft:projects -->` in your source `CLAUDE.md` and organise rule files under any directory named `projects` or `project-rules`:

```
php/project-rules/ubs-keyinvest/ubs-keyinvest.md
java/project-rules/instrument-service/instrument-service.md
```

Weft discovers these automatically and injects a grouped reference block into your assembled `CLAUDE.md` on every apply. See the [weft README](https://github.com/jophira/weft#per-project-rules) for full details.

### Source: [github.com/jophira/weft](https://github.com/jophira/weft)
