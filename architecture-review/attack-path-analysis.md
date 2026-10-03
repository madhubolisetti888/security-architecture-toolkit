Attack Path Analysis — Security Architecture Review

A practical framework for analyzing how an attacker could move from an initial compromise to a high-impact resource.

Why Attack Paths Matter

Security architecture reviews often identify individual weaknesses:

* Weak authentication
* Excessive permissions
* Missing segmentation
* Authorization gaps
* Exposed APIs
* Overprivileged workloads
* Weak monitoring

But individual weaknesses do not always explain the actual business impact.

An attacker may combine several weaknesses into a sequence:

Initial Access
      ↓
Compromised Identity
      ↓
API Access
      ↓
Authorization Weakness
      ↓
Lateral Movement
      ↓
Privilege Escalation
      ↓
Sensitive Resource
      ↓
Business Impact

CISA has used attack-path analysis to examine sequences of attacker activity including initial access, lateral movement, privilege escalation, collection, and exfiltration. (CISA)

The architectural objective is therefore:

Identify and disrupt the attack paths that can produce significant impact.

⸻

1. Define the Crown Jewels

Start with the resources that matter most.

Examples:

* Customer data
* Financial data
* Identity systems
* Privileged accounts
* Production databases
* Cloud control planes
* Source code
* Secrets
* Critical business services

Ask:

* What would have the greatest business impact if compromised?
* Which resources should never be directly reachable from untrusted systems?
* Which resources require multiple authorization layers?

⸻

2. Identify Entry Points

Document potential initial access paths:

* Internet-facing applications
* APIs
* Authentication endpoints
* Remote access
* Partner integrations
* SaaS integrations
* CI/CD pipelines
* Cloud services
* Workload interfaces

For each entry point:

Entry Point
    ↓
Who can reach it?
    ↓
What can they provide?
    ↓
What identity does the system establish?
    ↓
What resources become reachable?

⸻

3. Identify Identities

Attack paths increasingly depend on identity.

Consider:

* Human identities
* Privileged identities
* Service identities
* Workload identities
* Machine identities
* API identities
* Cloud identities
* Third-party identities

For each identity:

* What can it access?
* What can it modify?
* What can it invoke?
* What other identities can it influence?
* How is it revoked?
* What happens if it is compromised?

⸻

4. Map Trust Boundaries

Map every significant trust transition.

Example:

Internet
   ↓
[Trust Boundary]
   ↓
API Gateway
   ↓
[Trust Boundary]
   ↓
Application
   ↓
[Trust Boundary]
   ↓
Service
   ↓
[Trust Boundary]
   ↓
Database

Also consider:

Human → Application
Application → API
Service → Service
Cloud Account → Cloud Account
Enterprise → Third Party
Workload → Cloud Resource

⸻

5. Build the Attack Graph

Represent possible attacker movement.

Example:

Compromised User
       |
       v
     API A
       |
       v
Authorization Gap
       |
       v
    Service B
       |
       v
Excessive Permission
       |
       v
  Database C
       |
       v
Sensitive Data

This is more informative than simply recording:

“Authorization vulnerability exists.”

The attack graph tells us what that vulnerability enables.

⸻

6. Identify Chained Weaknesses

Look for combinations such as:

Weak Authentication
        +
Excessive Authorization
        +
Poor Segmentation
        +
Overprivileged Service
        =
Large Attack Path

Other examples:

Compromised Identity
        +
Long-Lived Credential
        +
Broad API Access
        =
Extended Attacker Access

Or:

Public API
        +
Authorization Bypass
        +
Sensitive Database Access
        =
Potential Data Exposure

⸻

7. Identify Control Points

For every attack path, identify where the chain can be broken.

Possible control points:

* Authentication
* Authorization
* API gateway
* Network segmentation
* Workload identity
* Privileged access controls
* Data access controls
* Runtime monitoring
* Detection
* Automated response

Example:

Compromised Identity
        ↓
Authentication
        ↓
Authorization  ← Break the path
        ↓
Service
        ↓
Database

A control is particularly valuable when it prevents an attacker from progressing to the next stage.

⸻

8. Analyze Blast Radius

Ask:

If the attacker succeeds at this stage, what can they reach next?

Classify the reachable resources:

Low
 ↓
Single Application
 ↓
Multiple Applications
 ↓
Sensitive Data
 ↓
Privileged Systems
 ↓
Enterprise Control Plane

The exact classification should be defined by organizational risk requirements.

NIST CSF 2.0 provides a broader framework for managing, assessing, prioritizing, and communicating cybersecurity risk rather than prescribing one particular control implementation. (NIST)

⸻

9. Prioritize Attack Paths

Consider:

Likelihood
    +
Reachability
    +
Privilege
    +
Asset Criticality
    +
Control Weakness
    =
Attack Path Risk

A technically possible path is not necessarily equally important to every organization.

Prioritization should consider the actual architecture and business context.

⸻

10. Detection Along the Path

Don’t only monitor the final compromise.

Look for signals at multiple stages:

Authentication
      ↓
Authorization
      ↓
API Activity
      ↓
Service Access
      ↓
Privilege Change
      ↓
Data Access
      ↓
Exfiltration

This creates multiple opportunities to detect an attack before it reaches its final objective.

⸻

11. Attack Path Mitigation

For each important path, document:

Stage	Weakness	Control	Detection
Entry	Exposed API	Gateway controls	API telemetry
Identity	Credential compromise	Strong authentication	Authentication monitoring
Authorization	Excessive permission	Least privilege	Authorization events
Movement	Broad connectivity	Segmentation	Network telemetry
Privilege	Overprivileged service	Scoped workload identity	Privilege monitoring
Data	Excessive data access	Data authorization	Data-access monitoring

The goal is not necessarily to eliminate every theoretical path.

The goal is to reduce the practical paths to high-impact resources.

⸻

12. Architecture Review Questions

1. What are the most valuable resources?
2. Where can an attacker initially enter?
3. Which identities could be compromised?
4. What can each identity reach?
5. Where are the trust boundaries?
6. Which permissions enable lateral movement?
7. Where can privilege increase?
8. Which weaknesses can be chained together?
9. Which controls break the attack path?
10. Where would we detect attacker progression?
11. What is the maximum blast radius?
12. Which attack paths deserve architectural remediation first?

⸻

Attack Path Model

Entry Point
     ↓
Identity
     ↓
Authentication
     ↓
Authorization
     ↓
Trust Boundary
     ↓
Lateral Movement
     ↓
Privilege
     ↓
Resource
     ↓
Impact
       ↑
       |
Detection / Response

Core Principle

A vulnerability is a weakness.

An attack path explains what that weakness enables.

Security architecture should therefore ask:

“If the attacker gets through this control, what can they reach next?”

And then:

“Where can we break the chain?”

That is the difference between reviewing controls individually and reviewing the architecture as an attacker would.