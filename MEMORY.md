# MEMORY.md — Autofiction

Long-term curated memory for the Autofiction project. This file is loaded at the start
of every AI assistant session and should contain only durable, stable information —
preferences, key decisions, project conventions, and important facts.

> **Convention:** Keep this file concise and curated. If it grows noisy, prune aggressively.
> Day-to-day notes belong in `memory/YYYY-MM-DD.md`, not here.

## Project Identity

- **Name:** Autofiction
- **Status:** Active — protocol defined, two stories generated
- **Repository:** charlessanders72/Autofiction

## Key Decisions

<!-- Record significant architectural and project decisions here. -->

- Stories saved to `stories/` with filename format `YYYY-MM-DD-slug.md`
- Each story file includes: metadata (date, prompt source, tense/POV), outline, full story text
- `PROTOCOL.md` lives at repo root and defines the four-step workflow
- Default branch is `Main-Branch` (not `main`)

## User Preferences

<!-- Record stable preferences about coding style, communication, tooling, etc. -->

_No preferences recorded yet._

## Conventions

<!-- Record project-specific conventions that emerge over time. -->

- Memory system follows the OpenClaw two-layer convention (see `CLAUDE.md` for details)
- Durable facts go here; running context goes to `memory/YYYY-MM-DD.md`

## Lessons Learned

<!-- Record insights, pitfalls, and patterns discovered during development. -->

- Remote container can only push to `claude/<name>-<session-id>` branches; merges to Main-Branch require a PR or local merge
- Multiple stories per day work fine by picking different topics under the same Daily Micro Fiction letter
- GitHub Actions workflow exists at `.github/workflows/autofiction.yml` for hourly automated runs; requires `ANTHROPIC_API_KEY` secret and merge to Main-Branch to activate
- **WebFetch is unreliable** — frequently returns 403s, hangs indefinitely, or fails domain verification. Prefer `WebSearch` for research, `curl` via Bash for direct URL fetching, or MCP servers for JS-rendered pages. See `CLAUDE.md` "Tool Usage — WebFetch" section for full details.
