# Open Operational State — Founding Plan

This document preserves the original locked decisions that shaped the initiative. It is a historical record, not a living specification. For current governance, see [GOVERNANCE.md](GOVERNANCE.md). For current scope, see [SCOPE.md](SCOPE.md).

---

## 1. Initiative Identity

### 1.1 Working Initiative Name
**Open Operational State**

### 1.2 GitHub Organization
**`open-operational-state`**

### 1.3 Strategic Intent
The initiative exists to define a vendor-neutral ecosystem around machine-readable operational state. The architecture, specification, and tooling are designed so that any vendor, platform, or organization can adopt, implement, and influence the standard on equal footing.

---

## 2. Locked Scope Decision

### 2.1 v1 Scope
**v1 is locked to machine-readable operational state of web services only.**

This means the effort is focused on:
- HTTP-accessible web services
- APIs
- websites and web applications
- machine-readable operational state exposed over web-delivered interfaces
- health/status/readiness/liveness-style operational resources and related discovery/auth concepts

### 2.2 Scope Lock Rule
This scope is considered **locked** unless explicitly reopened.

### 2.3 Out of Scope for v1
The following are out of scope for the v1 operational-state standard:
- non-web systems as first-class targets
- generic network devices
- local-only process health outside a web-delivered interface
- arbitrary observability protocols as primary targets
- synthetic transaction coordination
- end-to-end form testing protocols
- generalized "everything that can emit state" standardization

### 2.4 Design Constraint Despite Narrow Scope
Although v1 scope is narrow, the **internal architecture must remain extensible** so non-web systems can fit later through profiles, adapters, and additional serializations or discovery mechanisms.

---

## 3. Ecosystem Relationship

### 3.1 Ecosystem Goal
The standard should be useful to and adoptable by:
- site owners
- framework authors
- platform teams
- monitoring vendors
- reverse proxies and infrastructure products
- API gateways and adjacent tooling

### 3.2 Commercial Adoption
The standard and related tooling should enable interoperability with monitoring platforms and related tooling, including:
- hosted monitoring
- onboarding and validation
- monitoring configuration
- analytics and dashboards
- alerting and automation
- enterprise coordination

---

## 4. Governance and Ownership Model

### 4.1 Organizational Split
The effort distinguishes between:
- a **neutral ecosystem organization** for the standard and vendor-neutral assets
- **commercial organizations** for vendor-specific products and product-specific tooling

### 4.2 Neutral Ecosystem Organization
The neutral ecosystem organization is **`open-operational-state`**.

Its purpose is to host assets that exist to advance adoption of the open standard regardless of vendor.

### 4.3 Commercial Organizations
Vendor-specific products, commercial SDKs, agents, dashboards, and integrations belong under their respective commercial organizations — not under the neutral ecosystem.

### 4.4 Ownership Rule
If a repository primarily exists to advance adoption of a commercial product, it belongs under the relevant commercial organization.

If a repository primarily exists to advance adoption of the open standard regardless of vendor, it belongs under the neutral organization.

### 4.5 Neutrality Constraint
The neutral ecosystem organization must look and behave genuinely neutral enough that **any vendor** could adopt the standard and still find the organization legitimate.

That means:
- vendor-neutral tone
- open governance documentation
- no vendor-specific bias in core spec assets
- no proprietary product logic in neutral tooling
- permissive licensing where appropriate

---

## 5. Repository Plan

### 5.1 Created Repositories
The following repositories have been created under `open-operational-state`:
- `.github`
- `governance`
- `status-spec`
- `status-conformance`
- `status-tooling-js`

### 5.2 Intended Purpose of Each Repository

#### `.github`
Shared organization-level templates and community health files.

#### `governance`
Organizational and process authority for:
- charter
- governance model
- decision-making process
- terminology control
- roadmap framing
- contribution and stewardship model

#### `status-spec`
Primary technical specification repository for the operational-state standard.

#### `status-conformance`
Conformance philosophy, fixtures, test cases, compatibility matrices, and related validation material.

#### `status-tooling-js`
Vendor-neutral reference tooling, ideally as a monorepo for shared packages and examples.

### 5.3 Repositories Not to Create Yet
The following are intentionally deferred:
- `status-site`
- `status-schemas`
- `status-fixtures`
- separate RFC repo
- additional niche repos before needed

---

## 6. Conceptual Scope of the Standard

### 6.1 What the Standard Is
The v1 standard is a standard for **machine-readable operational state of web services**.

### 6.2 What the Standard Is Not
The v1 standard is **not**:
- merely a health-check format
- a full observability standard
- a metrics or tracing standard
- a synthetic testing protocol
- a universal standard for all machine-readable state across all systems
- an attempt to standardize all network or device telemetry

### 6.3 Positioning
The best external framing is:

> A standard for machine-readable operational state of web services, with an extensible architecture that can support other system classes later.

---

## 7. Separation Between Operational State and Synthetic Testing

### 7.1 Locked Separation
The operational-state standard and synthetic transaction/form testing are related but distinct.

### 7.2 Operational-State Standard Concerns
The operational-state standard covers:
- what a target says about its current condition
- how a target exposes that condition
- how a monitor discovers, authenticates to, and interprets that condition

### 7.3 Synthetic Transaction Concerns
Synthetic transaction or form testing covers:
- externally executed user-like workflows
- proof that a workflow succeeded from the outside
- controlled coordination between monitoring platforms and site owners for safe, deterministic end-to-end tests

### 7.4 Future Relationship
A future companion protocol may exist for synthetic transaction coordination, but it is **not part of the v1 operational-state standard**.

### 7.5 Architectural Bridge
The operational-state standard may include concepts that recognize evidence provenance, such as:
- self-reported
- externally observed
- derived
- manually declared

But this does not merge synthetic transaction coordination into the spec.

---

## 8. Abstraction Model

The architecture is not limited to a single JSON schema or a single endpoint.

The system is understood as a layered abstraction.

### 8.1 Required Layers
The locked architectural direction includes these six layers:

1. **Core Model**
2. **Profiles**
3. **Serializations**
4. **Adapters**
5. **Discovery**
6. **Capabilities / Negotiation**

### 8.2 Core Model
The core model is the stable semantic center of the effort.

It should represent, in a transport-agnostic way:
- the thing being described
- normalized condition
- timestamps / observation timing
- evidence or basis of condition
- affected scope
- dependencies/components
- provenance/source type
- other universally meaningful concepts

The core model is where long-term semantic durability lives.

### 8.3 Profiles
Profiles specialize the core model for a domain or use case.

For v1, profiles are expected to remain within web-service scope.

Profiles may eventually distinguish among concepts such as:
- shallow liveness-style state
- readiness-style state
- rich health state
- service status state

Profiles define:
- required or optional fields in context
- semantics that apply in that context
- valid interpretations and constraints

### 8.4 Serializations
Serializations define on-the-wire representations.

They are separate from profiles because meaning and wire shape are distinct concerns.

The architecture must support multiple normative serializations rather than one forced universal body format.

### 8.5 Adapters
Adapters translate native or legacy target formats into the core model and profiles.

Adapters are the mechanism by which the ecosystem can ingest:
- existing frameworks
- vendor-specific health/status formats
- legacy conventions
- plain HTTP status/body patterns

Adapters are essential to the goal of broad interpretability.

### 8.6 Discovery
Discovery explains how monitors find available operational-state resources and determine what they represent.

Discovery includes:
- resource location
- relation to other resources
- profile awareness
- public vs authenticated endpoints
- richer vs shallower resources
- optional DNS-assisted bootstrap

### 8.7 Capabilities / Negotiation
Capabilities describe what a target supports.

Negotiation covers how a monitor and target may determine:
- which profile(s) exist
- which serialization(s) exist
- what auth modes apply
- what evidence depth is available
- what kinds of condition statements the target can emit

This layer prevents extensibility from becoming opaque or fragile.

---

## 9. Key Structural Conclusion on Standards Integration

### 9.1 Dual-Draft Insight
The old health-check draft and the newer service-status draft cannot be collapsed into a single strict universal wire format without structural conflicts.

### 9.2 Locked Architectural Response
The correct approach is:
- **one core model**
- **multiple normative serializations / profiles**
- **clear mappings between them**
- **internal normalization, external representation flexibility**

### 9.3 Rejected Approach
A single hybrid payload that pretends to be fully compliant with both drafts at once is not the chosen direction.

### 9.4 Embrace of Multiple Shapes
The architecture should ingest and normalize many external shapes, while publishing a disciplined model and explicit representations.

---

## 10. Recommended Standards Pattern

### 10.1 Pattern Chosen
The preferred pattern is:

**core model + two or more official representations/serializations + discovery + conformance levels + extension rules**

### 10.2 Why This Pattern Was Chosen
This pattern best balances:
- compatibility
- clarity
- future extensibility
- vendor neutrality
- realistic adoption
- standards credibility

### 10.3 Important Constraint
Unification should happen:
- at the **model layer**
- at the **profile layer**
- through **mappings**

It should **not** happen by forcing every existing or future representation into one universal body shape.

---

## 11. Scope Expansion Policy

### 11.1 Current Decision
The effort should **not** broaden its v1 marketed or formalized scope beyond web services.

### 11.2 Design Principle
The project should:
- **scope narrowly**
- **design broadly**

### 11.3 Locked External Scope
External scope stays focused on machine-readable operational state of web services.

### 11.4 Internal Architectural Flexibility
Internal architecture may remain broad enough to support future extension to non-web systems, but those are not part of v1.

---

## 12. DNS Policy

### 12.1 DNS Is Optional, Not Primary
DNS may play a role, but it is not the main protocol surface.

### 12.2 Primary Role of DNS
DNS is most valuable for:
- domain control verification
- optional bootstrap discovery
- possibly specialized trust anchoring in advanced cases

### 12.3 DNS Roles Favored
High-confidence DNS uses include:
- TXT-based domain verification
- optional DNS-assisted bootstrap discovery for ecosystem-aware clients

### 12.4 DNS Roles Not Favored
DNS should not be the primary vehicle for:
- main operational-state semantics
- reusable auth secrets
- replacing HTTP-native discovery and representation

### 12.5 Locked Principle
HTTP remains normative for the resource itself; DNS may assist with discovery or ownership verification.

---

## 13. Discovery and HTTP Orientation

### 13.1 HTTP-Native Center of Gravity
The effort is centered on web-delivered operational state, so HTTP is the primary control plane.

### 13.2 Discovery Principle
Discovery should be treated as a first-class layer, not reduced to hard-coded path guessing alone.

### 13.3 Preferred Discovery Direction
The effort should support:
- link-based discovery
- predictable HTTP-accessible resources
- optional DNS bootstrap
- public vs private endpoint distinction
- richer vs shallower resource distinction

### 13.4 Content Negotiation Position
Content negotiation may be supported, but it should not be the sole or primary operational path early on.

Separate resources are simpler and more practical initially.

---

## 14. Authentication and Security Direction

### 14.1 Authentication Is First-Class
Authentication is a first-class part of the ecosystem design, not an optional add-on. Operational state may be exposed publicly or via authenticated access. The architecture must support both modes as equally legitimate.

### 14.2 Public vs Private Split
The architecture should allow distinction between:
- shallow public operational-state resources
- deeper authenticated operational-state resources

### 14.3 Security Principle
The ecosystem should support broad compatibility while avoiding accidental exposure of sensitive implementation details.

### 14.4 Exposure Philosophy
Public exposure of operational state is **optional**, not required. Implementations may restrict detail based on audience and authentication level. Foundational guidance:

- Public endpoints should generally expose only coarse condition (e.g., `operational`, `degraded`, `down`)
- Detailed topology, component names, and dependency information may be sensitive and should be restricted to authenticated consumers
- Discovery and capabilities metadata may itself expose sensitive information and should be treated with the same care as the resources they describe
- Exposing no public operational-state endpoint at all is a valid choice

### 14.5 Compatibility Direction
The eventual standard and tooling should work with realistic auth approaches used by monitoring systems and site owners, rather than assuming all resources are public.

---

## 15. Conformance Philosophy

### 15.1 Conformance Is Strategic
Conformance is not an afterthought. It is a core ecosystem asset.

### 15.2 Why It Matters
Conformance enables:
- trust
- compatibility validation
- interoperability testing
- quality control for implementations

### 15.3 Locked Repo Role
`status-conformance` exists to hold:
- fixtures
- test taxonomy
- conformance definitions
- compatibility cases
- ecosystem mappings
- possibly reports and validation artifacts

---

## 16. Neutral Tooling Philosophy

### 16.1 Neutral Tooling Exists
There should be vendor-neutral reference tooling.

### 16.2 What Neutral Tooling Means
Neutral tooling may include:
- parsers
- normalizers
- emitters
- validators
- framework adapters
- sample middleware
- example implementations

### 16.3 What Neutral Tooling Must Not Be
Neutral tooling should not:
- depend on any vendor-specific APIs
- phone home to any commercial service
- assume vendor-specific onboarding
- embed commercial product logic

### 16.4 Commercial Boundary
If a tool exists primarily to drive or couple to a vendor-specific product experience, it belongs under that vendor's organization, not the neutral organization.

---

## 17. Open vs Closed Asset Policy

### 17.1 Open Assets
The following should be open and live in the neutral ecosystem where appropriate:
- spec
- governance docs
- conformance material
- reference tooling
- vendor-neutral examples
- neutral schemas or fixtures if later needed

### 17.2 Commercial Assets
The following are examples of assets that belong under vendor-specific organizations:
- hosted monitoring networks
- dashboards and analytics
- enterprise onboarding systems
- premium integrations
- proprietary coordination or scoring logic

### 17.3 Business Model Principle
The protocol and ecosystem are open. Operational services and premium value layers built on top are commercial.

---

## 18. RFC and Formal Standards Position

### 18.1 Do Not Start With RFCs
Formal RFC work is not the immediate first step.

### 18.2 Immediate Priority
Immediate priority is:
- public spec scaffolding
- governance clarity
- implementation structure
- conformance foundations
- early real-world usefulness

### 18.3 Future Possibility
An Internet-Draft or RFC path may be considered later if:
- the work gains real traction
- the concepts stabilize
- multiple stakeholders or adopters emerge
- formalization becomes strategically valuable

### 18.4 Authorship Direction
Any eventual standards-track-style documents should be approached in a way that supports legitimacy and broad adoption, rather than looking like a proprietary vendor standard.

---

## 19. GitHub Organization Naming Decision

### 19.1 Chosen Name
The neutral ecosystem organization name is locked as:

**Open Operational State**
GitHub organization: **`open-operational-state`**

### 19.2 Why This Name Was Chosen
The name is:
- open enough for a neutral ecosystem effort
- precise enough to avoid vagueness
- not limited to "health"
- not centered on "testing"
- broad enough to host future adjacent specs
- still anchored in operational state as the center of gravity

### 19.3 Future Compatibility
The chosen name is intentionally broad enough that a future companion spec (e.g., synthetic transaction coordination) could plausibly live under the same umbrella without forcing a rename.

---

## 20. Initial Repository Action Plan

### 20.1 Immediate Repositories
The immediate repository set under `open-operational-state` is:
- `.github`
- `governance`
- `status-spec`
- `status-conformance`
- `status-tooling-js`

### 20.2 Initial Work Sequence
The first implementation phase is repository scaffolding, not final spec authorship.

### 20.3 Phase 1 Focus
Phase 1 should establish:
- repo structure
- governance docs
- scope and non-goals
- architecture summary
- terminology
- conformance philosophy
- tooling package boundaries

### 20.4 Phase 2 Focus
Phase 2 should lock:
- conceptual model boundaries
- six-layer architecture
- profile/serialization/adapters/discovery/capabilities framing
- v1 scope discipline

### 20.5 Phase 3 Focus
Phase 3 should create the first serious documents, including:
- charter/governance docs
- architecture doc
- scope doc
- glossary
- non-goals
- conformance model
- tooling architecture
- only then deeper technical definitions

### 20.6 Explicit Warning
Do **not** start with final JSON fields or detailed wire schemas before architecture, scope, and terminology are disciplined.

---

## 21. Locked Six-Layer Architecture Responsibilities

### 21.1 Core Model Responsibility
Provide stable, canonical semantics for operational-state meaning across representations.

### 21.2 Profiles Responsibility
Specialize the core model for concrete use cases within web-service scope.

### 21.3 Serializations Responsibility
Define wire-level representations without conflating them with semantics.

### 21.4 Adapters Responsibility
Bridge existing or foreign systems into the standard model.

### 21.5 Discovery Responsibility
Allow monitors to locate and understand available operational-state resources.

### 21.6 Capabilities / Negotiation Responsibility
Communicate what a target can provide and how a monitor can interact with it.

---

## 22. Evidence and Provenance Direction

### 22.1 Importance
Operational condition may originate from different sources, and the architecture should preserve enough room to represent that.

### 22.2 Expected Provenance Concepts
The architecture should support the concept that condition information may be:
- self-reported
- externally observed
- derived
- manually declared

### 22.3 Why This Matters
This distinction is important because:
- a system can claim it is healthy
- an external monitor can observe failure
- both statements can be meaningful simultaneously

Consumers of operational-state data should interpret it in the context of its provenance. A self-reported `operational` condition carries different weight than an externally observed one.

### 22.4 Scope Boundary
This provenance awareness belongs in the model direction, but it does not collapse synthetic testing into the operational-state spec.

---

## 23. What Is Locked vs What Remains Open

### 23.1 Locked Decisions
The following are considered locked unless explicitly reopened:
- v1 scope is machine-readable operational state of web services only
- synthetic transaction coordination is separate from the v1 operational-state spec
- architecture should remain extensible for non-web systems later
- the six-layer abstraction model is the correct architectural direction
- Open Operational State is the neutral ecosystem name
- the neutral/commercial organization split is correct in principle
- HTTP is the primary protocol surface; DNS is optional support
- core model plus multiple representations/serializations is preferred over one forced hybrid body
- repository strategy under `open-operational-state` is established

### 23.2 Open Future Decisions
The following remain open for future work:
- exact field names
- exact serialization details
- exact profile definitions
- exact discovery mechanics
- exact auth schemes and normative requirements
- exact conformance levels
- exact tooling package structure
- exact standards-body path later

---

## 24. One-Sentence Locked Summary

**Open Operational State is a vendor-neutral ecosystem effort focused in v1 on machine-readable operational state of web services only, built around a six-layer extensible architecture, kept separate from future synthetic transaction coordination, and structured so open standards adoption can benefit any vendor, platform, or organization equally.**
