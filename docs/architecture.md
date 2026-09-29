# Architecture

The goal is not to make one PC behave like a data center. The goal is to make a single development machine behave like a **small, observable engineering system**.

## Roles

```text
Human
  ├─ defines intent
  ├─ owns consequential decisions
  └─ approves risky transitions

AI agents
  ├─ plan
  ├─ implement
  ├─ review
  ├─ investigate
  └─ summarize evidence

GitHub
  ├─ source control
  ├─ issues / pull requests
  ├─ CI orchestration
  └─ durable engineering record

Windows host
  ├─ development workspace
  ├─ self-hosted runners
  ├─ PowerShell automation
  └─ local observability
```

## Design rules

1. **Separate implementation from approval.**
   An agent that writes a change should not silently manufacture the authority to ship it.

2. **Keep automation observable.**
   Important work should leave logs, commits, checks, or other evidence that can be reviewed later.

3. **Prefer small failure domains.**
   Split fast checks, heavy checks, and risky operations instead of placing everything behind one giant workflow.

4. **Treat credentials as infrastructure.**
   Do not place secrets in prompts, examples, source files, screenshots, or generated documentation.

5. **Make recovery a first-class path.**
   Know how to stop a runner, revert a change, restore a known-good state, and inspect what happened.

## A simple delivery loop

```text
Issue
  ↓
Plan
  ↓
Implementation branch
  ↓
Automated checks
  ↓
Review
  ↓
Risk-based verification
  ↓
Human approval
  ↓
Merge
```

This repository documents the pattern using generic examples only.
