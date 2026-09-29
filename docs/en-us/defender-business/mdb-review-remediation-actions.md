<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-review-remediation-actions -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Review remediation actions in the Action Center

As threats are detected, remediation actions come into play. Depending on the particular threat and how your security settings are configured, remediation actions might be taken automatically or only upon approval. Examples of remediation actions include stopping a process from running or removing a scheduled task.

All remediation actions are tracked in the Action Center.

[![Screenshot of the location of the Action Center in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-business/media/mdb-actioncenter.png)](https://learn.microsoft.com/en-us/defender-business/media/mdb-actioncenter.png#lightbox)

This article describes how to use the Action Center to review pending and completed remediation actions in Defender for Business.

## How to use the Action Center

Use the following steps to open and review the Action Center.

1. In the Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Actions & submissions** > **Action Center**. Or, to go directly to the **Action Center** page, use [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center).
2. On the **Action Center** page, use the available tabs:

   - **Pending**: View and approve \(or reject\) any pending actions. Actions on the **Pending** tab can arise from anti-virus protection, anti-malware protection, automated investigations, manual response activities, or live response sessions.
   - **History**: View completed actions.

## Remediation actions

Defender for Business includes several remediation actions. These actions include manual response actions, actions following automated investigation, and live response actions.

The following table lists remediation actions that are available.

| Source | Actions |
| --- | --- |
| [Automatic attack disruption](https://learn.microsoft.com/en-us/defender-business/mdb-attack-disruption) | - Contain a user account on a device<br>- Disable a user account |
| [Automated investigations](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations) | - Remove a registry key<br>- Kill a process<br>- Stop a service<br>- Disable a driver<br>- Remove a scheduled task |
| [Manual response actions](https://learn.microsoft.com/en-us/defender-endpoint/respond-machine-alerts) | - Isolate a device<br>- Add an indicator to block or allow a file |
| [Live response](https://learn.microsoft.com/en-us/defender-endpoint/live-response) | - Analyze a file<br>- Run a script<br>- Send a suspicious entity to Microsoft for analysis<br>- Remediate a file<br>- Proactively hunt for threats |

## Next steps

Use the following articles to learn more about responding to threats and managing devices:

- [Respond to and mitigate threats in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-respond-mitigate-threats)
- [Manage devices in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-manage-devices)
