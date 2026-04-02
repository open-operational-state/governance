# Principles

These principles guide all design, specification, and tooling decisions across the Open Operational State initiative.

## 1. Vendor Neutrality

The standard and all neutral-organization assets must be genuinely useful to any adopter, regardless of vendor affiliation. No single vendor's product logic, APIs, or onboarding flows should influence the standard's design.

Another vendor should be able to adopt the standard and find the organization legitimate.

## 2. Semantic Durability

The core model should prioritize long-term semantic stability. Wire formats and serializations may evolve, but the meaning of operational-state concepts should remain durable across versions and representations.

## 3. Separation of Meaning and Shape

Semantics (what operational state means) and serialization (how it appears on the wire) are distinct concerns. The architecture must never conflate a specific JSON structure with the canonical meaning of a concept.

## 4. Extensibility by Design

The architecture must support future extension — new profiles, new serializations, new discovery mechanisms, new system classes — without requiring breaking changes to the core model.

v1 is intentionally narrow in scope, but the architecture is intentionally broad in design.

## 5. Interoperability Over Purity

The standard should meet the real world where it is. Adapters exist specifically to bridge existing, legacy, and vendor-specific formats into the standard model. Broad interpretability is more valuable than ideological purity.

## 6. Discovery as a First-Class Concern

Monitors should not have to guess where operational-state resources live or what they represent. Discovery is a dedicated architectural layer, not an afterthought bolted onto path conventions.

## 7. Authentication Awareness

Operational-state resources may be public or private. The architecture must support both shallow public resources and deeper authenticated resources without assuming all endpoints are openly accessible.

## 8. Conformance as an Ecosystem Asset

Conformance definitions, fixtures, and test taxonomy are strategic assets — not afterthoughts. They enable trust, compatibility validation, and quality control across implementations.

## 9. Discipline Over Speed

Architecture, scope, and terminology must be stabilized before detailed wire schemas or field names are defined. Premature specification detail is a greater risk than slow specification progress.

## 10. Simplicity Where Possible

Prefer simple, practical designs over theoretically elegant but operationally complex ones. Separate resources over complex negotiation. Explicit structure over implicit convention. Clear constraints over flexible ambiguity.
