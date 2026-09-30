# Self-Hosted Runner Governance

A generic public guide for operating self-hosted GitHub Actions runners without turning one Windows PC into an uncontrolled job queue.

This document is clean-room material. All names and examples are fictional.

## The problem

A self-hosted runner is easy to install.

The harder problem is deciding:

- which jobs may run on it
- which jobs should have priority
- how to avoid duplicate work
- how to protect expensive verification
- how to recover when the machine is offline
- how to keep secrets out of logs and examples

## Reference model

```text
GitHub event
   ↓
job classification
   ↓
admission decision
   ↓
runner selection
   ↓
execution
   ↓
result collection
   ↓
human / repository decision
```

The runner executes work. It should not invent product or release authority.

## Separate lanes by purpose

A simple model can use three logical classes:

| Lane | Typical work | Goal |
| --- | --- | --- |
| fast | lint, unit tests, metadata checks | short feedback loop |
| heavy | builds, integration suites | expensive qualification |
| verify | independent or protected checks | evidence integrity |

These are logical categories. They do not require three physical computers.

## Admission before execution

Before consuming a scarce self-hosted runner, check whether the job is still useful.

Examples:

1. Is the target commit still current for this job?
2. Is an equivalent run already active or complete?
3. Has this candidate been superseded?
4. Is a higher-priority verification job waiting?
5. Does this job require a capability that this runner actually has?

A queue is not a product dependency. It is a resource-scheduling problem.

## Duplicate suppression

A common waste pattern is running equivalent checks more than once for the same immutable target.

A generic deduplication key can be:

```text
repository
+ workflow
+ target commit
+ test profile
```

If the key already has valid evidence, a new run may be unnecessary.

Do not deduplicate across materially different targets or environments.

## Protect important verification

If a long-running verification job is evidence for a consequential change, avoid cancelling it merely to make room for optional work.

Prefer:

1. reserve capacity
2. defer optional jobs
3. use a separate logical lane
4. add another runner only when the workload justifies it

## Offline behavior

When a runner disappears:

```text
RUNNER OFFLINE
   ↓
do not pretend work executed
   ↓
keep job state explicit
   ↓
restore runner or reroute only if policy permits
```

Do not silently downgrade a required self-hosted check into a weaker check just to get a green status.

## Windows host hygiene

For a public lab machine:

- use a dedicated runner directory
- keep repository credentials outside example files
- restrict what workflows may target the runner
- patch the OS and runner software
- avoid interactive user sessions during critical jobs when possible
- log enough to diagnose failures, but never print secrets
- prefer reproducible setup scripts over undocumented manual steps

## Example fictional labels

```text
self-hosted
windows
x64
lab-fast
```

Names such as `lab-fast` are examples only. Do not copy real infrastructure identifiers into public repositories.

## Operating principle

```text
Runner availability != permission to run everything
Green workflow != permission to release
Automation != authority
```

The goal is not maximum runner utilization. The goal is fast, reproducible evidence with controlled execution.
