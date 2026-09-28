<!-- Source: https://learn.microsoft.com/en-us/entra/global-secure-access/reference-change-request-template -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# Global Secure Access change request template

Use this template for all **normal** and **major** changes to Global Secure Access configuration. For change categories and the execution process, see the [Common operations guide](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-operations-common#change-management).

---

## Change request details

| Field | Value |
| --- | --- |
| **Change ID** | *\(your IT service management \(ITSM\) ticket number or sequential ID\)* |
| **Date submitted** |  |
| **Requested by** |  |
| **Change category** | Standard / Normal / Emergency / Major |
| **Priority** | Low / Medium / High / Critical |
| **Target date** |  |
| **Maintenance window required** | Yes / No |

## Description

**What is being changed?**

*\(Describe the specific configuration change in detail. Include the Global Secure Access capability affected: Private Access, Internet Access, Remote Networks, or Microsoft Traffic.\)*

**Why is this change needed?**

*\(Business justification, user request, security requirement, or compliance need.\)*

## Scope and impact

**Affected Global Secure Access capability:**

- Private Access
- Internet Access
- Remote Networks
- Microsoft Traffic
- Common / Cross-cutting

**Affected components:**

*\(List specific components: connector groups, application segments, web filtering policies, traffic forwarding rules, tunnels, etc.\)*

**Affected users / sites:**

*\(Estimate the number of users or sites impacted. List specific groups or locations if known.\)*

**Expected user impact during change:**

- No user impact
- Brief reconnection \(< 1 minute\)
- Service interruption during maintenance window
- Extended impact—communication plan required

## Risk assessment

| Risk factor | Assessment |
| --- | --- |
| **Risk level** | Low / Medium / High |
| **Potential for service disruption** | None / Minimal / Moderate / High |
| **Reversibility** | Fully reversible / Partially reversible / Irreversible |

**What could go wrong?**

*\(Describe the worst-case scenario if the change fails.\)*

## Testing

**Tested in non-production?** Yes / No / Not applicable

**Test results:**

*\(Describe testing performed and outcomes. If not tested, explain why.\)*

## Prechange checklist

- Configuration backup completed \(see capability guide for export scripts\)
- Change approved by Service Owner or Change Advisory Board
- Communication sent to affected users and support teams \(if necessary\)
- Rollback plan documented \(see Rollback plan\)
- Maintenance window scheduled \(if necessary\)
- On-call engineer confirmed for maintenance window

## Rollback plan

**How to roll back if the change fails:**

*\(Step-by-step procedure to restore the previous configuration. Reference the backup file created in the prechange checklist.\)*

**Maximum time to decide on rollback:**

*\(How long to wait before deciding the change failed and needs to be rolled back.\)*

## Execution

| Step | Action | Completed | Notes |
| --- | --- | --- | --- |
| 1 | Back up current configuration | \[ \] |  |
| 2 | *\(Add change steps\)* | \[ \] |  |
| 3 | *\(Add change steps\)* | \[ \] |  |
| 4 | Verify change—check traffic logs, alerts, and user connectivity | \[ \] |  |
| 5 | Confirm rollback isn't needed | \[ \] |  |

## Post-change verification

- Traffic logs show expected behavior
- No new alerts triggered
- User access confirmed for affected applications / sites
- Change documented in ITSM system

## Approvals

| Role | Name | Approved | Date |
| --- | --- | --- | --- |
| Service Owner |  | Yes / No |  |
| Network Security Engineer |  | Yes / No |  |
| Change Advisory Board \(if major\) |  | Yes / No |  |

---

**Post-change notes:**

---

---
