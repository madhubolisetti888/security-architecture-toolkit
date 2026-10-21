Security Policy and Enforcement Assessment

Purpose

Assess whether security policies are governed, correctly enforced, and supported by sufficient evidence for verification and incident investigation.

1. Architecture context

* System or service:
* Architecture owner:
* Review date:
* Critical assets:
* Trust boundaries:
* Applicable security policies:
* Relevant architecture diagrams:

2. Policy governance

Review question	Evidence to request	Finding
Is each critical policy owned by an accountable team?	Policy ownership and approval records	
Are policy changes authorized and traceable?	Change records and audit logs	
Are exceptions documented with expiry or review criteria?	Exception register	
Are conflicting policies identified and resolved?	Policy analysis and test results	
Can incorrect policy changes be rolled back?	Recovery procedure and test evidence	

3. Decision and enforcement

Review question	Evidence to request	Finding
Is the decision-making responsibility explicit?	Architecture diagram and component responsibilities	
Is enforcement performed at the appropriate trust boundary?	Request-flow analysis and tests	
Are sensitive resources protected by resource-level authorization where required?	Authorization tests	
Can alternate routes bypass mandatory controls?	Route inventory and bypass testing	
Are workload and service identities constrained to their intended scope?	Permissions and identity configuration	
Is failure behavior documented for critical dependencies?	Failure-mode analysis and test results	

4. Observability and evidence

Review question	Evidence to request	Finding
Are important access decisions recorded?	Representative event samples	
Do events include sufficient actor, action, resource, outcome, and time context?	Log schema and samples	
Can events be correlated across relevant services?	Trace or correlation examples	
Are privileged actions and policy changes auditable?	Audit records	
Are logging gaps and monitoring failures detected?	Monitoring configuration and test evidence	

Collect only the information needed for security and operational purposes. Protect sensitive logs and apply appropriate access, retention, and privacy controls.

5. Failure scenarios

For each scenario, document the expected behavior, actual behavior, evidence, owner, and residual risk.

* Policy decision service unavailable
* Stale or incorrect policy configuration
* Enforcement point bypassed
* Authenticated user attempts unauthorized resource access
* Workload identity compromised
* Logging or event delivery unavailable
* Emergency exception remains active beyond its intended period

6. Findings register

ID	Finding	Severity	Evidence	Owner	Remediation
F-01					
F-02					
F-03					

Use the organization’s approved severity and risk-rating methodology.

7. Review outcome

* Decision: Approved / Approved with conditions / Rejected / Deferred
* Critical gaps:
* Required remediation:
* Compensating controls:
* Residual risk and risk owner:
* Validation plan:
* Next review trigger:

Completion criteria

The review should establish who owns the policy, where it is enforced, how bypass and failure scenarios are handled, and what evidence demonstrates effectiveness.

A documented policy is intent. A tested enforcement point is implementation. Verifiable evidence supports assurance.