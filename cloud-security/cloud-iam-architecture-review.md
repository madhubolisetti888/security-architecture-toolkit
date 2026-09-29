Cloud IAM Architecture Review

Purpose

Cloud IAM should be treated as a security architecture control plane rather than simply a collection of roles and permissions.

The objective is to establish:

* Strong identity
* Explicit authorization
* Least privilege
* Controlled privilege escalation
* Identity lifecycle governance
* Context-aware access
* Monitoring
* Rapid revocation
* Bounded blast radius

⸻

Cloud IAM Decision Model

A useful way to model cloud access is:

Identity
    +
Context
    +
Policy
    +
Resource
    +
Action
    ↓
Authorization Decision
    ↓
Allow / Deny

Example:

Workload Identity
       +
Production Context
       +
Read Policy
       +
Customer Database
       +
Read Action
       ↓
Authorization Decision

⸻

1. Identity

Identify every entity that can access cloud resources.

Human

* Employees
* Administrators
* Developers
* Contractors
* External users

Non-human

* Applications
* Services
* Workloads
* CI/CD pipelines
* Automation
* Cloud service identities
* Third-party integrations

Questions

* Is every identity uniquely identifiable?
* Are shared identities prohibited where practical?
* Are privileged identities separated?
* Are machine identities governed?

⸻

2. Authentication

Determine how each identity establishes its identity.

Evaluate:

* Federation
* MFA
* Certificates
* Workload identity
* Managed identities
* Short-lived tokens
* Service authentication

Questions

* Can credentials be replayed?
* Are credentials long-lived?
* How are credentials rotated?
* How quickly can compromised credentials be revoked?

⸻

3. Authorization

Authentication establishes identity.

Authorization determines what that identity can do.

Evaluate:

* RBAC
* ABAC
* Resource policies
* Application authorization
* API authorization
* Privileged access
* Conditional access
* Least privilege

Questions

* What resources can the identity access?
* Which actions are permitted?
* Are permissions resource-specific?
* Are administrative privileges separated?

⸻

4. Permission Scope

Review permissions at the smallest practical scope.

Consider:

Organization
    ↓
Account / Subscription / Project
    ↓
Resource Group
    ↓
Resource
    ↓
Action

A workload that requires:

Read → Resource A

should not automatically receive:

Read/Write/Delete → All Resources

⸻

5. Privileged Access

Identify high-impact permissions.

Examples:

* IAM administration
* Security administration
* Network administration
* Key management
* Infrastructure deployment
* Database administration
* Production access

Review:

* Just-in-time access
* Approval
* Privilege elevation
* Session monitoring
* Emergency access
* Break-glass accounts

⸻

6. Identity Lifecycle

Cloud IAM should have a defined lifecycle.

Request
   ↓
Approval
   ↓
Provision
   ↓
Use
   ↓
Review
   ↓
Modify
   ↓
Revoke
   ↓
Retire

Questions

* Who owns the identity?
* Who approves access?
* How frequently is access reviewed?
* What triggers access removal?
* Are dormant identities detected?

⸻

7. Machine Identity

Machine identities deserve specific attention.

Examples:

* Application identity
* Service identity
* Workload identity
* Pipeline identity
* Automation identity

Ask:

If this machine identity is compromised, what can it access?

Then determine:

* Resource scope
* Privileges
* Network reachability
* Secrets
* Downstream services
* Administrative capabilities

⸻

8. Context

Authorization can depend on more than identity.

Potential context:

* Device posture
* Workload posture
* Location
* Time
* Network context
* Resource sensitivity
* Risk signals
* Authentication strength

Conceptually:

Identity
   +
Context
   +
Policy
   ↓
Authorization

⸻

9. Monitoring

Monitor IAM activity such as:

* Authentication
* Authorization failures
* Permission changes
* Role assignments
* Policy changes
* New identities
* Privilege elevation
* Credential creation
* Credential rotation
* Administrative operations

⸻

10. Compromise and Blast Radius

For each critical identity:

What happens if this identity is compromised?

Document:

* Accessible resources
* Permitted actions
* Privilege escalation paths
* Lateral movement paths
* Sensitive data exposure
* Administrative impact

Then design controls to reduce the blast radius.

⸻

Architecture Review Questions

1. What identities exist?
2. Who owns each identity?
3. How is each identity authenticated?
4. What can each identity access?
5. What actions can it perform?
6. Why does it need those permissions?
7. Where is authorization enforced?
8. How is privileged access controlled?
9. How is access reviewed?
10. How are identities revoked?
11. What happens if the identity is compromised?
12. What is the maximum blast radius?

⸻

Architecture Principle

Every cloud access decision should have an identifiable subject, an explicit authorization policy, a defined resource, a permitted action and a bounded blast radius.

Cloud IAM therefore becomes more than:

Roles + Permissions

It becomes:

Identity + Policy + Context + Authorization + Lifecycle + Detection

⸻

Final Architecture Question

Can you explain why every critical identity has every permission it currently possesses—and what happens when that identity is compromised?