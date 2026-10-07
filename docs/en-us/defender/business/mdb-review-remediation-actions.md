<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-review-remediation-actions -->
<!-- Sitemap-Last-Modified: 2026-10-01 -->

# Review remediation actions in the Action Center

As the system detects threats, remediation actions address them. Depending on the particular threat and your security settings, the system might take remediation actions automatically or wait for your approval. Examples of remediation actions include stopping a process from running or removing a scheduled task.

The Action Center tracks all remediation actions.

[![Screenshot of the location of the Action Center in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-business/media/mdb-actioncenter.png)](https://learn.microsoft.com/en-us/defender-business/media/mdb-actioncenter.png#lightbox)

Use the Action Center to review pending and completed remediation actions in Microsoft Defender for Business.

## How to use the Action Center

Use the following steps to open and review the Action Center.

1. In the [Defender portal](https://security.microsoft.com), go to **Actions & submissions** > **Action Center**. Or, go directly to the **Action Center** [page](https://security.microsoft.com/action-center).
2. On the **Action Center** page, use the available tabs:

   - **Pending**: View and approve or reject any pending actions. Actions on the **Pending** tab can arise from virus protection, malware protection, automated investigations, manual response activities, or live response sessions.
   - **History**: View completed actions.

## Remediation actions

Defender for Business includes several remediation actions. These actions include manual response actions, actions following automated investigation, and live response actions.

The following table lists remediation actions that are available.

| Source | Actions |
| --- | --- |
| [Automatic attack disruption](https://learn.microsoft.com/en-us/defender-business/mdb-attack-disruption) | - Contain a device<br>- Contain a user account on a device<br>- Disable a user account |
| [Automated investigations](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations) | - Quarantine a file<br>- Remove a registry key<br>- Kill a process<br>- Stop a service<br>- Disable a driver<br>- Remove a scheduled task |
| [Manual response actions](https://learn.microsoft.com/en-us/defender-endpoint/respond-machine-alerts) | - Run antivirus scan<br>- Isolate a device<br>- Add an indicator to block or allow a file |
| [Live response](https://learn.microsoft.com/en-us/defender-endpoint/live-response) | - Collect forensic data<br>- Analyze a file<br>- Run a script<br>- Send a suspicious entity to Microsoft for analysis<br>- Remediate a file<br>- Proactively hunt for threats |

## Related concepts

- [Respond to and mitigate threats in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-respond-mitigate-threats)
- [Manage devices in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-manage-devices)
