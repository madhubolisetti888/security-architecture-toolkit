Identity + Zero Trust Architecture Reference

A reference architecture showing how identity, policy, application security, workload identity and resource protection interact in a Zero Trust model.

Architecture

flowchart LR
    U[User / Device] -->|Authentication| ID[Identity Provider / IAM]
    ID --> PDP[Policy Decision Point]
    PDP -->|Authorization Decision| PEP[Policy Enforcement Point]
    PEP --> APP[Web Application / API]
    APP --> W[Workload / Service]
    W --> D[Data / Resources]
    U -.->|Telemetry| SIEM[SIEM / Security Analytics]
    ID -.->|Identity Events| SIEM
    APP -.->|Application Events| SIEM
    W -.->|Workload Events| SIEM
    D -.->|Data Access Events| SIEM
    SIEM -.->|Detection / Response| PDP

Core Components

1. User / Device

The request originates from a human user, device, application or automated process.

The architecture should establish:

* Who or what is requesting access
* What resource is being requested
* What context is associated with the request

⸻

2. Identity Provider / IAM

Identity establishes the subject making the request.

Examples include:

* Human identity
* Privileged identity
* Workload identity
* Service identity
* Machine identity
* Application identity

Identity should not be treated as synonymous with authentication.

Authentication establishes identity.

Authorization determines what that identity can do.

⸻

3. Policy Decision Point

The policy decision evaluates whether access should be permitted.

Relevant signals can include:

* Identity
* Resource
* Requested action
* Device posture
* Workload identity
* Authentication strength
* Risk
* Data sensitivity
* Environmental context

The policy should implement least privilege rather than broad implicit trust.

⸻

4. Policy Enforcement Point

The enforcement point is responsible for actually enforcing the authorization decision.

Examples can include:

* API gateway
* Application authorization layer
* Service mesh proxy
* Reverse proxy
* Cloud access control
* Resource-level authorization

NIST’s cloud-native Zero Trust guidance describes policy enforcement infrastructure as a critical part of enforcing identity-based policies at runtime. (NIST Publications)

⸻

5. Application / API

The application should not rely exclusively on network location for trust.

For example:

User
  ↓
Web Application
  ↓
API
  ↓
Service
  ↓
Database

Each important resource boundary should have appropriate authentication and authorization controls.

This is particularly important for distributed applications and microservices.

⸻

6. Workload / Service Identity

Modern applications increasingly depend on non-human identities.

Examples:

* Microservices
* Containers
* Kubernetes workloads
* Serverless functions
* CI/CD pipelines
* Service accounts
* API clients

These identities should have:

* Clear ownership
* Defined purpose
* Limited permissions
* Appropriate credential lifecycle
* Monitoring
* Revocation capability

NIST SP 800-207A specifically addresses application and service identities as part of cloud-native Zero Trust architecture. (NIST Computer Security Resource Center)

⸻

7. Data / Resources

The ultimate protection target may be:

* Database
* Files
* Object storage
* Cloud services
* Business applications
* APIs
* Infrastructure

Access should be evaluated based on the identity, resource and requested action rather than simply network location.

⸻

8. Telemetry

A Zero Trust architecture also requires visibility.

Useful telemetry includes:

* Authentication events
* Authorization decisions
* Privilege changes
* API activity
* Application activity
* Workload communication
* Data access
* Administrative actions

Telemetry supports:

Detect → Investigate → Respond → Recover

⸻

Trust Boundaries

The architecture should explicitly identify trust boundaries.

Examples:

User / Device
      ↓
Identity / Policy
      ↓
Application / API
      ↓
Workload
      ↓
Data

For every boundary, ask:

1. What is being trusted?
2. Why is it trusted?
3. How is that trust established?
4. What policy controls it?
5. Where is the policy enforced?
6. What happens if the identity is compromised?
7. What telemetry is generated?
8. How can access be revoked?

⸻

Architecture Principle

The objective is not to eliminate trust completely.

The objective is to eliminate unnecessary implicit trust.

A useful mental model is:

Identity + Context + Policy

→ Authorization

→ Resource Access

→ Telemetry

→ Continuous Evaluation

⸻

Architect’s Question

If this identity is compromised, what is the maximum blast radius?

Use this question during:

* Architecture reviews
* Threat modeling
* IAM design
* API security reviews
* Cloud architecture reviews
* Application security reviews

It connects identity architecture directly to attack-path analysis and resilience.

⸻

References

* NIST SP 800-207 — Zero Trust Architecture
* NIST SP 800-207A — Zero Trust Architecture for Cloud-Native Applications
* NIST SP 1800-35 — Implementing a Zero Trust Architecture