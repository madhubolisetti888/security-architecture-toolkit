API Security Architecture Review

A practical framework for reviewing the security architecture of APIs across identity, authorization, data, trust boundaries, lifecycle, and resilience.

Why API Security Is an Architecture Problem

APIs expose application functionality, data, and business operations to other systems, applications, users, and workloads.

Modern API architectures commonly connect:

User / Application
        ↓
Identity Provider
        ↓
API Gateway / Policy Enforcement
        ↓
API
        ↓
Business Logic
        ↓
Services / Databases
        ↓
Sensitive Data

Each connection represents a potential trust boundary.

NIST SP 800-228 emphasizes API protection across both pre-runtime and runtime stages of the API lifecycle. (NIST Computer Security Resource Center)

The objective is not simply to protect an API endpoint.

The objective is to ensure that every API request is:

* Authenticated
* Authorized
* Contextually evaluated where appropriate
* Limited to the intended resource and action
* Observable
* Containable if compromised

⸻

1. API Inventory

Identify:

* Public APIs
* Internal APIs
* Partner APIs
* Administrative APIs
* Service-to-service APIs
* Legacy APIs
* Shadow APIs
* Deprecated APIs
* Third-party APIs

Architecture Questions

* Do we know every API exposed by the organization?
* Who owns each API?
* Which APIs handle sensitive data?
* Which APIs are internet-facing?
* Which APIs are deprecated but still reachable?
* Are API versions tracked?

⸻

2. Authentication

Determine how API consumers establish identity.

Possible mechanisms include:

* OAuth 2.0
* OpenID Connect
* Mutual TLS
* Workload identity
* API keys
* Service credentials
* Federated identity

Architecture Questions

* Who issues the identity?
* How is the credential validated?
* How long is it valid?
* Can it be revoked?
* What happens when the credential is compromised?
* Are machine identities handled differently from human identities?

Important:

Authentication establishes identity.

It does not establish authorization.

⸻

3. Authorization

Authorization should evaluate the requested action against the intended resource.

A useful model is:

Identity
   +
Context
   +
Policy
   +
Resource
   +
Action
   ↓
Allow / Deny

Architecture Questions

* Can this identity access this resource?
* Can it perform this specific action?
* Is authorization enforced server-side?
* Is authorization evaluated for every sensitive operation?
* Are administrative functions separately protected?
* Are authorization decisions consistent across APIs?

⸻

4. Object-Level Authorization

Object-level authorization is critical when an API receives an object identifier.

Example:

GET /api/accounts/12345

The existence of a valid token does not prove that the caller can access account 12345.

The API must evaluate:

Caller Identity
       +
Requested Object
       +
Requested Action
       ↓
Authorization Decision

OWASP identifies Broken Object Level Authorization as API1:2023 and recommends authorization checks whenever user-controlled input is used to access an object. (OWASP API Security Top 10)

Architecture Questions

* Is access checked against the specific object?
* Can object IDs be manipulated?
* Are authorization checks performed in every relevant business function?
* Are authorization tests included in CI/CD?

⸻

5. Function-Level Authorization

Different API functions may require different privileges.

Example:

GET  /api/users
POST /api/users
DELETE /api/users
GET  /api/admin/audit

Authentication alone should not provide access to all functions.

Architecture Questions

* Which functions require privileged access?
* Are administrative endpoints separately protected?
* Is access denied by default?
* Are authorization checks centralized or duplicated inconsistently?
* Can a standard user invoke administrative functions?

OWASP identifies Broken Function Level Authorization as API5:2023. (OWASP API Security Top 10)

⸻

6. Object Property Authorization

Authorization may also need to happen at the property level.

Example:

{
  "name": "John",
  "email": "john@example.com",
  "role": "admin",
  "salary": 250000
}

A user may be authorized to view the object without being authorized to view every property.

Likewise, an API should not blindly bind client input to internal objects.

Architecture Questions

* Which properties can the caller read?
* Which properties can the caller modify?
* Are sensitive fields explicitly controlled?
* Are request and response schemas validated?
* Is mass assignment prevented?

OWASP’s API3:2023 specifically addresses Broken Object Property Level Authorization. (OWASP API Security Top 10)

⸻

7. API Gateway and Policy Enforcement

The API gateway can provide important controls such as:

* TLS termination
* Authentication integration
* Token validation
* Rate limiting
* Schema validation
* Routing
* Threat detection
* Request filtering
* Telemetry

However:

The API gateway should not automatically become the only authorization boundary.

Business-level authorization often belongs closer to the resource and business logic.

Architecture Principle

Use layered enforcement.

Gateway
   ↓
API
   ↓
Authorization Layer
   ↓
Business Logic
   ↓
Data Access

⸻

8. Machine-to-Machine APIs

Modern applications frequently have:

Service A
   ↓
API
   ↓
Service B
   ↓
Database

There may be no human user involved.

Therefore, API architecture must account for:

* Workload identity
* Service identity
* Credential lifecycle
* Service authorization
* Certificate/token rotation
* Service-to-service trust
* Compromise containment

Architecture Question

If Service A is compromised, what can it call?

This is a blast-radius question.

⸻

9. Sensitive Business Flows

Not every API attack involves a traditional technical vulnerability.

Some APIs expose business operations that can be abused through legitimate functionality.

Examples:

* Password reset
* Account recovery
* Financial transactions
* Bulk exports
* Coupon redemption
* Booking operations
* Privilege changes

OWASP identifies unrestricted access to sensitive business flows as API6:2023. (OWASP API Security Top 10)

Architecture Questions

* Can the operation be automated at scale?
* Are additional controls required?
* Is transaction risk evaluated?
* Are velocity and behavioral signals considered?
* Is the operation reversible?

⸻

10. API Inventory and Lifecycle

API security begins before deployment.

Review:

Design
 ↓
Development
 ↓
Testing
 ↓
Deployment
 ↓
Runtime
 ↓
Versioning
 ↓
Deprecation
 ↓
Retirement

Security controls should exist throughout this lifecycle.

Architecture Questions

* Is the API specification version controlled?
* Are security requirements part of API design?
* Are security tests automated?
* Are deprecated APIs removed?
* Is API ownership clearly defined?

⸻

11. Telemetry and Detection

API security requires visibility into:

* Authentication failures
* Authorization failures
* Token anomalies
* Privileged operations
* Unusual API usage
* Object access patterns
* Data export activity
* Administrative actions
* Service-to-service communication
* Rate/resource anomalies

Security telemetry should support:

Detect
  ↓
Investigate
  ↓
Contain
  ↓
Recover

⸻

12. Blast Radius

Ask:

If an API credential is compromised, what can the attacker reach?

Evaluate:

* API permissions
* Object access
* Function access
* Data access
* Service-to-service access
* Administrative privileges
* Network reachability
* Downstream dependencies

The objective is to keep compromise contained.

⸻

API Security Architecture Model

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
        ┌──────────┴──────────┐
        ↓                     ↓
     Resource              Action
        ↓                     ↓
        └──────────┬──────────┘
                   ↓
              API / Service
                   ↓
              Data / System
                   ↓
               Telemetry
                   ↓
        Detection / Response

⸻

API Architecture Review Questions

Before approving an API architecture, ask:

1. What identities can call this API?
2. How are those identities authenticated?
3. How is authorization enforced?
4. Can a caller access another user’s object?
5. Can a standard user invoke privileged functions?
6. Which object properties can be read or modified?
7. What happens if a token is compromised?
8. What happens if a workload identity is compromised?
9. What sensitive business operations are exposed?
10. How are APIs inventoried and retired?
11. What security telemetry is generated?
12. What is the maximum blast radius of a compromised API identity?

⸻

Core Principle

An authenticated request is not automatically an authorized request.

Secure API architecture requires explicit decisions about:

Identity
    ↓
Authentication
    ↓
Authorization
    ↓
Resource
    ↓
Action
    ↓
Trust Boundary
    ↓
Telemetry
    ↓
Response

The architectural question is not:

“Can this user call the API?”

It is:

“Should this identity be allowed to perform this action on this resource under this context?”

That is where API security becomes security architecture.