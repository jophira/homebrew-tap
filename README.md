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
| `weft` | Cask | Composable AI rules manager for coding agents and harnesses |

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
- **Per-project rules**: rule files carry `detect:` front-matter, and the session hook loads only the ones that match the repo you are in
- **Write-back** — edits you make in `~/.claude/CLAUDE.md` are propagated back to the owning source repo on next startup
- **MCP server** — `weft mcp serve` exposes the full API to any MCP-aware agent

### Quick start

```bash
# Register your rules repo
weft source add personal ~/weft/sources/personal

# Combine sources into a named profile
weft profile create main --sources personal

# Activate — merges, applies to all harnesses, watches for changes
weft profile use main
```

### Per-project rules

Give each rule file `label:`/`detect:` front-matter and weft loads it only in the projects it matches, via `weft rules resolve` from a session hook. `weft doctor` suggests the front-matter for each file. The older `<!-- weft:projects -->` marker still works but is deprecated. See the [weft README](https://github.com/jophira/weft#per-project-rules).

### Source: [github.com/jophira/weft](https://github.com/jophira/weft)

---

## License

MIT. See [LICENSE](LICENSE).
