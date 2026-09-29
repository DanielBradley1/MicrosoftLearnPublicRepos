<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/dlp-investigate-alerts-sentinel -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Investigate data loss prevention alerts with Microsoft Sentinel

**Applies to:**

- Microsoft Defender
- Microsoft Sentinel

This article explains how to use the Microsoft Defender XDR connector in Microsoft Sentinel to import, correlate, and investigate data loss prevention \(DLP\) alerts alongside other data sources. You learn how to set up the connector, view DLP incidents in Sentinel, and query user activities related to specific alerts.

## Prepare to investigate DLP alerts in Microsoft Sentinel

See, [Investigate data loss prevention alerts with Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/dlp-investigate-alerts-defender) for more details.

## DLP investigation experience in Microsoft Sentinel

You can use the Microsoft Defender XDR connector in Microsoft Sentinel to import all DLP incidents into Sentinel to extend your correlation, detection, and investigation across other data sources and extend your automated orchestration flows using Sentinel's native security orchestration, automation, and response \(SOAR\) capabilities.

1. Follow the instructions in [Connect data from Microsoft Defender XDR to Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender) to import all incidents including DLP incidents and alerts into Sentinel. Enable the `CloudAppEvents` event connector, which imports Office 365 audit log events into Microsoft Sentinel, to pull all Office 365 audit logs into Sentinel.

   You should be able to see your DLP incidents in Sentinel once the Microsoft Defender XDR connector and the `CloudAppEvents` event connector are set up.
2. Select **Alerts** to view the alert page.
3. You can use **AlertType**, **startTime**, and **endTime** to query the **CloudAppEvents** table to get all the user activities that contributed to the alert. Use this query to identify the underlying activities. The query retrieves a specific security alert by its `SystemAlertId`, then correlates it with `CloudAppEvents` to return the user activities that occurred within the alert time window. Replace the empty `SystemAlertId` value with the ID of the alert you want to investigate.

   Use the following KQL query to locate a specific alert from the last 30 days by its `SystemAlertId` and correlate it with user activities in `CloudAppEvents`:

```kusto
let Alert = SecurityAlert
| where TimeGenerated > ago(30d)
| where SystemAlertId == ""; // insert the systemAlertID here
CloudAppEvents
| extend correlationId1 = parse_json(tostring(RawEventData.Data)).cid
| extend correlationId = tostring(correlationId1)
| join kind=inner Alert on $left.correlationId == $right.AlertType
| where RawEventData.CreationTime > StartTime and RawEventData.CreationTime < EndTime
```

## Related articles

- [Incidents overview](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview)
- [Prioritize incidents](https://learn.microsoft.com/en-us/defender-xdr/incident-queue)
- [Manage incidents](https://learn.microsoft.com/en-us/defender-xdr/manage-incidents)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
