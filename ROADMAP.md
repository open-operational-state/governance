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

**Status: Complete**

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

## Phase 4 — Reference Implementation and Adoption Tooling

**Status: Not Started**

Build the reference implementation, conformance validator, and developer tooling that makes the standard usable. This is not further specification work — it is productization of the completed standard.

### Delivery Order

The order in which users experience value. Each step delivers benefit before requiring deeper buy-in:

1. **Conformance validation** — verify that live or static responses meet conformance levels using the fixtures from `status-conformance`. Proves the conformance model works.

2. **HTTP adapter support** — parse plain HTTP status code responses and `draft-inadarei` health check responses into canonical core model instances. First real proof that the adapter architecture works end-to-end.

3. **CLI surface** — command-line tool for probing, validating, and inspecting operational-state endpoints. Tangible developer-facing surface that consumes all prior work.

4. **Spring Boot adapter support** — parse Spring Boot Actuator responses into the canonical model. Higher-friction ecosystem adapter, built after the core path is proven.

5. **Native serialization** — emit `application/health+json` and `application/status+json` from core model instances. Enables targets to produce spec-conformant responses.

6. **Discovery client** — well-known path resolution, Link header parsing, discovery document consumption.

### Package Responsibility

Where code lives. The monorepo names reusable architectural primitives, not endpoint-specific silos:

| Package | Responsibility |
|---|---|
| `types` | Canonical TypeScript types — the shared contract surface for the core model |
| `core` | Model rules, normalization, aggregation, mapping helpers |
| `parser` | External input → canonical model (all adapter logic lives here) |
| `emitter` | Canonical model → spec serialization wire formats |
| `validator` | Fixture execution, conformance level checking |
| `discovery` | Well-known docs, link relation handling, capabilities helpers |

A single delivery milestone typically touches multiple packages. For example, "HTTP adapter support" requires types in `types`, parsing logic in `parser`, normalization rules in `core`, and validation coverage in `validator`.

### Deliverables

- Substantive implementation in all `status-tooling` packages
- Automated conformance suite using `status-conformance` fixtures
- CLI for endpoint probing, validation, and inspection
- Expanded fixture library (edge cases, negative tests, integration scenarios)
- Developer documentation and getting-started guides
- Ecosystem adapter implementations (Kubernetes, Spring Boot — embedded in parser/adapter logic)

## Future Phases

The following are anticipated but not yet formally scoped:

- **Ecosystem adoption** — framework middleware, platform integrations, language-specific SDKs beyond TypeScript
- **Extension registry** — formal registration mechanism for custom condition values and vocabularies
- **Formal standards consideration** — potential Internet-Draft or RFC path if adoption warrants

---

## Explicit Constraints

- Do not skip phases or begin later-phase work before prerequisites are met
- Do not expand scope beyond web services for v1
- Do not create new repositories without explicit approval
- Do not create new `status-tooling` packages without explicit approval
