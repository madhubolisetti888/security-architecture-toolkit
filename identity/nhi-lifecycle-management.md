Non-Human Identity Lifecycle Assessment

Suggested repository path: identity/nhi-lifecycle-management.md

1. Objective

Establish a repeatable process to discover, govern, monitor, and retire non-human identities across enterprise environments.

2. NHI inventory template

Field	Description
Identity ID	Unique identifier
Identity type	Service / API / workload / bot / AI agent
Application or workload	Associated system
Owner	Accountable team or individual
Purpose	Business or technical requirement
Environment	Development / Test / Production
Permissions	Roles, scopes, entitlements
Authentication method	Certificate / token / federation
Credential expiry	Expiry or rotation date
Last activity	Last verified usage
Risk level	Critical / High / Medium / Low
Lifecycle status	Active / Suspended / Retired

3. Lifecycle control checklist

Discovery

* [ ]	Identify NHIs across enterprise platforms.
* [ ]	Detect duplicate and unknown identities.
* [ ]	Record associated applications and workloads.
* [ ]	Identify credentials and access relationships.

Ownership

* [ ]	Assign a business or technical owner.
* [ ]	Document identity purpose.
* [ ]	Define accountable support team.
* [ ]	Establish review and renewal requirements.

Access governance

* [ ]	Apply least privilege.
* [ ]	Remove unused permissions.
* [ ]	Separate development and production access.
* [ ]	Review privileged access.
* [ ]	Establish approval for sensitive access.

Credential security

* [ ]	Protect secrets and private keys.
* [ ]	Avoid hardcoded credentials.
* [ ]	Use short-lived credentials where supported.
* [ ]	Automate rotation.
* [ ]	Monitor expiry and exposure.

Monitoring

* [ ]	Collect authentication events.
* [ ]	Monitor API and workload activity.
* [ ]	Detect abnormal usage.
* [ ]	Track permission changes.
* [ ]	Identify inactive and orphaned identities.

Retirement

* [ ]	Confirm business dependency removal.
* [ ]	Revoke credentials and tokens.
* [ ]	Remove permissions from target systems.
* [ ]	Disable or delete the identity.
* [ ]	Verify revocation.
* [ ]	Preserve audit evidence.

4. NHI risk register

Risk	Potential impact	Control
Unowned identity	Persistent unknown access	Ownership assignment
Excessive permissions	Privilege abuse	Least privilege
Hardcoded credentials	Credential compromise	Secrets management
Long-lived tokens	Extended unauthorized access	Short-lived credentials
Inactive identity	Unnecessary attack surface	Usage monitoring
Incomplete retirement	Residual access	Verified deprovisioning

5. Suggested maturity metrics

* NHI inventory coverage.
* Percentage of NHIs with verified owners.
* Percentage with documented purpose.
* Percentage meeting credential security standards.
* Number of orphaned identities.
* Number of excessive-permission findings.
* Percentage of high-risk NHIs reviewed on schedule.
* Mean time to revoke compromised NHI access.

6. Retirement workflow

Identify retirement requirement
            |
            v
Check application dependencies
            |
            v
Obtain required approval
            |
            v
Revoke credentials and tokens
            |
            v
Remove permissions and integrations
            |
            v
Disable or delete identity
            |
            v
Verify revocation and retain evidence

7. Assessment outcome

Document:

* Discovered identity population.
* Ownership gaps.
* Excessive permissions.
* Credential security weaknesses.
* Monitoring gaps.
* Retirement risks.
* Remediation owners and target dates.

Adapt the controls to the identity types, cloud environments, and business criticality involved.