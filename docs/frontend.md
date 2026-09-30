# Code quality

Code quality is not optional. It is the difference between something that ships once and something that remains understandable, safe, and maintainable.

## What good code quality looks like

- easy to read and reason about
- consistent with team conventions
- safe under change
- easy to test and debug
- resilient under future requirements

## Practices that matter

### Keep functions focused

A function should do one thing well. If a function is doing too much, break it into smaller units with clear names.

### Prefer explicitness

Prefer readable code over clever code. The person who reads it next may be a teammate under time pressure.

### Keep interfaces small

Thin interfaces and clear boundaries reduce accidental coupling and make systems easier to evolve.

### Refactor with purpose

Refactor when it improves clarity, reduces duplication, or reduces risk. Do not mix cleanup with unrelated behavior changes.

## Linting and formatting

Use the repo's standard tooling consistently.

Typical expectations:

- format on save or pre-commit
- lint before merge
- avoid bypassing rules for convenience

## Review quality

High-quality code review should focus on:

- correctness
- readability
- maintainability
- security and reliability
- risk of unintended side effects

Review comments should be actionable and specific.

## Error handling

Do not swallow errors silently. Prefer:

- clear error messages
- typed failures when applicable
- logs or tracing at the right boundary
- graceful degradation where appropriate

## Performance and maintainability

Performance should be driven by evidence. Avoid premature optimization, but do not ignore hot paths or obvious inefficiencies.

A good default is:

- optimize only when there is a real bottleneck
- use benchmarks or profiling when needed
- keep code understandable before micro-optimizing

## Behavior over style

Uniform style matters, but correctness and safety matter more. Standardize conventions that support maintainability and clarity.

## Checklist

- [ ] The code is easy to follow without extra explanation
- [ ] Naming is clear and consistent
- [ ] Error handling is explicit
- [ ] The change is not mixed with unrelated cleanup
- [ ] Lint and validation checks pass
- [ ] The change is easy to test
