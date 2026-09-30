# Testing

Testing is the safety net that helps teams move quickly without breaking trust.

## Test pyramid

A healthy project usually includes:

- unit tests for logic and isolated behavior
- integration tests for services, APIs, and data flows
- end-to-end tests for critical user journeys

## Principles

- Test behavior, not implementation details
- Prefer clear assertions over large fixture-heavy tests
- Keep failures focused and actionable
- Avoid brittle tests that depend on incidental UI formatting

## Unit tests

Use unit tests for:

- pure logic
- validation rules
- business logic and transformations
- edge conditions and failure paths

Good unit tests are:

- small
- deterministic
- easy to read
- fast enough to run regularly

## Integration tests

Use integration tests for:

- API contracts
- database interactions
- service orchestration
- authentication and authorization flows

These should validate the real behavior within the system boundary, without requiring full UI automation for every scenario.

## End-to-end tests

Use end-to-end tests for:

- critical user journeys
- release-blocking flows
- smoke coverage for deployment confidence

Keep them focused on the user path, not every component detail.

## Testing discipline

Before merging, validate the change with the smallest relevant test set.

Examples:

- run the changed unit test file
- run the targeted feature suite
- run smoke tests for deployment-critical paths

## Anti-patterns

Avoid:

- tests that assert internal implementation rather than outcome
- giant test files with mixed concerns
- intentionally flaky tests
- testing the same behavior in five different layers

## Coverage guidance

Coverage is useful, but it is not the goal. The goal is confidence in risky behavior.

Focus coverage where:

- business logic matters most
- failure modes are expensive
- changes are risky or frequently modified

## Example checklist

- [ ] The right test level was chosen
- [ ] The assertion checks behavior, not implementation
- [ ] The test is readable and names the scenario clearly
- [ ] It fails for the correct reason
- [ ] It is not overly coupled to incidental details

## Recommended practices

- Add tests when fixing bugs, not just when adding features
- Keep fixtures minimal and representative
- Prefer deterministic data and explicit setup
- Treat flaky tests as production issues
