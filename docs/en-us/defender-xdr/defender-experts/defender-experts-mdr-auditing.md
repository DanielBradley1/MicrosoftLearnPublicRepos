<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-auditing -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Audit Defender Experts actions and administrator changes in Microsoft Defender

**Applies to:**

- [Microsoft Defender Experts MDR](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-overview)
- [Microsoft Defender Experts for Servers](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-servers-overview)

As a tenant administrator, you can use Microsoft Purview to search the audit logs for the times Microsoft Defender Experts signed into your tenant and the actions they did there to perform their investigations. You can also search the audit logs for the changes done by your tenant administrators to the Defender Experts settings.

Auditing is automatically turned on in the Microsoft Defender portal. Features that are audited are logged in the audit log automatically. Auditing can also collect audit logs from GCC environments.

Note

Make sure you have the right [permissions required for audit log search](https://learn.microsoft.com/en-us/microsoft-365/compliance/audit-log-search#before-you-search-the-audit-log).

## Search the audit logs for actions performed by Defender Experts

Perform the following steps to search audit logs for actions performed by Defender Experts in your tenant:

1. Sign into the [Microsoft Purview portal](https://purview.microsoft.com/) to use [Audit New Search](https://learn.microsoft.com/en-us/microsoft-365/compliance/audit-new-search).
2. Provide a **Date and time range \(UTC\)**.
3. Select the **Workload** and **Record type** from the list shown in the following table to further narrow your search.
4. Select **Search** to list the audit logs related to actions taken by our experts in your tenant.

[![Partial screenshot of Microsoft Purview portal Defender New search page.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/auditing/audit.png)](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/auditing/audit.png#lightbox)

| Action performed by Defender Experts | Workload | Record type |
| --- | --- | --- |
| Sign into customer tenant | AzureActiveDirectory | AzureActiveDirectoryStsLogon |
| Make changes to incidents in Microsoft Defender portal | Microsoft365Defender | MS365Dincident |
| Make changes to alert suppression rules in Microsoft Defender portal | Microsoft365Defender | MS365DSuppressionRule |
| Make changes to indicators in Microsoft Defender for Endpoint | MicrosoftDefenderForEndpoint | MSDEIndicatorsSettings |
| Perform device remediation actions in Microsoft Defender for Endpoint | MicrosoftDefenderForEndpoint | MSDEResponseActions |

[![Partial screenshot of a sample audit log related to Defender Experts.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/auditing/audit-2.png)](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/auditing/audit-2.png#lightbox)

## Search the audit logs for actions performed by your administrators in the Defender Experts settings

Perform the following steps to search audit logs for changes made by your administrators in the Defender Experts settings:

1. Sign into the [Microsoft Purview portal](https://purview.microsoft.com/) to use [Audit New Search](https://learn.microsoft.com/en-us/microsoft-365/compliance/audit-new-search).
2. Provide a **Date and time range \(UTC\)**.
3. Under **Workload**, choose *MicrosoftDefenderExperts*.
4. Select **Search** to list the audit logs related to actions taken by your tenant administrators to the Defender Experts settings.

[![Partial screenshot of Microsoft Purview portal Defender New search page showing the Workload field selected to MicrosoftDefenderExperts.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/auditing/audit-3.png)](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/auditing/audit-3.png#lightbox)

## Search the audit logs using a PowerShell script

In addition to using Audit New Search in the Microsoft Purview portal, you can use PowerShell cmdlets to search for audit logs. [Search the audit log with a PowerShell script](https://learn.microsoft.com/en-us/microsoft-365/compliance/audit-log-search-script).

## See also

- For prerequisites, limitations, and other guidance, see [Important considerations for Microsoft Defender Experts](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-considerations).

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
