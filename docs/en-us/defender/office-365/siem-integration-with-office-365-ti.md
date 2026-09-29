<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/siem-integration-with-office-365-ti -->
<!-- Sitemap-Last-Modified: 2025-09-04 -->

# SIEM integration with Microsoft Defender for Office 365

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

If your organization is using a security information and event management \(SIEM\) server, you can integrate Microsoft Defender for Office 365 with your SIEM server. You can set up this integration by using the [Office 365 Activity Management API](https://learn.microsoft.com/en-us/office/office-365-management-api/office-365-management-activity-api-reference).

SIEM integration enables you to view information, such as malware or phish detected by Microsoft Defender for Office 365, in your SIEM server reports.

- To see an example of SIEM integration with Microsoft Defender for Office 365, see [this blog post](https://techcommunity.microsoft.com/blog/microsoftsecurityandcompliance/improve-the-effectiveness-of-your-soc-with-office-365-atp-and-the-o365-managemen/1525185).
- To learn more about the Office 365 Management APIs, see [Office 365 Management APIs overview](https://learn.microsoft.com/en-us/office/office-365-management-api/office-365-management-apis-overview).

## How SIEM integration works

The Office 365 Activity Management API retrieves information about user, admin, system, and policy actions and events from your organization's Microsoft 365 and Microsoft Entra activity logs. If your organization has Microsoft Defender for Office 365 Plan 1 or 2, or Office 365 E5, you can use the [Microsoft Defender for Office 365 schema](https://learn.microsoft.com/en-us/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema).

Recently, events from automated investigation and response capabilities in [Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet) were added to the Office 365 Management Activity API. In addition to including data about core investigation details such as ID, name and status, the API also contains high-level information about investigation actions and entities.

The SIEM server or other similar system polls the **audit.general** workload to access detection events. To learn more, see [Get started with Office 365 Management APIs](https://learn.microsoft.com/en-us/office/office-365-management-api/get-started-with-office-365-management-apis).

## Enum: AuditLogRecordType - Type: Edm.Int32

### AuditLogRecordType

The following table summarizes the values of **AuditLogRecordType** that are relevant for Microsoft Defender for Office 365 events:

| Value | Member name | Description |
| --- | --- | --- |
| 28 | ThreatIntelligence | Phishing and malware events from [the built-in security features for all cloud mailboxes](https://learn.microsoft.com/en-us/defender-office-365/eop-about) and from Microsoft Defender for Office 365. |
| 41 | ThreatIntelligenceUrl | Safe Links time-of-click and block override events from Microsoft Defender for Office 365. |
| 47 | ThreatIntelligenceAtpContent | Phishing and malware events for files in SharePoint, OneDrive, and Microsoft Teams, from Microsoft Defender for Office 365. |
| 64 | AirInvestigation | Automated investigation and response events, such as investigation details and relevant artifacts, from Microsoft Defender for Office 365 Plan 2. |

Important

You must have either the Global Administrator<sup>\*</sup> or Security Administrator role assigned to set up SIEM integration with Microsoft Defender for Office 365. For more information, see [Permissions in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-office-365/mdo-portal-permissions).

<sup>\*</sup>Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

Audit logging must be turned on for your Microsoft 365 environment \(it's on by default\). To verify that audit logging is turned on or to turn it on, see [Turn auditing on or off](https://learn.microsoft.com/en-us/purview/audit-log-enable-disable).

## See also

[Office 365 threat investigation and response](https://learn.microsoft.com/en-us/defender-office-365/office-365-ti)

[Automated investigation and response \(AIR\) in Office 365](https://learn.microsoft.com/en-us/defender-office-365/air-about)
