# Compound AI Starter Kit

Part of Compound AI Operating Standards by Cameron Sutcliff.

Canonical URL:

`https://cameronsutcliff.com/compound-ai`

## What This Is

This starter kit is a portable operating scaffold for AI-assisted and agentic project work.

For human readers, start with the Field Guide in the public repository:

`https://github.com/cameronpsutcliff/compound-ai-operating-standards`

For agents, start with `AGENT.md`, `_map.md`, and `_skills-index.md`.

It helps a project stop resetting every session by giving the AI:

1. A stable operating contract.
2. A current state file.
3. An append-only session log.
4. A map of where context lives.
5. Pointer skills that load deeper references only when needed.
6. Checklists for token, cache, model routing, quality, and lineage decisions.
7. Optional provenance verification.
8. A portable style guide for generated deliverables.

The kit is technique-first by design. Public pages can name the production systems that shaped these standards; the downloadable package should stay portable enough for an agent to use without product-specific background.

## First Use

1. Copy this folder into a project.
2. Fill in `AGENT.md`.
3. Fill in `Project.md`.
4. Update `STATE.md`.
5. Start work with `checklists/session-start.md`.
6. End work with `checklists/session-closeout.md`.

## File Map

| File | Purpose |
|---|---|
| `AGENT.md` | Machine-oriented operating contract |
| `AGENT.annotated.md` | Annotated version explaining each section |
| `Project.md` | Human-oriented project overview |
| `STATE.md` | Current state and next actions |
| `session-log.md` | Append-only history |
| `BACKLOG.md` | Open items and deferred decisions |
| `_map.md` | Navigation and context pointers |
| `_skills-index.md` | Pointer skill registry |
| `context/` | Tiered context files |
| `conventions/` | Token, skill, session-log, provenance, and style conventions |
| `skills/` | Small pointer skills |
| `checklists/` | Operational checklists |
| `code/` | Reference implementations |
| `scripts/` | Verification and setup scripts |

## Design Principle

Do not put everything into `AGENT.md`.

`AGENT.md` should point to context. It should not become the context.

## Before Release

After changing any starter-kit file, rebuild and verify the manifest:

```bash
scripts/build-manifest.py
scripts/verify-integrity.py
```

Run `scripts/verify-origin.py --online` only after the canonical website or GitHub release hosts the manifest and checksum.

## License

Docs and templates are intended for CC BY 4.0. Code examples are intended for Apache 2.0 unless the final release chooses a different split.
