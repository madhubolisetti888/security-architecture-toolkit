Security Architecture Review — 10 Questions

A practical set of questions for evaluating security architecture during solution and design reviews.

1. What are we protecting?

Identify the critical assets.

Examples:

* Sensitive data
* Business-critical applications
* APIs
* Credentials
* Infrastructure
* Customer information
* Intellectual property

The security architecture should begin with understanding what requires protection.

2. Who or what can access it?

Identify all relevant actors:

* Human users
* Administrators
* Applications
* Services
* Workloads
* APIs
* Automation
* Third-party integrations

Do not limit the analysis to human users.

3. Where are the trust boundaries?

Identify where trust changes between:

* Users and applications
* Applications and APIs
* Workloads and services
* Internal and external systems
* Enterprise and third-party systems

Trust boundaries should be explicit rather than assumed.

4. How is identity established?

Evaluate:

* Authentication
* Identity providers
* Workload identity
* Service accounts
* Certificates
* Secrets
* Federation

The architecture should establish how identities are authenticated and managed throughout their lifecycle.

5. How is authorization enforced?

Authentication answers:

Who are you?

Authorization answers:

What are you allowed to do?

Evaluate:

* Least privilege
* Role-based access
* Attribute-based access
* Privileged access
* Context-aware authorization
* Service-to-service authorization

6. What happens if an identity is compromised?

Assume credentials or identities can eventually be compromised.

Evaluate:

* Privilege level
* Accessible systems
* Accessible data
* Session controls
* Credential rotation
* Revocation
* Monitoring

7. Can an attacker move laterally?

Evaluate whether compromise of one component allows access to additional:

* Applications
* APIs
* Workloads
* Networks
* Data stores
* Administrative interfaces

Segmentation and least privilege should reduce unnecessary lateral movement.

8. What is the potential blast radius?

Ask:

If this component is compromised, how much of the environment could be affected?

Consider:

* Identity permissions
* Network connectivity
* Data access
* Administrative privileges
* Dependency relationships

9. How will malicious activity be detected?

Security architecture should define the telemetry required for detection.

Consider:

* Authentication events
* Authorization events
* Administrative actions
* API activity
* Network activity
* Data access
* Privilege changes

10. What happens when a security control fails?

Do not assume every control will work perfectly.

Evaluate:

* Compensating controls
* Defense in depth
* Detection
* Isolation
* Recovery
* Incident response

A resilient architecture should not depend on a single security control.

⸻

Architecture Review Principle

A security architecture review should connect:

Assets → Identity → Trust → Access → Attack Paths → Controls → Detection → Response → Resilience

The objective is not to eliminate all risk.

The objective is to understand risk and design the architecture so that compromise is difficult, detectable, containable and recoverable.