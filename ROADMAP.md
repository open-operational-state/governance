# Roadmap

This roadmap describes the phased approach for Open Operational State. Phases are sequential but may overlap. Scope and deliverables may be refined through the governance process.

---

## Phase 1 — Scaffolding and Structure

**Status: Complete**

Establish serious organizational and repository structure before drafting normative technical details.

Deliverables:

- Repository structure across all five repos
- Governance documents (charter, scope, glossary, principles, governance model)
- Architecture summary document
- Scope and non-goals documentation
- Conformance philosophy documentation
- Tooling monorepo skeleton with package boundaries
- Terminology foundations
- Community health files and contribution guidelines

## Phase 2 — Architecture and Terminology

**Status: Complete**

Lock the conceptual model boundaries and stabilize terminology.

Deliverables:

- Detailed six-layer architecture document
- Core model conceptual definition
- Profile/serialization/adapters/discovery/capabilities framing
- Stabilized glossary with precise, unambiguous definitions
- v1 scope discipline enforcement
- Design notes for key architectural decisions

## Phase 3 — Specification Drafts

**Status: In Progress**

Create normative specification documents building on stabilized architecture and terminology.

Deliverables:

- Core model normative specification (RFC 2119 language)
- Condition vocabulary definitions with per-profile values and ecosystem mapping
- Profile normative specifications (Liveness, Readiness, Health, Status)
- Serialization specifications (health-response, service-status, http-status-only)
- Discovery specification (well-known path, link relations, discovery document)
- Capabilities/negotiation specification
- Adapter specifications (plain HTTP, health-check draft)
- Conformance level definitions (Basic, Standard, Extended)
- Initial test fixtures across all layers
- Locked decisions: vocabulary values, well-known path, link relation types, extension format, field names

## Future Phases

The following are anticipated but not yet formally scoped:

- **Reference implementation** — substantive tooling in `status-tooling` packages
- **Conformance suite** — automated validation tooling
- **Ecosystem adoption** — framework adapters, middleware, integrations
- **Formal standards consideration** — potential Internet-Draft or RFC path if adoption warrants

---

## Explicit Constraints

- Do not skip phases or begin later-phase work before prerequisites are met
- Do not define JSON field names or wire schemas before Phase 2 is complete
- Do not expand scope beyond web services for v1
- Do not create new repositories without explicit approval
