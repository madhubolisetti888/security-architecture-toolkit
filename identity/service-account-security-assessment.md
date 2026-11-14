Service Account Security Assessment

Suggested repository path: identity/service-account-security-assessment.md

1. Purpose

Assess service account ownership, credential protection, access privileges, monitoring, and lifecycle controls.

2. Service account inventory

Field	Description
Account ID	Unique account identifier
Account name	Service account name
Application	Associated application
Owner	Accountable team or person
Purpose	Approved business function
Environment	Development / Test / Production
Target systems	Resources accessed
Permissions	Roles and entitlements
Authentication	Password / Certificate / Token / Federation
Credential expiry	Expiry or rotation date
Last activity	Most recent verified use
Privilege level	Standard / Elevated / Administrative
Status	Active / Suspended / Retired

3. Security assessment checklist

Ownership and governance

* [ ]	Account owner is documented.
* [ ]	Application association is recorded.
* [ ]	Business purpose is approved.
* [ ]	Account has a defined lifecycle.
* [ ]	Access review frequency is established.

Credential management

* [ ]	Credentials are not hardcoded.
* [ ]	Secrets are stored in approved vaults.
* [ ]	Static credentials are avoided where feasible.
* [ ]	Rotation and expiration are monitored.
* [ ]	Credential exposure response is defined.

Privileged access

* [ ]	Permissions are mapped to application requirements.
* [ ]	Administrative permissions are justified.
* [ ]	Unused entitlements are removed.
* [ ]	Production permissions are restricted.
* [ ]	Sensitive actions have additional controls.

Monitoring

* [ ]	Authentication events are logged.
* [ ]	Account activity is monitored.
* [ ]	Privilege changes are recorded.
* [ ]	Unexpected access patterns are detected.
* [ ]	Emergency suspension is tested.

Retirement

* [ ]	Application dependencies are identified.
* [ ]	Credentials and tokens are revoked.
* [ ]	Target-system permissions are removed.
* [ ]	Account is disabled or deleted.
* [ ]	Revocation is verified.

4. Risk register

Risk	Impact	Recommended control
Unknown account owner	Unaccountable access	Ownership register
Hardcoded credentials	Secret exposure	Centralized secrets management
Excessive permissions	Privilege abuse	Least privilege
Shared credentials	Poor attribution	Unique identities
Unmonitored activity	Delayed detection	Centralized logging
Orphaned service account	Persistent access	Lifecycle automation

5. Service account access review

For each account, answer:

1. Is the account still required?
2. Is its owner still accountable?
3. Does its purpose remain valid?
4. Are all permissions necessary?
5. Are credentials appropriately protected?
6. Is the account used only by approved applications?
7. Is its activity monitored?
8. Can its access be revoked quickly?

6. Example retirement workflow

Application retirement request
             |
             v
Identify dependent service accounts
             |
             v
Confirm account ownership
             |
             v
Validate application dependencies
             |
             v
Revoke credentials and tokens
             |
             v
Remove downstream permissions
             |
             v
Disable or delete service account
             |
             v
Verify access removal and retain evidence

7. Metrics

* Percentage of service accounts with verified owners.
* Percentage with documented purposes.
* Number of privileged service accounts.
* Number of inactive accounts.
* Number of hardcoded credential findings.
* Percentage meeting credential rotation policy.
* Percentage reviewed on schedule.
* Average time to revoke access.

Assessment outcome: Identify ownership gaps, credential weaknesses, excessive permissions, monitoring deficiencies, and incomplete retirement controls.