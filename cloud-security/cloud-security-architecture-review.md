Cloud Security Architecture Review

Purpose

Cloud security should be evaluated as an architectural problem rather than as a collection of individual security configurations.

A cloud environment typically contains:

* Human identities
* Privileged identities
* Workload identities
* Applications
* APIs
* Cloud services
* Networks
* Data stores
* Secrets
* Management/control planes
* Third-party integrations

The security architecture should define how these components interact and where trust is established, constrained and monitored.

⸻

Architecture Model

                    ┌─────────────────┐
                    │ Human / External│
                    │     Identity    │
                    └────────┬────────┘
                             │
                       Authentication
                             │
                             ▼
                    ┌─────────────────┐
                    │ Identity / IAM  │
                    └────────┬────────┘
                             │
                       Authorization
                             │
                             ▼
                    ┌─────────────────┐
                    │ Application /   │
                    │      API        │
                    └────────┬────────┘
                             │
                     Workload Identity
                             │
                             ▼
                    ┌─────────────────┐
                    │ Cloud Workload  │
                    └────────┬────────┘
                             │
                       Resource Access
                             │
                             ▼
                    ┌─────────────────┐
                    │ Data / Cloud    │
                    │    Resource     │
                    └─────────────────┘
              ──────── Telemetry / Detection ────────►

⸻

1. Identity Architecture

Identify every identity that can access cloud resources.

Human identities

* Employees
* Administrators
* Developers
* Contractors
* External users

Non-human identities

* Applications
* Services
* Workloads
* Automation
* CI/CD pipelines
* Cloud service identities

Questions

* Is every identity uniquely identifiable?
* Are privileged identities separated?
* Are workload identities governed?
* Are shared credentials being used?
* Can compromised identities be revoked quickly?

⸻

2. Authentication

Determine how identities establish trust.

Evaluate:

* MFA
* Federation
* Workload identity
* Certificates
* Short-lived tokens
* Managed identities
* Service authentication

Questions

* How is the identity authenticated?
* How long does the credential remain valid?
* Can credentials be rotated?
* Can compromised credentials be revoked?

⸻

3. Authorization

Authentication alone does not establish what an identity can access.

Evaluate:

* RBAC
* ABAC
* Resource policies
* Application authorization
* API authorization
* Privileged access
* Least privilege

Questions

* What permissions does each identity have?
* Are permissions resource-specific?
* Are administrative permissions separated?
* Are unused permissions removed?

⸻

4. Network Architecture

Network controls remain important, but network reachability should not automatically imply authorization.

Review:

* VPC/VNet architecture
* Subnets
* Security groups
* Network ACLs
* Firewalls
* Private endpoints
* Egress controls
* Service-to-service communication
* Segmentation

Key question

Can an identity communicate with a resource without actually being authorized to use it?

⸻

5. Application and API Architecture

Review how applications interact with cloud resources.

User
 ↓
Identity
 ↓
Application
 ↓
API Gateway
 ↓
Service
 ↓
Cloud Resource

Evaluate:

* Authentication
* API authorization
* Service identity
* Secrets
* Token validation
* Rate limiting
* Input validation
* Service-to-service authorization

⸻

6. Data Security

Identify:

* Sensitive data
* Data stores
* Data flows
* Encryption keys
* Backup copies
* Replication
* Data exports

Questions

* Who can access the data?
* Where is authorization enforced?
* How are encryption keys managed?
* Can administrators access sensitive data?
* Is data access monitored?

⸻

7. Cloud Control Plane

The cloud management/control plane is itself a critical security boundary.

Review:

* Administrative identities
* Privileged operations
* Infrastructure changes
* IAM changes
* Policy changes
* Logging
* Emergency access
* Break-glass accounts

A compromised administrative identity can potentially affect many resources, so control-plane access should receive particular architectural attention.

⸻

8. Blast Radius

For each major identity or workload, ask:

If this identity is compromised, what can it reach?

Evaluate:

* Other workloads
* APIs
* Databases
* Storage
* Secrets
* Management interfaces
* Production environments
* Other cloud accounts/subscriptions/projects

The objective is to keep compromise bounded.

⸻

9. Detection and Telemetry

Cloud architecture should provide visibility into:

* Authentication
* Authorization
* IAM changes
* Network activity
* API calls
* Administrative operations
* Data access
* Workload behavior
* Configuration changes

Telemetry should support:

Detect → Investigate → Contain → Recover

⸻

10. Resilience

Security architecture should account for failure and compromise.

Questions:

* Can compromised credentials be revoked?
* Can workloads be isolated?
* Can secrets be rotated?
* Can infrastructure be rebuilt?
* Can access policies be restored?
* Can critical data be recovered?
* Can cloud services be operated during an incident?

⸻

Cloud Architecture Review Questions

Before approving a cloud architecture, ask:

1. What are we protecting?
2. What identities exist?
3. Where are the trust boundaries?
4. Where is authentication performed?
5. Where is authorization enforced?
6. What can communicate with what?
7. What cloud resources can each identity access?
8. What happens if a workload identity is compromised?
9. What is the maximum blast radius?
10. Can suspicious activity be detected?
11. Can compromised access be contained?
12. Can the environment recover?

⸻

Architecture Principle

Cloud security should be designed around explicit identity, authorization, trust boundaries, resource protection and bounded blast radius—not around cloud configuration alone.

NIST’s cloud security guidance emphasizes understanding the underlying technologies and security implications across the system lifecycle, including IAM, software isolation, data protection, availability and incident response. (NIST Publications)

NIST’s Zero Trust guidance similarly emphasizes protecting resources rather than treating network location as the primary security boundary. (NIST Computer Security Resource Center)

Final Question

If the cloud network disappeared tomorrow, could you still explain exactly who is authorized to access every critical resource—and why?