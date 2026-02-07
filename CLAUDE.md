# CLAUDE.md — Autofiction

This file provides context and conventions for AI assistants (and developers) working on the Autofiction project.

## Project Overview

**Autofiction** is a newly initialized repository. This document should be updated as the project takes shape — adding architecture details, build instructions, testing workflows, and coding conventions as they are established.

## Repository Structure

```
Autofiction/
├── CLAUDE.md          # This file — AI assistant guide and project conventions
└── (empty)            # Project files to be added
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

## Key Files Reference

| File | Purpose |
|------|---------|
| `CLAUDE.md` | AI assistant guide and project conventions (this file) |

> **Update this table** as important files are added to the project.

## Common Tasks

_To be defined._ Add frequently performed tasks and their commands here, such as:

- How to add a new feature
- How to run a specific subset of tests
- How to deploy
- How to debug common issues

## Notes for AI Assistants

- **Read before editing:** Always read a file before proposing changes to it.
- **Stay focused:** Only make changes that are directly requested. Avoid unrelated refactors or "improvements."
- **Update this file:** When you add significant structure, tooling, or conventions to the project, update CLAUDE.md to reflect those changes so future sessions have accurate context.
- **Check for tests:** If tests exist, run them after making changes and ensure they pass before committing.
- **Security:** Never commit secrets, credentials, or `.env` files. Be cautious with user input handling (validate at system boundaries).
