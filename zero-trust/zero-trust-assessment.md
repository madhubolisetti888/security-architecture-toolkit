Zero Trust Architecture Assessment

A practical assessment framework for identifying implicit trust and evaluating Zero Trust architecture principles.

Purpose

Zero Trust is not a single technology or product.

It is an architectural approach that reduces implicit trust and makes access decisions based on explicit signals such as identity, context, policy, device or workload posture, and resource sensitivity.

This assessment helps identify where implicit trust exists in an architecture and where additional controls may be required.

⸻

1. Identity

Questions

* Are all human users uniquely identified?
* Are workloads and services assigned distinct identities?
* Is strong authentication required for sensitive resources?
* Are privileged identities separated from standard identities?
* Can compromised identities be rapidly revoked?
* Are service accounts and machine identities governed?

Evidence

Look for:

* Identity provider
* MFA
* Workload identity
* Privileged access management
* Identity lifecycle management
* Credential rotation
* Session management

⸻

2. Device and Workload Context

Questions

* Is device posture considered during access decisions?
* Are unmanaged devices restricted?
* Are workloads authenticated independently?
* Are workload identities tied to specific services or environments?
* Can access change when device or workload posture changes?

Evidence

Look for:

* Device compliance
* Endpoint security
* Workload identity
* Certificate-based authentication
* Runtime security
* Environment classification

⸻

3. Authorization

Questions

* Is access granted based on least privilege?
* Are permissions based on business or technical requirements?
* Are privileged operations separately controlled?
* Is authorization enforced at the application/API/resource layer?
* Can access decisions incorporate context?

Evidence

Look for:

* RBAC
* ABAC
* Policy engines
* API authorization
* Privileged access controls
* Just-in-time access

⸻

4. Network and Segmentation

Questions

* Does network location automatically imply trust?
* Can workloads communicate with unnecessary systems?
* Are critical resources isolated?
* Are east-west communications controlled?
* Can a compromised workload move laterally?

Evidence

Look for:

* Network segmentation
* Microsegmentation
* Service-to-service authorization
* Firewall policies
* Security groups
* Network access policies

⸻

5. Application and API Access

Questions

* Is authentication enforced consistently?
* Is authorization performed at the API/resource level?
* Are service-to-service calls authenticated?
* Are APIs protected against unauthorized access?
* Are sensitive operations subject to additional controls?

Evidence

Look for:

* API gateways
* OAuth/OIDC
* mTLS
* Application authorization
* Rate limiting
* API monitoring

⸻

6. Data Protection

Questions

* Is access based on data sensitivity?
* Is sensitive data encrypted?
* Are data access events logged?
* Can access to sensitive data be restricted independently of network location?
* Are excessive data permissions identified?

Evidence

Look for:

* Data classification
* Encryption
* Key management
* Data access policies
* DLP
* Data activity monitoring

⸻

7. Continuous Evaluation

Questions

* Are access decisions continuously evaluated?
* Can risk changes trigger additional authentication?
* Can compromised sessions be terminated?
* Are anomalous access patterns detected?
* Are important policy decisions logged?

Evidence

Look for:

* Risk-based authentication
* Session controls
* UEBA
* SIEM
* Detection rules
* Automated response

⸻

8. Blast Radius

A Zero Trust architecture should also consider what happens when an identity, device, workload or application is compromised.

Questions

* What resources can the compromised entity access?
* Can it move laterally?
* Can it access privileged functions?
* Can it reach sensitive data?
* How quickly can access be revoked?
* What controls limit the compromise?

Assessment

Low blast radius

Compromise is isolated and access is tightly constrained.

Medium blast radius

Compromise provides access to multiple resources but additional controls limit expansion.

High blast radius

A single compromised identity, workload or system provides broad access across the environment.

⸻

Zero Trust Architecture Model

A useful architectural sequence is:

Identity -> Context -> Policy -> Authorization -> Resource -> Telemetry -> Continuous Evaluation

The objective is not to eliminate all risk.

The objective is to ensure that:

Access is explicit.
Permissions are limited.
Trust is contextual.
Activity is observable.
Compromise is containable.

⸻

Architecture Review Principle

When reviewing an architecture, ask:

Where does implicit trust exist?

Then identify:

1. The trusted relationship
2. Why that trust exists
3. What could happen if it is abused
4. What control can reduce the trust
5. How the control will be monitored
6. What happens if the control fails

This turns Zero Trust from a product initiative into an architectural discipline.

⸻

Simple Assessment Matrix

Domain	Key Question	
Identity	Is every access request tied to a known identity?
Device/Workload	Is posture considered?
Authorization	Is least privilege enforced?	
Network	Is lateral movement restricted?
Application/API	Is authorization enforced at the resource layer?	
Data	Is sensitive data independently protected?
Telemetry	Are access decisions observable?	
Continuous Evaluation	Can access change when risk changes?	
Blast Radius	Is compromise contained?	
Resilience	What happens when a control fails?

⸻

Core Principle

Zero Trust is not “never trust.”

It is:

Minimize implicit trust.
Make access explicit.
Continuously evaluate context.
Limit blast radius.
Design for compromise.