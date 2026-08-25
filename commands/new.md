---
description: Plan and scaffold a new Fluxlay wallpaper project from an idea
argument-hint: "[describe the wallpaper you want to build]"
---

Plan and scaffold a new Fluxlay wallpaper from a free-form description, then start implementing it.

Read and follow `${CLAUDE_PLUGIN_ROOT}/skills/fluxlay-wallpaper/references/scaffold.md` end to end. It is the
single source of truth for this flow (discovery → scaffold → implement); `${CLAUDE_PLUGIN_ROOT}/skills/fluxlay-wallpaper/SKILL.md`
is the reference for the manifest schema, SDK, and CSP constraints. Template paths written as `../templates/...`
in that file resolve to `${CLAUDE_PLUGIN_ROOT}/skills/fluxlay-wallpaper/templates/...`.

The wallpaper description is `$ARGUMENTS`. If it is empty, ask the user what they want to build before doing
anything else. Do not assume.
