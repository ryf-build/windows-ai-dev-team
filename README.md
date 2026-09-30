# Windows AI Dev Team

**Turn one Windows PC into an AI-assisted development team.**

A practical public companion for building a disciplined AI-assisted engineering environment on Windows: GitHub, self-hosted runners, automation, QA, and human-controlled execution.

> This repository is intentionally generic. It contains no private product source code, customer data, production credentials, internal endpoints, real infrastructure identifiers, or proprietary deployment configuration.

## What this explores

- Structuring one Windows machine as a small engineering system
- GitHub-based planning and delivery
- Self-hosted runner patterns
- AI-assisted implementation and review
- QA and independent verification
- Safe automation and explicit human authority
- Repeatable PowerShell and CI workflows
- Recovery, observability, and operational discipline

## Model

```text
Human intent
    ↓
Planning
    ↓
AI-assisted implementation
    ↓
Automated checks
    ↓
Independent verification
    ↓
Human authority
    ↓
Merge / release
```

## Public guides

### [Architecture](docs/architecture.md)
A simple public model for organizing one Windows PC as an AI-assisted engineering environment.

### [Getting Started](docs/getting-started.md)
A generic starting path for a safe local setup.

### [Self-Hosted Runner Governance](docs/runner-governance.md)
How to classify jobs, control admission, avoid duplicate work, protect verification, and handle runner-offline states without exposing real infrastructure.

### [Fast Check Workflow Example](examples/github-actions/self-hosted-fast-check.yml)
A fictional GitHub Actions example using documentation-only runner labels.

## Writing

This repository is the public technical companion for:

**「1台のWindows PCをAI開発チームにする」**

## Principles

```text
Start small.
Automate repetition.
Verify consequential changes.
Keep credentials out of examples.
Keep human authority explicit.
```

---

Built by [ryf-build](https://github.com/ryf-build).
