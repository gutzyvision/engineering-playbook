# Databases

A reliable database layer is foundational to system health, performance, and correctness.

## Design principles

- model the domain clearly
- keep schema changes intentional and reviewed
- avoid unnecessary complexity in early designs
- prefer explicit constraints and invariant checks
- design for operational safety

## Schema and migrations

- migrations should be reversible or carefully planned
- large schema changes should be reviewed with operational impact in mind
- constraints and indexes should reflect real query patterns
- preserve data integrity over convenience

## Query and performance

- begin with correct and readable queries
- measure before optimizing
- use indexes where they provide clear value
- avoid N+1 query patterns by default
- understand the cost of expensive operations in production

## Data safety

- back up and test restore processes
- protect destructive operations behind careful review and automation
- consider transaction boundaries and consistency requirements
- monitor for growth, lock contention, and slow queries

## Operational habits

- watch for slow query trends over time
- keep migration strategies clear for deploy windows
- document assumptions and data conventions
- treat database schema decisions as architecture decisions

## Checklist

- [ ] Schema changes are intentional and reviewed
- [ ] Indexes are justified by query patterns
- [ ] Data integrity constraints are explicit
- [ ] Production-impacting changes are understood before rollout
- [ ] Backups and recovery steps are known
