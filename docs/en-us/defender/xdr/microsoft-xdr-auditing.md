<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/microsoft-xdr-auditing -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Search the audit log for events in Microsoft Defender XDR

The audit log helps you investigate specific activities across Microsoft 365 services. In the Microsoft Defender portal, Microsoft Defender XDR and Microsoft Defender for Endpoint activities are audited.

Some of the audited activities include:

- Changes to data retention settings
- Changes to advanced features
- Creation of indicators of compromise
- Isolation of devices
- Add\\edit\\deletion of security roles
- Create\\edit custom detection rules
- Assign user to an incidents

For a complete list of Microsoft Defender activities that are audited, see [Microsoft Defender activities](#microsoft-defender-xdr-activities) and [Microsoft Defender for Endpoint activities](#microsoft-defender-for-endpoint-activities).

Auditing is automatically turned on for Microsoft Defender. Features that are audited are logged in the audit log automatically. Auditing can also collect audit logs from GCC environments.

## Prerequisites

To access the audit log, you need to have the **View-Only Audit Logs** or **Audit Logs** role in Exchange Online. By default, those roles are assigned to the Compliance Management and Organization Management role groups.

Note

Global administrators in Office 365 and Microsoft 365 are automatically added as members of the Organization Management role group in Exchange Online.

Microsoft Defender uses the [Microsoft Purview auditing solution](https://learn.microsoft.com/en-us/purview/audit-solutions-overview). Before you can look at the audit data in the Microsoft Defender portal, you need to turn on auditing in the Microsoft Purview portal. For more information, see [Turn auditing on or off](https://learn.microsoft.com/en-us/purview/audit-log-enable-disable).

Important

Global Administrator is a highly privileged role that should be limited to scenarios when you can't use an existing role. Microsoft recommends that you use roles with the fewest permissions. Using accounts with lower permissions helps improve security for your organization.

## Search the audit log

You can search the audit log from the Microsoft Defender portal or the Microsoft Purview compliance portal. For detailed compliance portal instructions, see [Search the audit log in the compliance portal](https://learn.microsoft.com/en-us/purview/audit-new-search). Audit log record retention is based on Microsoft Purview retention policies. For more information, see [Manage audit log retention policies](https://learn.microsoft.com/en-us/purview/audit-log-retention-policies).

Follow these steps to search the audit log:

1. Go to the [Microsoft Defender portal's Audit page](https://security.microsoft.com/auditlogsearch). You can also open the [Purview compliance portal](https://purview.microsoft.com) and select **Audit**.

   [![Screenshot of the unified audit log page in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-xdr-auditing/unified-audit-log-xdr.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-xdr-auditing/unified-audit-log-xdr.png#lightbox)
2. On the **New Search** page, filter the activities, dates, and users you want to audit.
3. Select **Search**

   [![Screenshot of the unified audit log search options in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-xdr-auditing/unified-audit-search.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-xdr-auditing/unified-audit-search.png#lightbox)
4. Export your results to Excel for further analysis.

For step-by-step instructions, see [Search the audit log in the compliance portal](https://learn.microsoft.com/en-us/purview/audit-new-search).

How long audit log records are kept depends on your Microsoft Purview retention policies. To learn more, see [Manage audit log retention policies](https://learn.microsoft.com/en-us/purview/audit-log-retention-policies).

## Microsoft Defender XDR audit log activity reference

For a list of all events that are logged for user and admin activities in Microsoft Defender in the Microsoft 365 audit log, see:

- [Custom detection activities in Microsoft Defender in the audit log](https://learn.microsoft.com/en-us/purview/audit-log-activities#microsoft-defender-xdr-custom-detection-activities)
- [Incident activities in Microsoft Defender in the audit log](https://learn.microsoft.com/en-us/purview/audit-log-activities#microsoft-defender-xdr-custom-detection-activities)
- [Suppression rule activities in Microsoft Defender in the audit log](https://learn.microsoft.com/en-us/purview/audit-log-activities#microsoft-defender-xdr-suppression-rule-activities)

## Microsoft Defender for Endpoint audit log activity reference

The Microsoft 365 audit log records user and admin activities in Defender for Endpoint. For details, see:

- [General settings activities in Defender for Endpoint in the audit log](https://learn.microsoft.com/en-us/purview/audit-log-activities#microsoft-defender-for-endpoint-general-settings-activities)
- [Indicator settings activities in Defender for Endpoint in the audit log](https://learn.microsoft.com/en-us/purview/audit-log-activities#microsoft-defender-for-endpoint-indicator-settings-activities)
- [Response action activities in Defender for Endpoint in the audit log](https://learn.microsoft.com/en-us/purview/audit-log-activities#microsoft-defender-for-endpoint-reponse-actions-activities)
- [Roles settings activities in Defender for Endpoint in the audit log](https://learn.microsoft.com/en-us/purview/audit-log-activities#microsoft-defender-for-endpoint-roles-settings-activities)

## Search for events using a PowerShell script

You can use the following PowerShell code snippet to query the Office 365 Management API for Microsoft Defender XDR events. The script connects to Exchange Online PowerShell, establishes a remote session, and then searches the unified audit log for a specified record type and date range.

Note

Before you run this script, identify the record type value you need. See the API column in [Audit log activities](https://learn.microsoft.com/en-us/purview/audit-log-activities) for the record type values.

```PowerShell
$cred = Get-Credential
$s = New-PSSession -ConfigurationName microsoft.exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $cred -Authentication Basic -AllowRedirection 
Import-PSSession $s
Search-UnifiedAuditLog -StartDate 2023/03/12 -EndDate 2023/03/20 -RecordType <ID>
```

Note

See the API column in [Audit log activities](https://learn.microsoft.com/en-us/purview/audit-log-activities) for the record type values.

For more information, see [Use a PowerShell script to search the audit log](https://learn.microsoft.com/en-us/purview/audit-log-search-script)

## Related content

- [Detailed properties in the audit log](https://learn.microsoft.com/en-us/purview/audit-log-detailed-properties)
- [Export, configure, and view audit log records](https://learn.microsoft.com/en-us/purview/audit-log-export-records)
- [Office 365 Management Activity API reference](https://learn.microsoft.com/en-us/office/office-365-management-api/office-365-management-activity-api-reference)
