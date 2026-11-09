IAM, IDM and IGA Architecture Assessment

Suggested repository path: identity/iam-idm-iga-architecture-assessment.md

1. Objective

Assess whether enterprise identity management, access management, and identity governance capabilities are properly defined and integrated.

2. Capability assessment

Identity Management (IDM)

* [ ]	Authoritative identity sources are documented.
* [ ]	Identity correlation and reconciliation are defined.
* [ ]	Joiner, mover, and leaver workflows are implemented.
* [ ]	Account provisioning is controlled.
* [ ]	Deprovisioning is verified.
* [ ]	Identity attributes are maintained consistently.
* [ ]	Orphaned accounts are identified.

Identity and Access Management (IAM)

* [ ]	Authentication architecture is defined.
* [ ]	SSO and federation are implemented where appropriate.
* [ ]	MFA requirements are established.
* [ ]	Authorization policies are documented.
* [ ]	RBAC / ABAC are applied appropriately.
* [ ]	Privileged access is separately controlled.
* [ ]	Application-level authorization is enforced.

Identity Governance and Administration (IGA)

* [ ]	Access request workflows are established.
* [ ]	Approval ownership is defined.
* [ ]	Access certifications are implemented.
* [ ]	SoD policies are documented.
* [ ]	Entitlements have accountable owners.
* [ ]	Access exceptions are tracked.
* [ ]	Audit evidence is available.

3. Cross-capability integration

Integration	Expected outcome
HR to IDM	Accurate identity lifecycle
IDM to directories	Account synchronization
IGA to provisioning	Approved access fulfillment
IAM to applications	Authentication and access enforcement
IGA to application owners	Access certification
Identity systems to SIEM	Security visibility and auditability

4. NHI and AI agent coverage

* [ ]	Service accounts are inventoried.
* [ ]	API identities have defined owners.
* [ ]	Workload identities are governed.
* [ ]	Credentials and secrets are protected.
* [ ]	AI agents have distinct identities.
* [ ]	Agent permissions are task-scoped.
* [ ]	Runtime authorization is enforced.
* [ ]	Agent actions are attributable.
* [ ]	Retirement revokes downstream access.

5. Example identity lifecycle

Authoritative Identity Source
            |
            v
     Identity Management
            |
            v
    Identity Governance
    - Access policies
    - Approval
    - Risk evaluation
            |
            v
       Provisioning
            |
            v
   IAM / Access Enforcement
            |
            v
     Enterprise Resources
            |
            v
   Access Review & Monitoring

6. Architecture findings register

Finding	Risk	Recommendation	Owner
Unowned accounts	Persistent unauthorized access	Establish ownership	IAM
Manual provisioning	Inconsistent access	Automate lifecycle	IDM
Excessive entitlements	Privilege abuse	Implement access governance	IGA
Weak application authorization	Unauthorized operations	Enforce application policies	Application owner
Ungoverned AI agents	Uncontrolled automated actions	Establish agent identity controls	AI platform owner

7. Architecture maturity indicators

Evaluate each capability using an agreed maturity scale:

1. Initial — ad hoc and undocumented.
2. Developing — partially defined.
3. Defined — documented and consistently implemented.
4. Managed — measured and monitored.
5. Optimized — continuously improved.

Assess IDM, IAM, IGA, NHI, and AI agent security separately. Avoid relying on one overall score that hides capability gaps.

Expected outcome: A clearly defined identity security architecture connecting lifecycle management, access control, governance, and continuous assurance.