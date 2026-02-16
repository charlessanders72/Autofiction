# CLAUDE.md — Autofiction

This file provides context and conventions for AI assistants (and developers) working on the Autofiction project.

## Project Overview

**Autofiction** is a protocol-driven generative fiction project. It uses Claude (via the Anthropic API and Claude Code CLI) to produce short literary stories (500–1,000 words) by pairing [Daily Micro Fiction](https://www.dailymicrofiction.com/p/index) prompts with current news headlines. A 5-step workflow defined in `PROTOCOL.md` governs idea selection, outlining, generation, logging, and recursive self-improvement of the protocol itself. Stories are generated daily — either manually or via GitHub Actions automation.

## Repository Structure

```
Autofiction/
├── .github/
│   └── workflows/
│       └── autofiction.yml    # GitHub Actions: daily automated story generation
├── stories/                   # Generated stories (YYYY-MM-DD-slug.md)
├── memory/
│   ├── TEMPLATE.md            # Template for new daily logs
│   ├── YYYY-MM-DD.md          # Daily session logs (append-only)
│   └── .gitkeep
├── CLAUDE.md                  # AI assistant guide and project conventions (this file)
├── MEMORY.md                  # Curated long-term memory (loaded every session)
└── PROTOCOL.md                # 5-step story generation workflow
```

## Getting Started

### Prerequisites

- **Claude Code CLI** — `npm install -g @anthropic-ai/claude-code`
- **Anthropic API key** — set as `ANTHROPIC_API_KEY` environment variable
- **Git** — for version control and branch management

### Setup

1. Clone the repository and check out `Main-Branch` (the default branch).
2. Set your API key: `export ANTHROPIC_API_KEY=<your-key>`
3. Read `PROTOCOL.md` for the full story generation workflow.

### Running

- **Manual:** Run `claude` in the repo root and ask it to "run autofiction protocol". The protocol in `PROTOCOL.md` guides the session.
- **Automated:** The GitHub Actions workflow (`.github/workflows/autofiction.yml`) runs daily at 8 AM Eastern. It can also be triggered manually via `workflow_dispatch` in the GitHub UI.

## Development Workflow

This is a Markdown-and-protocol project — there is no traditional build step, test suite, or linter. Quality is maintained through the protocol's recursive analysis (Step 5) and manual review via pull requests.

### CI/CD

A GitHub Actions workflow at `.github/workflows/autofiction.yml` automates daily story generation:

- **Schedule:** Daily at 8 AM Eastern (1 PM UTC) via cron
- **Manual trigger:** Available via `workflow_dispatch` in the GitHub UI
- **Process:** Checks out `Main-Branch`, installs Claude Code CLI, runs the protocol, commits the story to an `autofiction/YYYY-MM-DD-HHMM` branch, and opens a PR to `Main-Branch`
- **Important:** The workflow handles all git operations (commit, push, PR creation). Claude is told to skip git commands during CI runs — it only writes files.
- **Secrets required:** `ANTHROPIC_API_KEY` must be configured in the repository settings

## Conventions

### General Principles

- Write small, focused commits with clear messages describing _why_ a change was made.
- Prefer editing existing files over creating new ones when possible.
- Only modify `PROTOCOL.md` through the recursive analysis step (Step 5) — one sentence-level change per story, motivated by a specific observation.

### Story Format

- **Filename:** `YYYY-MM-DD-slug.md` in the `stories/` directory
- **Metadata header:** Date, prompt source, tense/POV, recursive analysis notes
- **Sections:** Metadata, outline (from Step 2), full story text
- **Target length:** 500–1,000 words
- **No em dashes** — use commas, semicolons, or periods instead

### Git Conventions

- **Default branch:** `Main-Branch` (not `main`)
- **Interactive sessions:** Push to `claude/<name>-<session-id>` branches
- **Automated runs:** Push to `autofiction/YYYY-MM-DD-HHMM` branches
- **Merging:** All changes reach `Main-Branch` via pull request
- **Commit messages:** Use imperative mood, concise subject lines (under 72 chars)

## Architecture

The project follows a protocol-driven loop defined in `PROTOCOL.md`:

1. **Pick an Idea** — Select a Daily Micro Fiction topic (letter = day of month) and pair it with a current CNN headline to extract human tension.
2. **Create an Outline** — Develop theme (universal claim about human nature), characters, setting, and a 2–4 scene plot.
3. **Generate the Story** — Send the outline to Claude Opus with a structured prompt emphasizing immersion, fast pacing, show-don't-tell, and abrupt endings.
4. **Log and Commit** — Save to `stories/YYYY-MM-DD-slug.md` with metadata, commit to a feature branch, update the daily memory log.
5. **Recursive Analysis** — Analyze the story for craft strengths/weaknesses and make at most one sentence-level change to `PROTOCOL.md`, creating a self-improving feedback loop.

The system is designed so that each story generation cycle refines the protocol for the next.

## Memory System

This project uses a two-layer memory system inspired by [OpenClaw's memory architecture](https://docs.openclaw.ai/concepts/memory).

### Overview

| Layer | File(s) | Purpose | Lifecycle |
|-------|---------|---------|-----------|
| **Long-term** | `MEMORY.md` | Curated, durable facts — preferences, key decisions, conventions | Persistent; prune to stay concise |
| **Daily logs** | `memory/YYYY-MM-DD.md` | Running session context — tasks, decisions, learnings | Append-only; one file per day |

### Principles

1. **Decisions, preferences, and durable facts** go to `MEMORY.md`.
2. **Day-to-day notes and running context** go to `memory/YYYY-MM-DD.md`.
3. **If someone says "remember this," write it down** — do not rely on context window alone.
4. **`MEMORY.md` should stay curated and concise.** If it gets noisy, move details to daily logs or prune.
5. **Daily logs are append-only.** Do not edit previous days' logs.

### Session Start

At the start of each session, an AI assistant should:

1. Read `MEMORY.md` for long-term context.
2. Read today's daily log (`memory/YYYY-MM-DD.md`) if it exists.
3. Optionally read yesterday's log for recent context.
4. Create today's daily log from `memory/TEMPLATE.md` if it doesn't exist yet.

### Writing to Memory

- **During a session:** Append notes, decisions, and learnings to today's `memory/YYYY-MM-DD.md`.
- **When a fact becomes durable:** Promote it to `MEMORY.md` (e.g., a convention that will persist, a key decision, a user preference).
- **Before session end or context compaction:** Flush any important context to the daily log so it isn't lost.

### Curation

Over time, review daily logs and promote recurring patterns or significant decisions to `MEMORY.md`. Prune `MEMORY.md` entries that are no longer relevant. The goal is for `MEMORY.md` to give any new session a strong "pick up where we left off" foundation without overwhelming the context window.

## Key Files Reference

| File | Purpose |
|------|---------|
| `CLAUDE.md` | AI assistant guide and project conventions (this file) |
| `PROTOCOL.md` | 5-step story generation workflow |
| `MEMORY.md` | Curated long-term memory — preferences, decisions, conventions |
| `memory/TEMPLATE.md` | Template for creating new daily session logs |
| `memory/YYYY-MM-DD.md` | Daily session logs (append-only, one per day) |
| `stories/YYYY-MM-DD-slug.md` | Generated stories with metadata, outlines, and full text |
| `.github/workflows/autofiction.yml` | GitHub Actions daily automation workflow |

## Common Tasks

- **Generate a story manually:** Run `claude` in the repo root and instruct it to "run autofiction protocol". It will follow the 5 steps in `PROTOCOL.md`.
- **Trigger automated generation:** Use the `workflow_dispatch` trigger in GitHub Actions, or wait for the daily 8 AM Eastern cron.
- **Review a story:** Check the latest file in `stories/` — each includes metadata, the outline, and the full text.
- **Update the protocol:** Follow Step 5 (Recursive Analysis) — at most one sentence-level change per story, motivated by a specific craft observation.
- **Check session history:** Read the daily logs in `memory/` for running context, or `MEMORY.md` for durable facts.

## Tool Usage — Web Search

When searching external websites for information (news headlines, research, documentation, etc.), **use `WebSearch` exclusively**. Do not use `curl`, `WebFetch`, MCP servers, or any other method to access external web content.

- **`WebSearch`** is the only supported tool for querying external websites. It queries search engines reliably and avoids the access issues that plague direct-fetch approaches.
- **`WebFetch`** is unreliable (HTTP 403 blocks, indefinite hangs, content truncation) and should **not** be used.
- **`curl` via Bash** is **not permitted** for fetching external web content.
- **MCP servers** (e.g., Puppeteer) are **not permitted** for fetching external web content.

## Notes for AI Assistants

- **Read before editing:** Always read a file before proposing changes to it.
- **Stay focused:** Only make changes that are directly requested. Avoid unrelated refactors or "improvements."
- **Update this file:** When you add significant structure, tooling, or conventions to the project, update CLAUDE.md to reflect those changes so future sessions have accurate context.
- **Check for tests:** If tests exist, run them after making changes and ensure they pass before committing.
- **Security:** Never commit secrets, credentials, or `.env` files. Be cautious with user input handling (validate at system boundaries).
- **Use the memory system:** Read `MEMORY.md` and today's daily log at session start. Write durable facts to `MEMORY.md` and running notes to `memory/YYYY-MM-DD.md`. If asked to remember something, write it down immediately.
- **Curate, don't hoard:** Periodically promote recurring patterns from daily logs into `MEMORY.md`, and prune stale entries. Keep `MEMORY.md` concise enough that it doesn't overwhelm the context window.
