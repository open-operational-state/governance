# Governance Model

## Overview

Open Operational State uses a lightweight, transparent governance model appropriate for an early-stage standards effort. As the project matures and attracts additional contributors, this model may evolve.

## Roles

### Stewards

Stewards are the primary maintainers and decision-makers for the initiative. They are responsible for:

- Maintaining the specification and related repositories
- Reviewing and merging contributions
- Enforcing project rules and scope discipline
- Making architectural and governance decisions
- Managing the roadmap

See [STEWARDSHIP.md](STEWARDSHIP.md) for the stewardship model.

### Contributors

Contributors are anyone who participates in the project through:

- Issues, discussions, or proposals
- Pull requests (code, documentation, fixtures)
- Design feedback or review

All contributors must follow the [Code of Conduct](https://github.com/open-operational-state/.github/blob/main/CODE_OF_CONDUCT.md) and [Contributing Guide](https://github.com/open-operational-state/.github/blob/main/CONTRIBUTING.md).

## Decision-Making

### Day-to-Day Decisions

Stewards make routine decisions (merging PRs, triaging issues, minor edits) independently using their best judgment.

### Significant Decisions

Decisions that affect scope, architecture, governance, or locked constraints require:

1. A written proposal (issue or design note)
2. Review period of at least 7 days
3. Consensus among active stewards
4. An Architecture Decision Record (ADR) in [decisions/](decisions/)

### Decision Severity Levels

Not all changes carry equal weight. Changes are classified by severity to ensure proportional process:

| Severity | Examples | Process |
|---|---|---|
| **Editorial** | Typo fixes, formatting, wording clarification | Direct merge by any steward |
| **Minor technical** | Non-breaking spec refinements, tooling improvements, new fixtures | Standard PR review |
| **Major** | Scope changes, architecture modifications, locked-decision changes | Formal proposal + review period + ADR |

### Locked Decisions

Certain decisions are considered **locked** and cannot be changed without an explicit, documented reopening process. These include:

- v1 scope (web services only)
- Six-layer architecture model
- Separation of operational state from synthetic testing
- HTTP as the primary protocol surface
- Core model + multiple serializations (not one forced hybrid body)

See [PROJECT_RULES.md](https://github.com/open-operational-state/.github/blob/main/PROJECT_RULES.md) for the full list.

### Reopening Locked Decisions

To reopen a locked decision:

1. Open an issue with the `governance` label explaining why the decision should be reconsidered
2. Provide evidence or rationale for the change
3. Allow a review period of at least 14 days
4. Require unanimous agreement among active stewards
5. Document the outcome as an ADR

## Transparency

- All governance decisions are documented publicly
- Architecture Decision Records track significant choices
- Roadmap and scope changes are reflected in this repository
- No decisions are made in private channels without public documentation

## Evolution

This governance model is intentionally simple for an early-stage effort. As the project grows, it may be updated to include:

- Formal working groups
- Voting procedures
- Advisory board structure
- Graduated contributor roles

Changes to the governance model follow the "Significant Decisions" process above.
