# Scope

## v1 Scope

**v1 is locked to machine-readable operational state of web services only.**

This means the effort is focused on:

- HTTP-accessible web services
- APIs
- Websites and web applications
- Machine-readable operational state exposed over web-delivered interfaces
- Health, status, readiness, and liveness-style operational resources
- Related discovery and authentication concepts

## What Operational State Means

The operational-state standard covers:

- What a target says about its current condition
- How a target exposes that condition
- How a monitor discovers, authenticates to, and interprets that condition

## Out of Scope for v1

The following are explicitly out of scope for v1:

- Non-web systems as first-class targets
- Generic network devices
- Local-only process health outside a web-delivered interface
- Arbitrary observability protocols as primary targets
- Synthetic transaction coordination
- End-to-end form testing protocols
- Generalized "everything that can emit state" standardization
- Metrics or tracing standards
- Full observability standards

## Design Constraint

Although v1 scope is narrow, the **internal architecture must remain extensible** so non-web systems can fit later through profiles, adapters, and additional serializations or discovery mechanisms.

The guiding principle is: **scope narrowly, design broadly.**

## Scope Expansion Policy

The v1 scope is considered **locked** unless explicitly reopened through the governance process described in [GOVERNANCE.md](GOVERNANCE.md).

To propose a scope expansion:

1. Open an issue in this repository with the `scope` label
2. Provide concrete evidence that the expansion is necessary and cannot be deferred
3. Demonstrate that the expansion does not compromise v1 deliverables
4. Follow the locked-decision reopening process

Scope should not be expanded to chase breadth at the expense of depth, quality, or delivery.
