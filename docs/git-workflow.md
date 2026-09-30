# Engineering Playbook

A practical full-stack engineering playbook covering Git, development workflows, testing, code quality, frontend, backend, databases, CI/CD, and other software engineering best practices.

## Quick navigation

| Topic | Description |
| --- | --- |
| [Git workflow](docs/git-workflow.md) | Branching, commit conventions, pull requests, and review expectations |
| [Development](docs/development.md) | Local setup, tooling, debugging, and day-to-day engineering habits |
| [Testing](docs/testing.md) | Unit, integration, and end-to-end testing strategies |
| [Code quality](docs/code-quality.md) | Linting, readability, refactoring, and maintainability |
| [Frontend](docs/frontend.md) | UI architecture, accessibility, performance, and React patterns |
| [Backend](docs/backend.md) | API design, service boundaries, reliability, and observability |
| [Databases](docs/databases.md) | Schema design, migrations, performance, and data safety |
| [CI/CD](docs/ci-cd.md) | Pipelines, deployment, release flow, and environment hygiene |

## Getting started

1. New to the team? Start with [Development](docs/development.md).
2. Working on a feature or fix? Review [Git workflow](docs/git-workflow.md).
3. Shipping code? Check [Testing](docs/testing.md) and [Code quality](docs/code-quality.md).
4. Building a user-facing feature? Use [Frontend](docs/frontend.md) and [Backend](docs/backend.md) as needed.

## What this playbook covers

- Best practices for writing maintainable, production-ready software
- Team workflows that reduce ambiguity and rework
- Guidance for full-stack delivery from idea to deployment
- Practical examples and checklists that are easy to follow

## Core principles

- Prefer clarity over cleverness
- Optimize for readability, reviewability, and maintainability
- Keep changes small and focused
- Make risk visible early
- Automate repetitive checks whenever possible
- Document decisions when trade-offs matter

## Repository structure

```text
engineering-playbook/
├── README.md
├── docs/
│   ├── git-workflow.md
│   ├── development.md
│   ├── testing.md
│   ├── code-quality.md
│   ├── frontend.md
│   ├── backend.md
│   ├── databases.md
│   └── ci-cd.md
├── examples/
│   └── README.md
└── templates/
    └── README.md
```

## Contributing

This playbook is meant to be practical and updated regularly. If you see outdated guidance, missing context, or a better pattern, please open an issue or submit a pull request.

## Recommended reading order

For a new contributor, a good sequence is:

1. [Development](docs/development.md)
2. [Git workflow](docs/git-workflow.md)
3. [Code quality](docs/code-quality.md)
4. [Testing](docs/testing.md)
5. Then branch into [Frontend](docs/frontend.md), [Backend](docs/backend.md), [Databases](docs/databases.md), and [CI/CD](docs/ci-cd.md)

---

This repository is intentionally opinionated but practical. Use the guidance here as a baseline, and adapt it to the realities of the product and team.
