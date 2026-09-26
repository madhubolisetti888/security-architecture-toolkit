Machine Identity Architecture Review

Purpose

Modern applications depend heavily on non-human identities.

Applications, APIs, services, workloads, automation pipelines, containers and cloud resources may all require identities to communicate with other resources.

Machine identity should therefore be treated as an architectural security boundary.

The objective is to ensure that every non-human identity is:

* uniquely identifiable
* strongly authenticated
* appropriately authorized
* governed throughout its lifecycle
* monitored
* revocable
* constrained to an appropriate blast radius

⸻

1. Machine Identity Inventory

Identify all non-human identities in the architecture.

Examples:

* Application identities
* Service identities
* Workload identities
* API identities
* Service accounts
* Cloud workload identities
* Automation identities
* CI/CD identities
* Database/service credentials
* Certificates
* API keys
* Tokens

Architecture questions

* What non-human identities exist?
* Which applications own them?
* Which systems depend on them?
* Are any identities shared?
* Are there unmanaged credentials?

⸻

2. Identity Establishment

Determine how a workload or service establishes its identity.

Examples:

* Certificates
* Short-lived tokens
* Workload identity systems
* Cloud-native workload identities
* Service mesh identity
* Federated identity
* Managed identities

Questions

* Who issues the identity?
* How is the identity protected?
* Can the identity be spoofed?
* How is identity authenticity verified?
* Is identity cryptographically verifiable?

⸻

3. Authentication

Authentication should establish that the workload is actually the identity it claims to be.

Questions

* How does Service A authenticate to Service B?
* Is mutual authentication required?
* Are long-lived secrets being used?
* Are tokens short-lived?
* How are certificates or credentials rotated?
* Can compromised credentials be revoked?

⸻

4. Authorization

Authentication answers:

Who are you?

Authorization answers:

What are you allowed to do?

Evaluate:

* Service-to-service authorization
* API authorization
* Resource-level authorization
* Least privilege
* RBAC
* ABAC
* Policy-based authorization
* Privileged operations

A valid workload identity should not automatically receive broad access.

⸻

5. Machine Identity Lifecycle

Review the complete identity lifecycle:

Create
  ↓
Register
  ↓
Authenticate
  ↓
Authorize
  ↓
Rotate
  ↓
Monitor
  ↓
Revoke
  ↓
Retire

Questions

* How are identities created?
* Who owns them?
* How are changes approved?
* How are credentials rotated?
* What happens when a workload is deleted?
* How quickly can an identity be revoked?

⸻

6. Blast Radius

For every important machine identity, determine:

If this identity is compromised, what can the attacker reach?

Evaluate:

* APIs
* Databases
* Cloud resources
* Secrets
* Other workloads
* Administrative interfaces
* Production systems
* Sensitive data

The objective is to prevent one compromised workload identity from becoming a pathway to broad lateral movement.

⸻

7. Trust Boundaries

Document where machine identities cross trust boundaries.

Example:

Application
     │
     │ Workload Identity
     ▼
API Gateway
     │
     │ Authorization
     ▼
Service A
     │
     │ Service Identity
     ▼
Service B
     │
     │ Resource Authorization
     ▼
Database

Every transition should have an explicit security decision.

⸻

8. Monitoring and Detection

Machine identity activity should be observable.

Monitor:

* Authentication failures
* Token usage
* Certificate events
* Authorization failures
* Unusual service-to-service communication
* Privilege changes
* New machine identities
* Identity lifecycle events
* Unexpected access to sensitive resources

The goal is not only to prevent unauthorized access, but also to detect compromised identities.

⸻

9. Architecture Review Questions

Before approving an architecture, ask:

1. What machine identities exist?
2. Who owns each identity?
3. How is each identity established?
4. How is identity authenticity verified?
5. Where is authorization enforced?
6. Are privileges scoped to the minimum required?
7. Are credentials short-lived where possible?
8. How are identities rotated?
9. How are identities revoked?
10. What happens if one machine identity is compromised?
11. Can the compromised identity move laterally?
12. Is machine identity activity observable?

⸻

Architecture Principle

Every workload that communicates with another resource should have an explicit and verifiable identity, an explicit authorization decision, and a bounded blast radius.

Zero Trust therefore applies not only to:

User → Application

but also to:

Application → API

Service → Service

Workload → Database

Automation → Cloud Resource

Agent → Tool / API

Machine identity is becoming a fundamental part of identity-centric security architecture.

References

* NIST SP 800-207 — Zero Trust Architecture
* NIST SP 800-207A — Zero Trust Architecture Model for Cloud-Native Applications