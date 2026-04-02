# Glossary

This glossary defines controlled terminology for the Open Operational State initiative. These definitions are authoritative across all repositories.

For spec-level applied usage and context, see the [terminology directory](https://github.com/open-operational-state/status-spec/blob/main/terminology/) in `status-spec`.

---

## Adapter

A component that translates a native or legacy target format into the core model and profiles. Adapters enable the ecosystem to ingest existing frameworks, vendor-specific formats, and legacy conventions without requiring targets to change their implementations.

## Capabilities

The set of features and behaviors that a target supports, including which profiles, serializations, and authentication modes are available. See also: **Negotiation**.

## Condition

The normalized operational state of a target or component at a point in time. Condition is a semantic concept in the core model, distinct from any specific wire representation.

## Conformance

The degree to which an implementation satisfies the requirements defined by the standard. Conformance is assessed through fixtures, test taxonomy, and validation tooling.

## Core Model

The stable, transport-agnostic semantic center of the operational-state standard. The core model defines the canonical concepts (condition, provenance, scope, timing, dependencies, etc.) that all profiles and serializations reference.

## Discovery

The process by which a monitor locates available operational-state resources and determines what they represent, including resource location, profile awareness, public vs. authenticated endpoints, and optional DNS-assisted bootstrap.

## Monitor

Any external system, tool, or agent that discovers, retrieves, and interprets operational-state information from a target.

## Negotiation

The process by which a monitor and target determine which profiles, serializations, and interaction modes are available. Part of the Capabilities layer.

## Operational State

Machine-readable information about the current condition of a web service — encompassing health, readiness, liveness, status, and related concepts. This is what the standard defines.

## Profile

A specialization of the core model for a specific domain or use case. Profiles define which fields are required or optional, what semantics apply, and what valid interpretations exist in context.

## Provenance

The origin or basis of a condition statement. Provenance concepts include:

- **Self-reported** — the target claims its own condition
- **Externally observed** — a monitor or external system observes the condition
- **Derived** — the condition is computed from other data
- **Manually declared** — a human operator has set the condition

## Serialization

A wire-level representation of operational-state data. Serializations are separate from profiles because meaning and wire shape are distinct concerns. The architecture supports multiple normative serializations.

## Target

A web service, API, website, or web application that exposes operational-state information. The entity being described by the standard.
