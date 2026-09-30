# Git workflow

Good Git habits reduce merge conflicts, make reviews easier, and help teams ship with confidence.

## Core principles

- Keep changes small and scoped to one concern
- Prefer descriptive branch names
- Commit with clear purpose, not just activity
- Review before merge
- Protect the main branch with required checks

## Branching model

A simple, effective model is:

- `main` — production-ready, always releasable
- `feature/<short-name>` — work for a single feature or bug fix
- `fix/<short-name>` — small bug fixes when they are not tied to a broader feature
- `hotfix/<short-name>` — urgent production recovery changes
- `chore/<short-name>` — tooling, dependency, or maintenance updates

### Naming guidance

Use branches that explain the problem, not the implementation.

Good examples:

- `feature/user-onboarding-email`
- `fix/login-session-timeout`
- `chore/update-eslint-config`

Avoid:

- `feature/test`
- `fix/123`
- `work-in-progress`

## Commit practices

Write commits like a narrative:

- Explain the intent
- Keep scope narrow
- Use a clear summary before the body

Example:

```bash
git commit -m "Add retry logic for checkout API timeout"
```

For more detailed changes, add a short body:

```text
Add a retry policy for transient checkout API timeouts.

This avoids failing user purchases during brief upstream latency spikes.
It keeps retries bounded and logs the failure context for debugging.
```

## Pull request expectations

A pull request should answer three questions:

1. What changed?
2. Why did it change?
3. How do we know it is safe?

A solid PR includes:

- A clear title
- A brief description of the problem and solution
- Screenshots or recordings when UI changes
- Testing evidence
- Links to issue or ticket references

## Review etiquette

- Review the change, not the author
- Keep comments specific and actionable
- Prefer suggestions over broad criticism
- Ask questions when the intent is unclear
- Approve only when the change is correct and safe

## Merge strategy

Choose a workflow that matches the team:

- Squash merge for most feature work when a clean history matters
- Rebase if the team prefers a linear history and is comfortable with rebasing discipline
- Merge commit only when context is important and history needs to remain explicit

## Before opening a PR

- Rebase or merge the latest `main`
- Run target tests locally
- Ensure linting and formatting are clean
- Verify the change matches the ticket or issue description
- Remove dead code and debugging leftovers

## Checklist

- [ ] Branch name is clear and scoped
- [ ] Commit history is understandable
- [ ] PR description explains why and what
- [ ] Tests are included or updated
- [ ] No unrelated files are included
- [ ] Review comments are addressed

## Recommended resources

- [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow)
- [Conventional Commits](https://www.conventionalcommits.org/)
