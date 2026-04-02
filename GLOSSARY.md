# Glossary

This glossary defines controlled terminology for the Open Operational State initiative. These definitions are authoritative across all repositories.

**Authority rule:** The glossary in governance is the single source of truth. All spec documents must use terms consistently with these definitions. If a term is used in spec text that is not in this glossary, it should be added here first.

For spec-level applied usage and context, see the [terminology directory](https://github.com/open-operational-state/status-spec/blob/main/terminology/) in `status-spec`.

---

## Adapter

A component that translates a native or legacy target format into the core model and profiles. Adapters enable the ecosystem to ingest existing frameworks, vendor-specific formats, and legacy conventions without requiring targets to change their implementations.

## Capabilities

The set of features and behaviors that a target supports, including which profiles, serializations, and authentication modes are available. See also: **Negotiation**.

## Component

A constituent part of a target whose operational condition is tracked. Components exist within the target's operational boundary. A component is itself a subject with its own condition, timing, evidence, and provenance. Distinguished from a **Dependency** by being internal to the target. See also: **Dependency**, **Subject**.

## Condition

The normalized operational state of a subject at a point in time, within a specific scope. Condition values are drawn from a **Condition Vocabulary** appropriate to the profile. Within a single snapshot, there must be at most one condition per subject per scope. See also: **Condition Vocabulary**, **Snapshot**.

## Condition Vocabulary

The defined set of allowed condition values within a profile. A condition vocabulary specifies the valid values, their meanings, and whether they are orderable (have severity ordering) or categorical (represent distinct states without inherent ordering). Each profile defines its own condition vocabulary.

## Conformance

The degree to which an implementation satisfies the requirements defined by the standard. Conformance is assessed through fixtures, test taxonomy, and validation tooling.

## Core Model

The stable, transport-agnostic semantic center of the operational-state standard. The core model defines the canonical concepts (Subject, Condition, Timing, Evidence, Scope, Components, Dependencies, Provenance) that all profiles and serializations reference. It is the normative semantic foundation of the standard.

## Dependency

An external system or service that a target relies on but does not own or operate. A dependency is itself a subject with its own condition. Distinguished from a **Component** by being external to the target's operational boundary. A dependency from one target's perspective may be a service from its own. See also: **Component**, **Subject**.

## Discovery

The process by which a monitor locates available operational-state resources and determines what they represent, including resource location, profile awareness, public vs. authenticated endpoints, and optional DNS-assisted bootstrap. The standard defines a priority hierarchy: link-based (primary), well-known path (fallback), inline references, DNS (optional).

## Evidence

The basis on which a condition is asserted — what checks, observations, measurements, or inputs informed the condition statement. Evidence describes **what was checked**, while provenance describes **who checked it**. See also: **Provenance**.

## Fidelity

The degree of information preservation in an adapter mapping. Classified as: lossless (all source information maps cleanly), partially lossy (some information documented as lost), heuristic (mapping relies on inference), or inferred (core model fields populated from indirect evidence).

## Monitor

Any external system, tool, or agent that discovers, retrieves, and interprets operational-state information from a target.

## Negotiation

The process by which a monitor and target determine which profiles, serializations, and interaction modes are available. Part of the Capabilities layer.

## Operational State

Machine-readable information about the current condition of a web service — encompassing health, readiness, liveness, status, and related concepts. This is what the standard defines.

## Profile

A specialization of the core model for a specific domain or use case. Profiles select which core model concepts are required or optional, define condition vocabularies, and constrain valid interpretations in context. Profiles must not redefine core model semantics. A single resource may declare conformance to multiple profiles simultaneously — profiles are composable, not mutually exclusive.

## Provenance

The origin or method by which a condition statement was generated. Provenance is per-condition-statement, not per-snapshot. The core model defines four provenance types:

- **Self-reported** — the target claims its own condition
- **Externally observed** — a monitor or external system observes the condition
- **Derived** — the condition is computed from other data
- **Manually declared** — a human operator has set the condition

Provenance does not imply trust. See also: **Evidence**.

## Scope

What part of the system a condition statement applies to. Scope delineates the boundary of a condition's applicability and may be whole-service, component-specific, dependency-specific, endpoint-specific, or regional/zonal. If no explicit scope is provided, the condition applies to the subject as a whole. See also: **Subject**.

## Serialization

A wire-level representation of operational-state data. Serializations define how core model concepts are expressed in a concrete format (e.g., JSON). Serializations are separate from profiles because meaning and wire shape are distinct concerns. The architecture supports multiple normative serializations. A serialization must not introduce new semantics that have no counterpart in the core model.

## Snapshot

An immutable observation of operational state at a point in time. Each observation produces an independent snapshot. A snapshot contains one or more condition statements and may include structural relationships between subjects. Snapshots do not represent time ranges or transitions — v1 treats each snapshot as standalone.

## Subject

The entity whose operational state is being described — a service, endpoint, component, or dependency. A subject must be uniquely identifiable within a snapshot and stably identifiable across snapshots. See also: **Component**, **Dependency**.

## Target

A web service, API, website, or web application that exposes operational-state information. The entity being described by the standard.

## Timing

Temporal metadata associated with a condition statement. The core model distinguishes three temporal concepts: observation time (when the condition was measured), report time (when it was communicated), and state-change time (when the condition last transitioned to its current value).

## Well-Known Resource

A predictable URI path (per RFC 8615) used for discovery. In the context of this standard, a well-known resource serves as a discovery document — not necessarily the operational-state payload itself.
