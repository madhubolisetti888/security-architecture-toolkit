Blast Radius Assessment

A practical framework for determining how far an attacker can move after compromising an identity, application, API, workload, or infrastructure component.

Why Blast Radius Matters

Security controls cannot guarantee that compromise will never occur.

A resilient architecture therefore asks a second question:

If this component is compromised, what can the attacker reach?

NIST Zero Trust Architecture emphasizes protecting resources through granular access decisions and least privilege rather than relying on implicit trust based on network location. (NIST Publications)

The objective of blast-radius analysis is to understand and reduce the consequences of compromise.

⸻

1. Identify the Compromise Point

Start with the component that has been compromised.

Examples:

* Human identity
* Privileged identity
* API credential
* Service account
* Workload identity
* Application
* API
* Container
* Virtual machine
* Cloud account
* Third-party integration

Example:

Compromised Workload
        ↓
What can it access?
        ↓
What can it invoke?
        ↓
What can it modify?

⸻

2. Map Direct Access

Identify everything the compromised component can directly access.

Compromised Identity
      |
      +---- API A
      |
      +---- Database A
      |
      +---- Storage A
      |
      +---- Service B

Review:

* Read permissions
* Write permissions
* Delete permissions
* Administrative permissions
* API permissions
* Network connectivity
* Cloud permissions

⸻

3. Map Indirect Access

Direct permissions are only part of the problem.

Ask:

What can this component reach through another component?

Example:

Compromised Service A
        ↓
Service B
        ↓
Service C
        ↓
Database
        ↓
Sensitive Data

This is where attack-path analysis becomes important.

⸻

4. Evaluate Trust Boundaries

Identify every boundary the compromised component can cross.

User Environment
       ↓
Application
       ↓
Internal Service
       ↓
Cloud Resource
       ↓
Production Data

Ask:

* Is each boundary explicitly enforced?
* Is identity re-evaluated?
* Is authorization performed?
* Can the boundary be bypassed?
* Is network location being treated as implicit trust?

NIST Zero Trust Architecture specifically rejects implicit trust based solely on network or physical location. (NIST)

⸻

5. Evaluate Privilege

Determine whether compromise enables privilege escalation.

Look for:

* Excessive permissions
* Privileged roles
* Administrative APIs
* Role-assignment capabilities
* Credential-management permissions
* Cloud control-plane access
* Ability to modify security controls

A useful question is:

Can the compromised identity grant itself or another identity additional access?

⸻

6. Evaluate Data Exposure

Determine how much sensitive information can be reached.

Consider:

* Customer data
* Credentials
* Tokens
* Personal information
* Financial data
* Intellectual property
* Security configuration
* Production data

Example:

Compromised API
      ↓
Customer Database
      ↓
10 Million Records

The number and sensitivity of accessible records can dramatically change the impact of compromise.

⸻

7. Evaluate Lateral Movement

Determine which systems the compromised component can communicate with.

Compromised Server
       |
       +---- Server A
       |
       +---- Server B
       |
       +---- Admin Service
       |
       +---- Database
       |
       +---- Cloud Control Plane

Broad connectivity increases potential blast radius.

Segmentation and explicit authorization can reduce the number of reachable resources.

⸻

8. Evaluate Identity Propagation

Modern architectures frequently propagate identity across services.

Example:

User
 ↓
Application
 ↓
API
 ↓
Service
 ↓
Cloud Resource

Ask:

* Is the original identity propagated?
* Is a new workload identity used?
* Are permissions inherited unnecessarily?
* Can a compromised service impersonate another identity?
* Are downstream permissions independently evaluated?

⸻

9. Evaluate Credential Lifetime

Credential lifetime can affect containment.

Consider:

* Token lifetime
* Session lifetime
* API key lifetime
* Certificate lifetime
* Service credential lifetime
* Refresh-token lifetime

Shorter-lived credentials can reduce the useful lifetime of stolen credentials, but lifecycle design must also include effective revocation and detection.

⸻

10. Detection Boundary

Ask:

Where would we notice the attacker moving through the architecture?

Monitor:

* Authentication
* Authorization
* Privilege changes
* API activity
* Service-to-service communication
* Data access
* Administrative activity
* Credential changes

Example:

Compromise
    ↓
Authentication Event
    ↓
Unusual API Access
    ↓
Privilege Attempt
    ↓
Sensitive Data Access
    ↓
Detection
    ↓
Containment

⸻

11. Containment

Design explicit mechanisms to reduce blast radius after detection.

Examples:

* Disable identity
* Revoke sessions
* Revoke credentials
* Isolate workload
* Block network path
* Remove privileges
* Quarantine resource
* Rotate secrets
* Restrict API access

The architecture should not depend entirely on manual intervention.

⸻

12. Blast Radius Assessment Matrix

Dimension	Low	Medium	High
Identity permissions	Narrow	Multiple resources	Broad enterprise access
Data access	Limited	Sensitive data	Large-scale sensitive data
Network reach	Isolated	Several services	Broad connectivity
Privilege	Standard	Elevated	Administrative
Credential lifetime	Short	Moderate	Long-lived
Lateral movement	Difficult	Possible	Easy
Detection	Strong	Partial	Limited
Recovery	Fast	Moderate	Difficult

The exact thresholds should be adapted to the organization’s risk model.

⸻

13. Architecture Questions

1. What happens if this identity is compromised?
2. What resources can it directly access?
3. What resources can it indirectly reach?
4. Which trust boundaries can it cross?
5. Can it move laterally?
6. Can it escalate privileges?
7. Can it access sensitive data?
8. Can it modify security controls?
9. How long can stolen credentials remain useful?
10. Where will the compromise be detected?
11. How quickly can access be revoked?
12. What is the maximum realistic blast radius?

⸻

Blast Radius Model

                 Compromise
                     |
                     v
                  Identity
                     |
             +-------+-------+
             |               |
             v               v
          Direct          Indirect
          Access           Access
             |               |
             +-------+-------+
                     |
                     v
              Trust Boundaries
                     |
                     v
             Lateral Movement
                     |
                     v
                  Privilege
                     |
                     v
                Data / Systems
                     |
                     v
                  Impact

⸻

Core Principle

Security architecture should assume that some controls will eventually fail.

The goal is therefore not only:

Prevent compromise.

It is also:

Limit what compromise can become.

A resilient architecture makes every compromised identity, workload, service, and application a contained event rather than a platform-wide failure.

That is the essence of designing for limited blast radius.