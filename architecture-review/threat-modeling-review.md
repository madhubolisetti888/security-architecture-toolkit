Threat Modeling — Security Architecture Review

A practical architecture-focused approach to identifying threats, attack paths, security controls, and residual risk.

Threat modeling provides a structured way to understand what can go wrong in a system and what should be done about it. OWASP describes it as a process that can be applied to applications, systems, networks, distributed systems, and business processes. (OWASP Foundation)

The objective of this review is not to produce the largest possible threat list.

The objective is to identify the important attack paths and architectural weaknesses that could materially affect the system.

⸻

1. Define the System

Start by understanding what is being built.

Document:

* Applications
* APIs
* Users
* Workloads
* Services
* Databases
* Cloud resources
* External integrations
* Administrative interfaces
* Security services

Example:

User
  |
  v
Identity Provider
  |
  v
API Gateway
  |
  v
Web Application
  |
  +------> Service A
  |          |
  |          v
  |       Database
  |
  +------> Service B
             |
             v
          External API

Review Questions

* What are we building?
* What are the critical components?
* Which components communicate with each other?
* Which components are externally reachable?

⸻

2. Identify Assets

Determine what an attacker would want to compromise.

Examples:

* Customer data
* Credentials
* Access tokens
* Personal information
* Financial information
* Intellectual property
* Administrative privileges
* Cloud resources
* Business-critical services

Review Questions

* What must be protected?
* Which assets are business-critical?
* Which assets have regulatory or contractual requirements?
* What would cause significant impact if compromised?

⸻

3. Identify Entry Points

Every attacker needs an interaction point.

Examples:

* Web applications
* APIs
* Login endpoints
* File uploads
* Administrative interfaces
* Public cloud endpoints
* Partner integrations
* Messaging systems
* CI/CD pipelines
* Remote management interfaces

Review Questions

* What is internet-facing?
* What accepts untrusted input?
* Which interfaces accept authentication credentials?
* Which interfaces perform privileged operations?

⸻

4. Identify Trust Boundaries

Trust boundaries are architectural locations where the level or nature of trust changes.

Examples:

Internet
   |
   | Trust Boundary
   v
API Gateway
   |
   | Trust Boundary
   v
Application
   |
   | Trust Boundary
   v
Internal Service
   |
   | Trust Boundary
   v
Database

Also consider:

* User → Application
* Application → API
* Service → Service
* Enterprise → Third Party
* Cloud Account → Cloud Account
* Human Identity → Privileged System
* Workload Identity → Resource

Review Questions

* Where does trust change?
* What security control enforces the boundary?
* Can the boundary be bypassed?
* What happens when an identity crossing the boundary is compromised?

⸻

5. Identify Threats

Ask:

What can go wrong?

Threat identification can use different methodologies depending on the system and organization. OWASP lists approaches including STRIDE, attack trees, PASTA, LINDDUN, OCTAVE, MITRE ATT&CK and others. (OWASP Foundation)

For architecture reviews, consider:

* Spoofing
* Tampering
* Repudiation
* Information disclosure
* Denial of service
* Elevation of privilege
* Credential compromise
* Authorization bypass
* Lateral movement
* Supply-chain compromise
* Data exfiltration

⸻

6. Build Attack Paths

Don’t stop at individual threats.

Connect them.

Example:

Compromised Identity
        |
        v
Valid Authentication
        |
        v
API Access
        |
        v
Authorization Weakness
        |
        v
Unauthorized Object Access
        |
        v
Sensitive Data

A second example:

Compromised Workload
        |
        v
Service Credential
        |
        v
Internal API
        |
        v
Excessive Service Permission
        |
        v
Database Access
        |
        v
Data Exfiltration

The attack path is often more useful to an architect than an isolated vulnerability.

⸻

7. Map Security Controls

For each important attack path, identify the controls that should disrupt it.

Example:

Threat:
Compromised user identity
        ↓
Authentication
        ↓
MFA
        ↓
Authorization
        ↓
Object-level access control
        ↓
Network / service segmentation
        ↓
Data access controls
        ↓
Telemetry
        ↓
Detection
        ↓
Response

Review Questions

* Which control prevents the attack?
* Which control detects it?
* Which control limits impact?
* Are controls independent?
* What happens if one control fails?

⸻

8. Evaluate Blast Radius

Ask:

If the attacker succeeds, how far can they go?

Evaluate:

* Identity permissions
* API permissions
* Network connectivity
* Service permissions
* Data access
* Administrative privileges
* Cloud permissions
* Third-party access

Example:

Compromised Identity
        |
        +--> API A
        |
        +--> Database A
        |
        +--> Admin API
        |
        +--> Cloud Control Plane

If one compromised identity reaches all of these resources, the architecture has a potentially large blast radius.

⸻

9. Detection and Response

Threat modeling should consider what happens after preventive controls fail.

Identify:

* Authentication telemetry
* Authorization failures
* Privilege changes
* API anomalies
* Service-to-service activity
* Data access
* Administrative actions
* Credential changes

Architecture should support:

Detect
  ↓
Investigate
  ↓
Contain
  ↓
Recover

⸻

10. Residual Risk

Not every threat can necessarily be eliminated.

For each significant threat, document:

Threat
↓
Impact
↓
Existing Controls
↓
Control Gaps
↓
Residual Risk
↓
Decision

Possible decisions may include:

* Mitigate
* Eliminate
* Transfer
* Accept

OWASP describes threat modeling as a way to support informed security-risk decisions rather than simply generating a list of vulnerabilities. (OWASP Foundation)

⸻

11. Threat Model Review Triggers

Threat models should evolve with the architecture.

Revisit the model when there is a significant change such as:

* New application
* New API
* New data flow
* New trust boundary
* New external integration
* New workload
* New authentication mechanism
* New privileged function
* Major infrastructure change
* Security incident

OWASP recommends continuous refinement as systems evolve because new architectural and implementation details can introduce new attack vectors. (OWASP Community)

⸻

Security Architecture Threat Modeling Flow

System
  ↓
Assets
  ↓
Entry Points
  ↓
Trust Boundaries
  ↓
Threats
  ↓
Attack Paths
  ↓
Security Controls
  ↓
Residual Risk
  ↓
Detection
  ↓
Response
  ↓
Recovery

⸻

Architecture Review Questions

1. What are we protecting?
2. Who or what can interact with it?
3. Where are the entry points?
4. Where are the trust boundaries?
5. What identities cross those boundaries?
6. What can go wrong?
7. What are the realistic attack paths?
8. Which controls interrupt those paths?
9. What happens if a control fails?
10. What is the maximum blast radius?
11. How would we detect the attack?
12. How would we contain and recover from it?

⸻

Core Principle

Threat modeling is architecture under an adversarial lens.

A good threat model should help the team answer:

If an attacker compromises one part of this architecture, what can they reach next — and which controls stop them?

That question turns a static architecture diagram into an attack-path model.

And that is where threat modeling becomes useful to the security architect.