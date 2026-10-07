Security Boundary Assessment

A practical framework for evaluating whether security boundaries are correctly defined and enforced within an architecture.

Core Principle

A security boundary defines where trust, authority, data, privileges, or administrative control changes.

A boundary should not exist simply because two components are on different networks.

The key question is:

What trust relationship exists across this boundary, and what happens if that trust is compromised?

⸻

1. Identify Security Domains

Document the major security domains within the system.

Examples:

* User identity domain
* Privileged identity domain
* Application domain
* API domain
* Workload domain
* Data domain
* Management domain
* Third-party domain
* Cloud control-plane domain

For each domain, document:

* Assets
* Identities
* Privileges
* Data sensitivity
* Administrative authority
* Security requirements

⸻

2. Identify Trust Relationships

For every connection between domains, determine:

* Who trusts whom?
* What evidence establishes trust?
* Is authentication required?
* Is authorization evaluated independently?
* What attributes influence the decision?
* Is the trust permanent or session-based?
* Can the trust be delegated?

Do not treat connectivity as trust.

⸻

3. Analyze What Crosses the Boundary

Document what crosses each boundary:

* Identity
* Authentication credentials
* Tokens
* Authorization decisions
* Data
* Commands
* Administrative privileges
* Service-to-service requests
* Secrets

For each item, determine whether it is:

* Required
* Minimized
* Validated
* Logged
* Revocable
* Time-limited

⸻

4. Identify Boundary Enforcement Points

Examples include:

* Identity provider
* Policy enforcement point
* API gateway
* Service mesh
* Network segmentation
* Database authorization
* Application authorization
* Privileged access management
* Data access controls

A boundary without an enforcement mechanism may only be a conceptual boundary.

⸻

5. Test Compromise Scenarios

For each important boundary, ask:

Scenario A — Identity Compromise

If an identity crossing the boundary is compromised:

* What can it access?
* Can privileges be escalated?
* Can the attacker move laterally?
* How quickly can access be revoked?

Scenario B — Workload Compromise

If a workload is compromised:

* Which services can it call?
* Which credentials can it access?
* Which data can it reach?
* Can it access management interfaces?

Scenario C — Control Failure

If the primary enforcement control fails:

* Is access denied?
* Does the system fail open?
* Is there a compensating control?
* What is the resulting blast radius?

⸻

6. Boundary Review Matrix

Boundary	Trust Relationship	Data/Authority Crossing	Enforcement	Failure Impact
User → Application	User to application	User identity/session	IAM + application authz	Account compromise
API → Service	Service invocation	Token + request	API/service authorization	Service compromise
Service → Database	Workload to data	Query + data	DB/application authorization	Data exposure
Admin → Control Plane	Privileged access	Administrative authority	PAM + MFA + policy	Platform compromise
Cloud → Third Party	External trust	Data/API access	Federation + API controls	Third-party compromise

⸻

7. Architecture Review Questions

1. Where are the security domains?
2. Where do trust relationships change?
3. What authority crosses each boundary?
4. What data crosses each boundary?
5. Who or what enforces the boundary?
6. Can the boundary be bypassed?
7. What happens if the enforcement point is compromised?
8. Can compromised identities move across the boundary?
9. Is access more privileged than necessary?
10. What is the maximum blast radius of boundary failure?

⸻

Security Architecture Model

Identity
   ↓
Authentication
   ↓
Context
   ↓
Policy
   ↓
Authorization
   ↓
Security Boundary
   ↓
Resource / Service
   ↓
Data
          ↓
      Telemetry
          ↓
Detection / Response

Core Principle

A security boundary should do more than separate components.

It should limit trust, constrain authority, protect sensitive resources, and contain compromise.

The objective is not to eliminate every trust relationship.

The objective is to make every important trust relationship:

* Explicit
* Necessary
* Enforced
* Observable
* Revocable
* Bounded

Design the boundary before you design the control.

Reference: NIST SP 800-160 Vol. 1 Rev. 1 — Engineering Trustworthy Secure Systems