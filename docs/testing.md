# Development

This guide covers the local engineering setup, day-to-day workflows, and practical habits that keep teams productive.

## Local setup

Every team member should be able to:

- install dependencies reproducibly
- run the app locally
- run tests relevant to changed behavior
- understand how to debug and profile issues

### Standard setup checklist

- Install the required language/runtime versions
- Set environment variables from a template or secret manager
- Install project dependencies with a pinned package manager
- Run the app and verify a basic happy path
- Confirm linting and formatting commands succeed

## Environment hygiene

- Keep local environments close to production when possible
- Avoid hard-coded secrets in code or config
- Use `.env.example` or similar for required variables
- Document steps that are not obvious
- Remove temporary debug code before merging

## Working effectively

### Keep changes small

Small, coherent changes are easier to review and reason about.

Good signals:

- one obvious purpose per PR
- limited scope per change set
- fewer incidental refactors

### Prefer explicitness

Prefer code that makes intent obvious to the next engineer.

Examples:

- descriptive names over short cryptic identifiers
- early returns over deeply nested conditionals
- explicit validation over silent coercion

## Debugging workflow

When debugging:

1. Reproduce the issue locally
2. Reduce the problem to a minimal example
3. Confirm the exact root cause
4. Patch the root cause, not just the symptom
5. Verify the fix with a focused test or scenario

## Tooling expectations

Use the toolchain the repo expects:

- a pinned package manager version
- project-level lint and format commands
- the standard test runner
- the repo's conventional build commands

Do not bypass required checks just to save time. The saved minute usually costs much more later.

## On-call and operational awareness

Developers should understand:

- how to run the app in local and staging environments
- where logs and metrics live
- which alerts or dashboards are relevant
- what the expected failure mode looks like

## Quick checklist

- [ ] Local setup works from a clean environment
- [ ] Required env vars are documented
- [ ] Basic app flow runs
- [ ] Focused tests pass
- [ ] No fix is hidden behind unrelated refactors
- [ ] Logs and debugging steps are understandable

## Suggested tools

Use the team's standard tools consistently:

- editor/IDE configuration
- formatter and linter
- git hooks or pre-commit checks
- local task runners
