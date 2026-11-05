Security Architecture Effectiveness Measurement Framework

1. Purpose

Use this framework to define, track, and improve the effectiveness of security architecture capabilities.

The framework connects business risk, architecture decisions, control implementation, and measurable outcomes.

2. Measurement principles

* Measure outcomes, not only implementation activity.
* Tie every metric to a defined risk or architecture objective.
* Establish a baseline before setting a target.
* Use verifiable evidence and documented data sources.
* Assign an accountable metric owner.
* Review trends and exceptions, not just point-in-time scores.
* Define corrective actions for missed targets.

3. Security capability scorecard

Capability	Example metric	Evidence source
Identity security	Time to revoke compromised access	IAM logs and incident records
Privileged access	Percentage of privileged identities under governance	PAM and identity inventory
Application security	Critical applications with completed architecture reviews	Architecture review register
API security	Critical APIs with verified authorization controls	API inventory and test evidence
Cloud security	Critical misconfigurations beyond remediation SLA	Cloud security posture platform
Detection	Mean time to detect relevant incidents	SIEM and incident records
Incident response	Mean time to contain incidents	Incident management platform
Resilience	Recovery tests meeting agreed RTO/RPO	Disaster recovery test reports

4. Metric definition template

For every metric, document:

* Metric name:
* Business risk addressed:
* Architecture objective:
* Metric definition:
* Calculation method:
* Measurement unit:
* Baseline:
* Target:
* Data source:
* Accountable owner:
* Reporting frequency:
* Threshold / escalation criteria:
* Corrective action:
* Known limitations:

5. Example metric: compromised-access revocation

Objective: Reduce the period during which compromised identities retain access.

Definition: Elapsed time between confirmed compromise notification and verified revocation of the affected identity’s relevant access.

Recommended reporting:

* Median revocation time.
* 90th percentile revocation time.
* Percentage completed within the approved SLA.
* Number of failed or incomplete revocations.

Evidence: Identity platform audit logs, application access records, incident timestamps, and revocation verification.

Important: Define the start and end events consistently. A successful disablement in the identity provider does not automatically prove that all downstream sessions, tokens, and application permissions have been invalidated.

6. Architecture review checklist

* [ ]	Is each metric linked to a business risk?
* [ ]	Is the metric definition unambiguous?
* [ ]	Is a baseline available?
* [ ]	Is the target risk-based and approved?
* [ ]	Is the evidence source reliable?
* [ ]	Is the owner accountable for the outcome?
* [ ]	Is the reporting frequency defined?
* [ ]	Are exceptions and outliers visible?
* [ ]	Is there a corrective-action process?
* [ ]	Are metrics periodically reviewed for relevance?

7. Governance

Review metrics at an agreed cadence based on system criticality and risk. Escalate sustained deterioration, missed targets, unreliable evidence, and material changes to the underlying architecture.

Expected result: A measurable feedback loop that demonstrates whether security architecture is delivering its intended outcomes.

This framework is a starting point. Tailor metric definitions, targets, and thresholds to the organization’s risk appetite, system criticality, and regulatory obligations.