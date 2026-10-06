Security Architecture Decision Record

A reusable template for documenting significant security architecture decisions, trade-offs, assumptions, and residual risk.

NIST systems-security engineering guidance emphasizes evaluating security design alternatives and making trade-offs based on factors such as cost, schedule, lifecycle considerations, and assurance. (NIST Computer Security Resource Center)

⸻

1. Decision Title

Decision:

<Short description of the architecture decision>

Date:

<YYYY-MM-DD>

Status:

Proposed / Accepted / Rejected / Superseded

⸻

2. Context

Describe the problem requiring an architecture decision.

Include:

* Business context
* Technical context
* Security context
* Existing architecture
* Constraints

Example

Multiple applications require consistent authorization for sensitive customer resources while maintaining availability and acceptable latency.

⸻

3. Security Requirements

Define what the architecture must achieve.

Examples:

* Strong authentication
* Least privilege
* Resource-level authorization
* Tenant isolation
* Credential protection
* Auditability
* Resilience
* Containment

⸻

4. Assets

Identify what must be protected.

Asset:
Owner:
Sensitivity:
Business Impact:

⸻

5. Threats

Identify relevant threats.

Examples:

* Credential compromise
* Authorization bypass
* Privilege escalation
* Lateral movement
* Data exposure
* Service compromise
* Insider misuse
* Supply-chain compromise

⸻

6. Attack Paths

Document important attack paths.

Entry Point
    ↓
Identity
    ↓
Authorization
    ↓
Trust Boundary
    ↓
Resource
    ↓
Impact

⸻

7. Architecture Options

Option A

Description:

<Describe option>

Security Advantages:

Security Concerns:

Operational Impact:

⸻

Option B

Description:

<Describe option>

Security Advantages:

Security Concerns:

Operational Impact:

⸻

8. Trade-off Analysis

Dimension	Option A	Option B
Security		
Availability		
Performance		
Scalability		
Complexity		
Cost		
Operations		
Developer Experience		
Blast Radius		
Compliance		

⸻

9. Decision

Selected Option:

<Option>

Reason:

<Explain why this option was selected.>

The explanation should explicitly connect the decision to:

* Security requirements
* Threats
* Business requirements
* Technical constraints
* Operational constraints

⸻

10. Residual Risk

Document risks that remain after implementing the selected design.

Risk	Impact	Likelihood	Treatment
			
			

⸻

11. Compensating Controls

Document controls that reduce remaining risk.

Examples:

* Monitoring
* Alerting
* Segmentation
* Least privilege
* Credential rotation
* Additional authorization
* Incident response
* Backup and recovery

⸻

12. Failure Scenario

Ask:

What happens if the primary security control fails?

Document:

Control Failure
      ↓
Attacker Capability
      ↓
Reachable Resources
      ↓
Detection
      ↓
Containment
      ↓
Recovery

⸻

13. Assumptions

Document assumptions that the decision depends upon.

Examples:

* Identity provider remains available
* Authorization service is highly available
* Workload identity is correctly configured
* Logging is available
* Credentials can be revoked

⸻

14. Decision Review Trigger

Define when the decision should be revisited.

Examples:

* Major architecture change
* New external integration
* New regulatory requirement
* Security incident
* Significant threat change
* New authentication architecture
* New cloud environment
* New business capability

⸻

Architecture Decision Principle

A security architecture decision should answer:

What are we protecting?

What threats are we addressing?

What alternatives did we consider?

Why did we select this design?

What risk are we accepting?

What happens if the control fails?

A good Security Architecture Decision Record makes security trade-offs explicit, reviewable, and defensible.

The goal is not to prove that an architecture is perfect.

The goal is to prove that the decision was deliberate.