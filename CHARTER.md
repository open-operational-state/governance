# Charter

## Mission

Open Operational State exists to define and maintain a vendor-neutral standard for machine-readable operational state of web services — enabling any web service to communicate its condition in a way that is discoverable, interoperable, and useful to monitors, platforms, and tooling regardless of vendor.

## Scope

The initiative is focused on operational state: what a web service says about its own condition, how it exposes that information, and how external systems discover, authenticate to, and interpret that information.

The v1 scope is locked to **machine-readable operational state of web services only**. See [SCOPE.md](SCOPE.md) for the full scope definition, non-goals, and expansion policy.

## Organizational Identity

**Open Operational State** is the name of the neutral ecosystem effort.

The GitHub organization is [`open-operational-state`](https://github.com/open-operational-state).

## Repositories

The initiative maintains the following repositories:

| Repository | Purpose |
|---|---|
| `.github` | Org-wide community health files and templates |
| `governance` | Charter, governance model, terminology, roadmap |
| `status-spec` | Technical specification |
| `status-conformance` | Conformance definitions, fixtures, test taxonomy |
| `status-tooling` | Vendor-neutral reference tooling |

Additional repositories require explicit approval per [PROJECT_RULES.md](https://github.com/open-operational-state/.github/blob/main/PROJECT_RULES.md).

## Architectural Foundation

The standard is built around a six-layer extensible architecture:

1. **Core Model** — stable, transport-agnostic semantics
2. **Profiles** — domain-specific specializations
3. **Serializations** — wire-level representations
4. **Adapters** — bridges for existing and legacy formats
5. **Discovery** — how monitors locate operational-state resources
6. **Capabilities / Negotiation** — what a target supports and how to interact

This architecture is locked. See the [Architecture document](https://github.com/open-operational-state/status-spec/blob/main/ARCHITECTURE.md) for details.

## Neutrality

This initiative is committed to genuine vendor neutrality. All assets under this organization must:

- Maintain a vendor-neutral tone
- Contain no proprietary product logic
- Be useful to any adopter regardless of vendor affiliation
- Use permissive licensing (CC BY 4.0 for documents, Apache 2.0 for code)

## Contributions

All contributions are governed by:

- [Developer Certificate of Origin (DCO)](https://developercertificate.org/) sign-off
- [Contributor Covenant v2.1](https://github.com/open-operational-state/.github/blob/main/CODE_OF_CONDUCT.md)
- [Contributing Guide](https://github.com/open-operational-state/.github/blob/main/CONTRIBUTING.md)

No Contributor License Agreement (CLA) is required at this time.
