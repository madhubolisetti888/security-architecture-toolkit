Security Architecture Trade-off Assessment

Purpose

Evaluate architectural alternatives against security requirements, business constraints, operational needs, and residual risk.

1. Decision Context

* Decision title:
* System or capability:
* Decision owner:
* Date:
* Stakeholders:
* Business objective:
* Constraints and assumptions:

2. Mandatory Requirements

Document requirements that must not be silently traded away.

* [ ]	Confidentiality requirements identified
* [ ]	Integrity requirements identified
* [ ]	Availability requirements identified
* [ ]	Authentication and authorization requirements identified
* [ ]	Regulatory and contractual requirements identified
* [ ]	Performance and latency targets documented
* [ ]	Recovery requirements documented

3. Threat and Failure Analysis

* [ ]	Relevant threats identified
* [ ]	Trust boundaries documented
* [ ]	Failure modes assessed
* [ ]	Privilege escalation considered
* [ ]	Blast radius evaluated
* [ ]	Detection and response requirements considered
* [ ]	Dependencies and single points of failure identified

4. Alternatives

For each alternative, document:

Attribute	Alternative A	Alternative B	Alternative C
Security effectiveness	Assess	Assess	Assess
Performance	Assess	Assess	Assess
Availability	Assess	Assess	Assess
Operational complexity	Assess	Assess	Assess
Cost	Assess	Assess	Assess
Failure behavior	Assess	Assess	Assess
Residual risk	Assess	Assess	Assess

Use measured evidence where available. Do not treat unverified assumptions as established facts.

5. Decision Rationale

* Selected alternative:
* Why it satisfies mandatory requirements:
* Benefits:
* Disadvantages:
* Alternatives rejected and reasons:
* Supporting evidence:
* Compensating controls:

6. Residual Risk

For each remaining risk, record:

* Risk description:
* Likelihood and impact assessment:
* Existing mitigations:
* Additional treatment required:
* Risk owner:
* Formal acceptance authority:
* Review date or trigger:

7. Validation Plan

* [ ]	Security tests defined
* [ ]	Performance tests defined
* [ ]	Failure-mode tests defined
* [ ]	Availability behavior validated
* [ ]	Monitoring requirements validated
* [ ]	Operational ownership confirmed
* [ ]	Decision review triggers established

8. Review Triggers

Revisit the decision when:

* Threat assumptions change
* Business requirements change
* Performance or availability targets change
* A material security incident occurs
* A key dependency changes
* Compensating controls become ineffective
* New evidence invalidates the original rationale

Final Principle

A defensible architecture decision documents what was chosen, why it was chosen, what was rejected, and what risk remains.