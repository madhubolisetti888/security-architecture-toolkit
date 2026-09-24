Identity Architecture Review

A practical framework for reviewing identity security across users, privileged accounts, applications, services, workloads and devices.

Purpose

Identity is a foundational component of Zero Trust architecture.

A secure architecture should not assume that a user, workload, device or service is trusted merely because it exists inside a corporate network or cloud environment.

Every access request should be evaluated using relevant identity, authentication, authorization, resource and contextual information.

⸻

1. Identity Inventory

Review questions

* Are all human identities inventoried?
* Are privileged identities separately identified?
* Are service accounts documented?
* Are application and workload identities known?
* Are machine identities and certificates tracked?
* Is every identity associated with an accountable owner?
* Are inactive or orphaned identities identified?

Evidence

Look for:

* Identity inventory
* Application and service catalog
* Service-account register
* Certificate inventory
* Ownership records
* Identity lifecycle reports

⸻

2. Authentication

Review questions

* Is strong authentication required for sensitive resources?
* Is MFA enforced for privileged access?
* Are authentication methods appropriate to the risk?
* Are workload-to-workload interactions authenticated?
* Are service accounts using secure authentication mechanisms?
* Are shared accounts prohibited or tightly controlled?
* Are authentication events centrally logged?

Evidence

Look for:

* Identity provider
* MFA
* SSO
* Federation
* Workload identity
* Certificates
* OAuth/OIDC
* mTLS
* Authentication logs

⸻

3. Authorization

Review questions

* Is access based on least privilege?
* Are permissions granted according to business or technical need?
* Are privileged operations separately controlled?
* Is authorization enforced at the application or resource layer?
* Are permissions reviewed periodically?
* Are dormant or excessive permissions removed?
* Can access decisions consider context and risk?

Evidence

Look for:

* RBAC
* ABAC
* Policy engine
* Application authorization
* Privileged access management
* Just-in-time access
* Access review records

⸻

4. Privileged Identity

Review questions

* Are administrative identities separated from standard identities?
* Is privileged access time-bound where practical?
* Are privileged sessions monitored?
* Are administrator actions logged?
* Are emergency or break-glass accounts controlled?
* Are privileged credentials protected and rotated?
* Is dual authorization required for high-impact actions?

Evidence

Look for:

* PAM
* Just-in-time elevation
* Session recording
* Break-glass procedures
* Privileged activity logs
* Credential vaulting
* Approval workflows

⸻

5. Non-Human Identity

Non-human identities include:

* Applications
* APIs
* Services
* Containers
* Kubernetes workloads
* CI/CD pipelines
* Automation accounts
* Cloud workloads
* Devices
* Certificates
* API clients

Review questions

* Does every non-human identity have an owner?
* Is its purpose documented?
* Are permissions narrowly scoped?
* Are long-lived credentials avoided?
* Are secrets stored securely?
* Are credentials rotated automatically?
* Can the identity be revoked quickly?
* Can the identity access resources outside its intended scope?

Evidence

Look for:

* Workload identity
* Secrets management
* Certificate management
* Short-lived tokens
* Cloud IAM roles
* Service mesh identity
* API client inventory
* Automated rotation

⸻

6. Identity Lifecycle

Review questions

* How are identities created?
* How are identity changes approved?
* How are identities disabled?
* How are employees, contractors and suppliers offboarded?
* How are service accounts retired?
* How are certificates renewed or revoked?
* Are orphaned identities detected?

Evidence

Look for:

* Joiner-mover-leaver process
* Identity governance
* Access certification
* Automated provisioning
* Deprovisioning workflows
* Certificate revocation
* Ownership reviews

⸻

7. Monitoring and Detection

Review questions

* Are authentication failures monitored?
* Are unusual privilege changes detected?
* Are anomalous service-account activities identified?
* Are impossible-travel or unusual-location events evaluated where relevant?
* Are unusual workload-to-workload calls monitored?
* Are sensitive resource access events recorded?
* Can identity compromise be investigated across systems?

Evidence

Look for:

* SIEM
* UEBA
* Identity threat detection
* Authentication telemetry
* Privilege-change alerts
* Cloud audit logs
* Application logs
* Workload telemetry

⸻

8. Compromise and Recovery

Review questions

* How quickly can a compromised identity be disabled?
* Can active sessions be terminated?
* Can tokens be revoked?
* Can secrets and certificates be rotated?
* What resources are reachable from the compromised identity?
* Can lateral movement be limited?
* Are recovery procedures tested?

Evidence

Look for:

* Identity disablement procedure
* Token revocation
* Secret rotation
* Certificate revocation
* Session termination
* Incident response playbooks
* Access graph or privilege analysis

⸻

Identity Architecture Principles

A robust identity architecture should aim for:

* Explicit identity: Every subject is identifiable.
* Strong authentication: Authentication strength matches resource sensitivity.
* Least privilege: Access is limited to what is required.
* Separation of duties: High-impact activities require appropriate separation.
* Short-lived access: Persistent privileges are minimized.
* Lifecycle control: Identities are created, changed and removed systematically.
* Observability: Identity activity is logged and monitored.
* Rapid recovery: Compromised identities can be contained quickly.
* Accountability: Every identity has a clear owner and purpose.

⸻

Architecture Review Question

If this identity were compromised today, what could it access, how far could it move, and how quickly could we contain it?

That question connects identity architecture directly to:

Zero Trust → Least Privilege → Attack Paths → Blast Radius → Detection → Recovery