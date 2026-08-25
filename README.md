# Fluxlay Agent Skills

[![skills.sh](https://skills.sh/b/fluxlay/skills)](https://skills.sh/fluxlay/skills)

Agent skills and a Claude Code plugin for building [Fluxlay](https://fluxlay.com) wallpapers — scaffold a project
from an idea, then let your coding agent write the wallpaper with full knowledge of the SDK and runtime constraints.

## Install

### Any agent — `npx skills`

Works with Claude Code, Codex, Cursor, OpenCode, Gemini CLI, Copilot, and [70+ other agents](https://github.com/vercel-labs/skills#supported-agents).

```sh
npx skills add fluxlay/skills            # this project only
npx skills add fluxlay/skills -g         # every project
```

### Claude Code — full plugin

The plugin adds a slash command and guardrail hooks on top of the skill.

```text
/plugin marketplace add fluxlay/skills
/plugin install fluxlay@fluxlay
```

Pick this one if you're on Claude Code; pick `npx skills` for everything else.

## What's included

| | `npx skills` | Claude Code plugin |
|---|---|---|
| **Skill: `fluxlay-wallpaper`** — `@fluxlay/react` SDK hooks, `fluxlay.yaml` manifest schema, runtime CSP constraints, `@fluxlay/cli` workflow, and common pitfalls. Pulled in automatically when you work on a wallpaper. | ✅ | ✅ |
| **Scaffolding flow** — discovery (kind / naming / permissions / network) → copy template → implement. Bundled as `references/scaffold.md` + `templates/`. | ✅ (ask "create a new Fluxlay wallpaper") | ✅ (`/fluxlay:new`) |
| **`PostToolUse` hook** — shallow-validates `fluxlay.yaml` on every edit (slug format, `kind` enum, media `source` extension) and surfaces errors back so the agent fixes them in the same turn. | — | ✅ |
| **`PreToolUse` hook** — pre-flight check before `fluxlay publish` (manifest, build freshness, `fluxlay whoami`). Hard failures deny the action; otherwise you get a confirmation prompt. | — | ✅ |

For `dev` / `build` / `publish` just ask in natural language ("start the dev server", "build and check it",
"publish it") — the skill knows the right `@fluxlay/cli` commands and the pre-flight checks to run.

## Requirements

- [Fluxlay desktop app](https://fluxlay.com/download) — for previewing wallpapers
- Node.js 20+ (any package manager: npm / pnpm / yarn / bun)
- A `fluxlay login` session (only needed when publishing)

## Usage

```text
/fluxlay:new                       # Claude Code
```

On other agents, just say what you want:

> Create a new Fluxlay wallpaper: a breathing circle whose color tracks CPU usage.

Then keep going in natural language:

> Add a CPU-usage bar that pulses in red when load goes above 80%.

> Make the background react to system audio with a frequency-spectrum visualizer.

## Repository layout

```text
skills/fluxlay-wallpaper/
  SKILL.md                 # the skill — SDK, manifest, CSP, CLI, pitfalls
  references/scaffold.md   # new-project flow (agent-agnostic)
  templates/web-react/     # kind: web starter (Vite + React)
  templates/media/         # kind: video / image starter
commands/new.md            # /fluxlay:new — thin wrapper over references/scaffold.md
hooks/                     # Claude Code guardrail hooks
.claude-plugin/            # Claude Code plugin + marketplace manifests
```

`skills/` is the single source of truth. The Claude Code plugin layers hooks and a slash command on top of it —
it does not fork the content.

## License

MIT
