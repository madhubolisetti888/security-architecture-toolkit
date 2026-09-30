Multi-Cloud Security Architecture

Purpose

Multi-cloud security introduces a different architectural challenge from securing a single cloud environment.

The objective is not necessarily to make every cloud implementation identical.

The objective is to establish consistent security principles and security outcomes while allowing each cloud platform to use its native capabilities.

⸻

Architecture Model

                    ┌─────────────────────┐
                    │ Enterprise Identity │
                    └──────────┬──────────┘
                               │
                         Authentication
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Policy /            │
                    │ Authorization Model │
                    └──────────┬──────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
        ┌──────────┐     ┌──────────┐     ┌──────────┐
        │ Cloud A  │     │ Cloud B  │     │ Cloud C  │
        │          │     │          │     │          │
        │ IAM      │     │ IAM      │     │ IAM      │
        │ Workload │     │ Workload │     │ Workload │
        │ Identity │     │ Identity │     │ Identity │
        └────┬─────┘     └────┬─────┘     └────┬─────┘
             │                │                │
             └────────────────┼────────────────┘
                              │
                         Telemetry
                              │
                              ▼
                    ┌─────────────────────┐
                    │ Detection / SIEM    │
                    └─────────────────────┘

⸻

1. Identity Consistency

Identify the enterprise identities that need access across cloud environments.

Examples:

* Employees
* Administrators
* Developers
* Applications
* Workloads
* Automation
* CI/CD pipelines
* Third-party services

Questions

* Is there a consistent enterprise identity model?
* How is federation implemented?
* How are privileged identities managed?
* Are workload identities unique?
* Can identities be revoked consistently?

⸻

2. Authorization Model

Cloud providers may implement authorization differently.

Define the enterprise security principle first.

Examples:

Enterprise Principle
        ↓
Least Privilege
        ↓
Cloud A Policy
Cloud B Policy
Cloud C Policy

The implementation may differ.

The security intent should remain consistent.

Questions

* What is the enterprise authorization model?
* Which permissions are standardized?
* Which permissions are cloud-specific?
* How are exceptions governed?

⸻

3. Workload Identity

Cross-cloud applications introduce workload-to-workload trust.

Example:

Cloud A
Application
    │
    │ Workload Identity
    ▼
Cloud B
API
    │
    │ Authorization
    ▼
Cloud B
Database

Questions

* How does the workload authenticate?
* Is identity portable across environments?
* Are long-lived credentials required?
* How are credentials rotated?
* Can the identity be revoked?

NIST SP 800-207A specifically discusses application and service identities, API gateways, sidecar proxies and identity infrastructure for cloud-native multi-cloud environments. (NIST Computer Security Resource Center)

⸻

4. Network Architecture

Review:

* Network connectivity
* Transit architecture
* Private connectivity
* Egress
* Ingress
* Segmentation
* Firewall controls
* DNS
* Cross-cloud communication

But distinguish:

Network reachability

from:

Authorization

A workload being able to reach another workload does not necessarily mean it should be allowed to use it.

⸻

5. Data Security

Identify where sensitive data exists across environments.

Evaluate:

* Data classification
* Encryption
* Key management
* Replication
* Backups
* Cross-cloud data movement
* Data access policies
* Data exfiltration controls

Key question

Can the organization maintain consistent protection for sensitive data regardless of which cloud hosts it?

⸻

6. Security Telemetry

Multi-cloud environments create fragmented telemetry.

Collect and correlate:

* Authentication events
* Authorization events
* IAM changes
* API activity
* Network activity
* Administrative actions
* Data access
* Workload activity

Conceptually:

Cloud A ──┐
Cloud B ──┼──► Common Detection Architecture
Cloud C ──┘

The goal is not necessarily identical logs.

The goal is sufficient visibility to investigate activity across trust boundaries.

⸻

7. Control Plane Security

Every cloud has a management/control plane.

Protect:

* Administrative identities
* IAM configuration
* Security configuration
* Network configuration
* Key management
* Infrastructure deployment
* Logging configuration

A compromised control-plane identity can have a substantially larger blast radius than an ordinary workload identity.

⸻

8. Standardize vs. Specialize

A useful architectural distinction:

Standardize

* Security principles
* Identity governance
* Risk classification
* Authorization concepts
* Logging requirements
* Detection objectives
* Incident response requirements

Specialize

* Cloud-native IAM implementation
* Native network controls
* Cloud-specific services
* Provider-specific security features

The goal is:

Consistent security intent without unnecessary implementation uniformity.

⸻

9. Multi-Cloud Blast Radius

Ask:

If one cloud environment is compromised, how far can the attacker move?

Evaluate:

* Cross-cloud identities
* Shared credentials
* Network connectivity
* Shared management systems
* Shared CI/CD pipelines
* Shared secrets
* Shared data
* Federated privileges

A multi-cloud strategy should not accidentally create a single identity or control-plane failure with organization-wide impact.

⸻

Architecture Review Questions

1. What identities cross cloud boundaries?
2. How are those identities authenticated?
3. How is authorization enforced?
4. Are workload identities unique?
5. Which security principles are standardized?
6. Which controls are cloud-specific?
7. What data crosses cloud boundaries?
8. How is cross-cloud communication secured?
9. Can telemetry be correlated?
10. What happens if one cloud environment is compromised?
11. Can an attacker move from one cloud to another?
12. What is the maximum cross-cloud blast radius?

⸻

Architecture Principle

Multi-cloud security should provide consistent security intent and bounded trust relationships while allowing cloud-specific implementation where appropriate.

The objective is not:

One cloud security tool everywhere.

It is:

One security architecture implemented appropriately across different cloud environments.

⸻

Final Question

If one cloud environment were compromised today, could you clearly explain which identities, resources, networks and data in the other environments remain protected—and why?