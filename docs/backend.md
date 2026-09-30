# Frontend

This guide covers practical frontend engineering standards for user-facing products and interfaces.

## Principles

- Build for accessibility from the start
- Optimize for fast feedback and predictable behavior
- Keep component boundaries clear
- Prefer simple, composable UI patterns
- Treat performance as part of correctness

## State and data flow

- Keep state as close to where it is used as practical
- Avoid duplicating state unnecessarily
- Prefer explicit data flow over hidden side effects
- Keep asynchronous flows predictable and observable

## Components

Good components are:

- small and focused
- easy to reason about
- reusable only when the abstraction is genuinely useful
- consistent in naming and structure

Avoid creating a generic abstraction before the actual repeated behavior is clear.

## Accessibility

Accessibility is part of feature quality, not a separate phase.

Minimum expectations:

- semantic HTML
- proper focus states
- keyboard support for interactive controls
- meaningful labels and alt text
- color contrast that respects usability

## Performance

Frontend performance matters for user trust and product quality.

Prefer:

- lazy loading where appropriate
- efficient rendering and memoization only when justified
- minimal unnecessary re-renders
- optimized asset loading and image handling

Do not optimize prematurely without measuring or observing a real bottleneck.

## Forms and UX

- Validate early and clearly
- Provide useful feedback on errors
- Keep actions explicit and predictable
- Do not surprise users with destructive behavior

## Testing frontend behavior

Test critical functionality and user flows rather than visual implementation details. Prefer tests that check user-visible outcomes and interaction states.

## Checklist

- [ ] Interfaces are keyboard accessible
- [ ] Loading, empty, and error states are handled
- [ ] Navigation and actions are explicit and understandable
- [ ] Performance-sensitive code is validated with evidence
- [ ] State transitions are predictable
