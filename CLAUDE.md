# CLAUDE.md — Autofiction

This file provides context and conventions for AI assistants (and developers) working on the Autofiction project.

## Project Overview

**Autofiction** is a newly initialized repository. This document should be updated as the project takes shape — adding architecture details, build instructions, testing workflows, and coding conventions as they are established.

## Repository Structure

```
Autofiction/
├── CLAUDE.md              # AI assistant guide and project conventions (this file)
├── MEMORY.md              # Curated long-term memory (loaded every session)
├── memory/
│   ├── TEMPLATE.md        # Template for new daily logs
│   ├── YYYY-MM-DD.md      # Daily session logs (append-only)
│   └── .gitkeep
└── (source code TBD)
```

> **Update this section** as directories and files are added (e.g., `src/`, `tests/`, `docs/`, config files).

## Getting Started

### Prerequisites

_To be defined._ Document required runtimes, tools, and system dependencies here as the project is set up.

### Setup

_To be defined._ Add installation and setup steps (e.g., `npm install`, `pip install -r requirements.txt`, `cargo build`).

### Running

_To be defined._ Add commands to run the application locally.

## Development Workflow

### Build

_To be defined._ Document build commands and build system details here.

### Testing

_To be defined._ Document testing framework, test commands, and how to run individual tests.

### Linting and Formatting

_To be defined._ Document linter/formatter configuration and commands.

### CI/CD

_To be defined._ Document continuous integration and deployment pipelines.

## Coding Conventions

### General Principles

- Keep code simple and readable; avoid premature abstraction.
- Write small, focused commits with clear messages describing _why_ a change was made.
- Prefer editing existing files over creating new ones when possible.
- Delete unused code rather than commenting it out.

### Style Guidelines

_To be defined._ Add language-specific style guides, naming conventions, and formatting rules as the project adopts them.

### Git Conventions

- **Branch naming:** Use descriptive branch names (e.g., `feature/add-auth`, `fix/login-redirect`).
- **Commit messages:** Use imperative mood, concise subject lines (under 72 chars), and a body explaining the "why" when needed.
- **Pull requests:** Include a summary of changes and a test plan.

## Architecture

_To be defined._ Document the high-level architecture, key modules, data flow, and design decisions here as the project develops.

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
| `MEMORY.md` | Curated long-term memory — preferences, decisions, conventions |
| `memory/TEMPLATE.md` | Template for creating new daily session logs |
| `memory/YYYY-MM-DD.md` | Daily session logs (append-only, one per day) |

> **Update this table** as important files are added to the project.

## Common Tasks

_To be defined._ Add frequently performed tasks and their commands here, such as:

- How to add a new feature
- How to run a specific subset of tests
- How to deploy
- How to debug common issues

## Tool Usage — WebFetch

The `WebFetch` tool is **unreliable** and should be treated as a last resort for fetching web content. Known issues:

- **HTTP 403 blocks:** Many sites (Wikipedia, npm, docs sites) reject WebFetch requests based on its User-Agent/fingerprint, even when `curl` works fine.
- **Hangs with no timeout:** WebFetch can freeze in a "Fetching..." state indefinitely, locking the session with no way to interrupt. Recovery requires killing and restarting Claude Code.
- **Domain verification failures:** The preflight safety check fails in restricted networks, corporate proxies, or environments with TLS inspection (Cloudflare WARP, VPNs).
- **Content truncation:** Results are capped at ~100KB of text; large pages lose information silently.

**Prefer these alternatives instead:**

| Need | Use | Why |
|------|-----|-----|
| General research / docs lookup | `WebSearch` | Queries search engines; avoids direct-access blocks |
| Controlled URL fetching | `curl` via Bash | Full control over headers, User-Agent, retries |
| Rich / JS-rendered pages | MCP server (e.g., Puppeteer) | Handles dynamic content and bypasses simple blocks |

Only fall back to `WebFetch` when the alternatives above are unavailable or when fetching a known-reliable URL.

## Notes for AI Assistants

- **Read before editing:** Always read a file before proposing changes to it.
- **Stay focused:** Only make changes that are directly requested. Avoid unrelated refactors or "improvements."
- **Update this file:** When you add significant structure, tooling, or conventions to the project, update CLAUDE.md to reflect those changes so future sessions have accurate context.
- **Check for tests:** If tests exist, run them after making changes and ensure they pass before committing.
- **Security:** Never commit secrets, credentials, or `.env` files. Be cautious with user input handling (validate at system boundaries).
- **Use the memory system:** Read `MEMORY.md` and today's daily log at session start. Write durable facts to `MEMORY.md` and running notes to `memory/YYYY-MM-DD.md`. If asked to remember something, write it down immediately.
- **Curate, don't hoard:** Periodically promote recurring patterns from daily logs into `MEMORY.md`, and prune stale entries. Keep `MEMORY.md` concise enough that it doesn't overwhelm the context window.
