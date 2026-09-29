# Getting started

This project is intentionally incremental. Start with the smallest useful setup and add automation only when you can still explain what each part does.

## Baseline

A practical starting point:

- Windows 11
- PowerShell 7
- Git
- GitHub CLI
- Node.js or your language runtime
- one GitHub repository
- one AI coding assistant
- one CI workflow

A self-hosted runner is optional at the beginning.

## Stage 1 — Local discipline

Create a repeatable local loop:

```text
edit → format → lint → test → commit
```

Write the commands down before automating them.

## Stage 2 — GitHub as the shared record

Use issues or a small task document to record:

- goal
- scope
- constraints
- acceptance criteria
- evidence required

Use pull requests even when working alone if the change benefits from a review boundary.

## Stage 3 — Add CI

Move deterministic checks into GitHub Actions:

- formatting
- lint
- unit tests
- build
- static analysis

Keep credentials out of workflow files.

## Stage 4 — Add AI roles

Useful roles include:

- planner
- implementer
- reviewer
- investigator
- documentation editor

The roles may be separate tools or simply separate review passes. The important part is the **separation of concerns**, not the number of agents.

## Stage 5 — Add a self-hosted runner when needed

Use one when you need:

- Windows-specific behavior
- local hardware
- local services
- faster repeated builds
- tooling unavailable on hosted runners

Do not make production access the default capability of a development runner.

## Next

Read [Architecture](./architecture.md).
