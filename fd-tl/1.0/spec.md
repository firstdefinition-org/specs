# FD-TL 1.0 — FirstDefinition Truth Layer Specification

**Status:** Public Draft  
**Version:** 1.0  
**Maintained by:** FirstDefinition  
**Last updated:** 2026-01-01
FD-TL 1.0 — FirstDefinition Truth Layer Specification
Status: Public Draft Version: 1.0 Maintained by: FirstDefinition Last updated: 2026-01-01

1. Purpose
FD-TL (FirstDefinition Truth Layer) defines a domain-owned, machine-readable canonical source of truth for a business.
Its purpose is to allow machines — including AI systems, agents, and automations — to reason about a business without inference, hallucination, or ambiguity.
FD-TL is not a conversational system. FD-TL is not a runtime context protocol. FD-TL is a pre-conversational authority layer.

2. Design Principles
FD-TL is built on four principles:
Authority over inference Truth must be explicitly declared, not guessed.
Domain ownership The business controls its own canonical definitions on its own domain.
Separation of concerns Truth is defined once; reasoning happens elsewhere.
Silence over invention If something is undefined, machines must not fabricate answers.

3. Discovery
A compliant domain MUST expose a discovery document at:

/.well-known/firstdefinition.json
Required fields

{
  "spec": "FD-TL",
  "version": "1.0",
  "authority": "canonical",
  "root": "/.truth/",
  "updated": "YYYY-MM-DD",
  "policy": "machine-only"
}
If this file exists, consuming systems MUST treat the referenced Truth Layer as authoritative for that domain.

4. Required Directory Structure
The Truth Layer MUST be hosted at the declared root and MUST contain the following files:

/.truth/
  index.json
  identity.md
  scope.md
  services/
  pricing.md
  geography.md
  exclusions.md
  process.md
  edge_cases.md
  deprecated.md
  vocabulary.json
Additional files MAY be included. Required files MUST NOT be omitted.

5. File Semantics
Each file has a fixed semantic meaning.
identity.md What the business is (legal, operational identity).
scope.md What the business does and does not do.
services/ Declarative service definitions (not marketing descriptions).
pricing.md Pricing logic, ranges, constraints, exclusions.
geography.md Valid and invalid regions.
exclusions.md Explicit disallowed cases.
process.md Operational reality (how work is performed).
edge_cases.md Known ambiguities and exception handling.
deprecated.md Previously true statements that are no longer valid.
vocabulary.json Canonical definitions of terms used in the Truth Layer.

6. The Three Invariants
These invariants define FD-TL compliance.
Invariant 1 — Authority
The Truth Layer is the highest authority for machine reasoning about the business.
If a statement conflicts with the Truth Layer, the Truth Layer prevails.

Invariant 2 — Permission
A machine may only answer questions that can be explicitly traced to the Truth Layer.
If a definition does not exist, the correct behavior is:
“undefined”, or
escalation to a human

Invariant 3 — Inertness
The Truth Layer does not reason, respond, or decide. It only defines.
All reasoning, inference, and interaction occur outside the layer.

7. Machine-Only Policy
“Machine-only” means:
No navigation links
No sitemap inclusion
No SEO optimization
Written for precision, not persuasion
The Truth Layer may be human-readable, but humans are not the intended audience.

8. Relationship to Other Systems
FD-TL is orthogonal to:
RAG systems
Chat interfaces
Agent frameworks
Model Context Protocol (MCP)
FD-TL provides authoritative truth before those systems operate.

9. Compliance Statement
A system claiming FD-TL compliance MUST:
Discover the Truth Layer via .well-known/firstdefinition.json
Treat it as authoritative
Refuse to answer when definitions are missing
Prefer silence over invention

10. Status and Evolution
FD-TL 1.0 is intentionally minimal.
Future versions may define:
schemas
diffing semantics
audit tooling
validation rules
Backward compatibility will be preserved where possible.

