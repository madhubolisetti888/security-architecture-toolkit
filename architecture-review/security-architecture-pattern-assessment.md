Security Architecture Pattern Assessment

Purpose

Use this assessment to determine whether a security architecture pattern is appropriate for a system, whether its assumptions are valid, and whether its failure modes are understood.

This document supports architecture reviews and decision records. It does not certify that a system is secure.

1. Pattern identification

* Pattern name:
* System or service:
* Architecture owner:
* Review date:
* Business requirement:
* Security objective:
* Pattern scope:
* Relevant architecture diagram:

2. Problem and context

1. What recurring security problem does this pattern address?
2. Which assets and business processes require protection?
3. What are the trust boundaries?
4. Which identities, services, and external systems are involved?
5. What availability, performance, cost, or operational constraints apply?

3. Threat model

Threat scenario	Impact	Existing mitigation	Residual risk
Unauthorized access			
Identity or credential compromise			
Dependency failure			
Control bypass			
Privilege escalation or lateral movement			
Configuration or policy error			

Adapt these scenarios to the actual system and threat model.

4. Assumption validation

For each assumption, record how it will be validated.

Assumption	Validation method	Evidence	Status
Required identities can be authenticated			
Authorization is enforced at the resource boundary			
Policy changes are governed and traceable			
Critical dependencies meet availability requirements			
Failure behavior is defined and tested			
Security events can be investigated			

5. Failure-mode assessment

Consider what happens when:

* The pattern’s primary control is unavailable.
* A dependency is compromised.
* A policy is incorrect or outdated.
* An attacker bypasses one enforcement point.
* An emergency exception is introduced.
* The system scales or crosses a new trust boundary.

For each case, document the expected behavior, detection method, containment mechanism, recovery approach, and remaining exposure.

6. Alternatives and trade-offs

Option	Security benefits	Limitations	Operational impact	Residual risk
Proposed pattern				
Alternative A				
Alternative B				

Explain why the selected option is preferable under the stated requirements and constraints.

7. Validation plan

Define test cases before approving the pattern.

Test	Expected result	Evidence required	Owner
Unauthorized request	Denied at the appropriate enforcement point	Test result and logs	
Compromised identity scenario	Access limited to authorized scope	Access and policy evidence	
Critical dependency failure	Behavior matches the approved failure policy	Resilience test	
Policy change	Change is authorized and traceable	Audit record	
Security incident	Detection and response workflow operates as designed	Test evidence	

8. Architecture decision

* Decision: Approved / Approved with conditions / Rejected / Deferred
* Rationale:
* Mandatory controls:
* Compensating controls:
* Residual risk:
* Risk owner:
* Implementation owner:
* Review date or trigger:

9. Review triggers

Reassess the pattern when:

* The threat model changes materially.
* A trust boundary is added or removed.
* The pattern’s key dependency changes.
* A security incident exposes a failed assumption.
* Business requirements or availability targets change.
* A significant exception or compensating control is introduced.

Completion principle

A pattern should be accepted only when its purpose, assumptions, enforcement points, failure behavior, and residual risks are understood.

Do not approve a pattern merely because it is widely used. Approve it because it is appropriate for the system and its security objectives.