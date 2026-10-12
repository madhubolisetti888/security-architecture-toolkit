Security Resilience Assessment

Purpose

Evaluate whether a system can anticipate cyber threats, withstand compromise, contain damage, restore trusted operations, and adapt after an incident.

This assessment is informed by NIST SP 800-160 Vol. 2 Rev. 1.

1. Critical Business Functions

Document:

* Critical business services
* Essential application components
* Sensitive data and supporting systems
* Availability and recovery requirements
* Dependencies that could disrupt operations

2. Anticipate

* [ ]	Critical assets and dependencies are documented.
* [ ]	Threat models include identity and workload compromise.
* [ ]	High-impact attack paths have been identified.
* [ ]	Single points of failure are understood.
* [ ]	Recovery dependencies are included in the threat model.

3. Withstand

* [ ]	Least privilege is enforced.
* [ ]	Security boundaries limit lateral movement.
* [ ]	Critical services are isolated where appropriate.
* [ ]	Independent authorization controls protect sensitive resources.
* [ ]	Essential functions have defined degraded operating modes.
* [ ]	Compromise of one workload does not automatically grant broad access.

4. Recover

* [ ]	Incident containment procedures are documented.
* [ ]	Credential, token, and key revocation procedures are tested.
* [ ]	Backup integrity can be verified.
* [ ]	Rebuild artifacts and configurations are protected.
* [ ]	Recovery procedures include identity and privilege validation.
* [ ]	Return-to-service criteria include security validation.
* [ ]	Recovery exercises validate business and security requirements.

5. Adapt

* [ ]	Incident findings feed into architecture reviews.
* [ ]	Material changes trigger threat-model updates.
* [ ]	Security exceptions and residual risks have owners.
* [ ]	Recovery exercises result in tracked improvements.
* [ ]	Architecture decisions are reviewed when assumptions change.

6. Resilience Scenarios

For each scenario, record the expected response and evidence.

Scenario	Required outcome
Compromised service identity	Restrict access and revoke identity
Compromised application workload	Isolate workload and limit lateral movement
Identity provider disruption	Apply documented, secure continuity procedures
Ransomware or destructive activity	Contain impact and recover verified systems
Compromised administrative account	Revoke access and validate control-plane integrity
Critical third-party outage	Maintain or safely degrade essential functions

7. Resilience Metrics

Record target and observed values where applicable.

Metric	Target	Observed	Evidence
Workload isolation time	Define	Measure	Exercise/incident
Credential revocation time	Define	Measure	Test results
Recovery time objective	Define	Measure	Recovery exercise
Recovery point objective	Define	Measure	Recovery exercise
Trusted restoration validation	Define	Measure	Validation records

8. Findings and Remediation

For each gap, document:

* Finding
* Business impact
* Threat scenario
* Recommended architectural change
* Responsible owner
* Target date
* Residual risk
* Validation evidence

Final Architecture Review Question

If a critical component is compromised, can the organization contain the incident, preserve essential business functions where feasible, and restore trusted operations?

The objective is not to promise that compromise will never happen.

The objective is to make compromise survivable, bounded, and recoverable.

Reference: NIST SP 800-160 Vol. 2 Rev. 1, Developing Cyber-Resilient Systems: A Systems Security Engineering Approach.