<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/defender-office-365-unified-rbac-permissions -->
<!-- Sitemap-Last-Modified: 2026-07-10 -->

# Unified RBAC permissions for Microsoft Defender for Office 365

Use this quick reference to find the Microsoft Defender unified role-based access control \(RBAC\) permissions that are required for Microsoft Defender for Office 365 features in the Microsoft Defender portal:

- Find the exact permission that's required for a feature.
- Build custom roles based on specific Defender for Office 365 tasks.
- Understand what's in scope and out of scope for Unified RBAC.

For step-by-step configuration guidance, see [How to configure Unified RBAC for Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/configure-unified-rbac-defender-office-365). For all Unified RBAC permissions, see [Permissions in Microsoft Defender unified RBAC](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details).

Important

Starting July 2026, Unified RBAC is the default permission model for new Microsoft Defender for Office 365 Plan 2 organizations. The legacy Email & collaboration roles page isn't available for those organizations. Existing organizations can manually activate Unified RBAC at any time. For more information, see [MC1246006](https://admin.microsoft.com/Adminportal/Home#/MessageCenter/:/messages/MC1246006).

## Scope and constraints

Unified RBAC applies only to the Defender portal at [https://security.microsoft.com](https://security.microsoft.com). Unified RBAC doesn't apply to:

- The Exchange admin center.
- The Microsoft Purview portal.
- PowerShell \(uses [Exchange Online RBAC](https://learn.microsoft.com/en-us/exchange/permissions-exo/permissions-exo)\).

Microsoft Entra roles \(for example, Security Administrator\) always grant access regardless of Unified RBAC activation.

## Quick lookup

The following table maps common tasks to the required Unified RBAC permission:

| Task | Required permission |
| --- | --- |
| View threat policies | Core security settings \(read\) |
| Edit threat policies | Core security settings \(manage\) |
| View email in Threat Explorer | Email & collaboration metadata \(read\) |
| Preview email content | Email & collaboration content \(read\) |
| Remediate emails | Email & collaboration advanced actions \(manage\) |
| Manage quarantine | Email & collaboration quarantine \(manage\) |
| Submit messages to Microsoft | Response \(manage\) |
| View incidents and alerts | Security data basics \(read\) |
| Manage incidents | Alerts \(manage\) |
| Approve automated investigation actions | Response \(manage\) |
| Manage Tenant Allow/Block List entries | Detection tuning \(manage\) |
| Manage user tags | System settings \(manage\) |
| Run advanced hunting queries | Security data basics \(read\) |
| Take actions from advanced hunting | Response \(manage\) and Email & collaboration advanced actions \(manage\) |

## Defender for Office 365 permissions

The following tables list the Unified RBAC permissions that apply to Defender for Office 365 features, grouped by permission category.

### Security operations – Security data

For detailed permission descriptions, see [Security operations – Security data](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details#security-operations--security-data).

| Permission | Level | What it enables |
| --- | --- | --- |
| Security data basics | Read | View incidents, alerts, investigations, advanced hunting data, submissions, and reports |
| Alerts | Manage | Manage alerts, start automated investigations, classify and assign incidents |
| Response | Manage | Approve or dismiss remediation actions, submit messages to Microsoft, manage automation lists |
| Email & collaboration quarantine | Manage | View and release quarantined email and Teams messages |
| Email & collaboration advanced actions | Manage | Move or delete email \(soft delete and hard delete\), remediate from Threat Explorer |

### Security operations – Raw data \(Email & collaboration\)

For detailed permission descriptions, see [Security operations – Raw data \(Email & collaboration\)](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details#security-operations--raw-data-email--collaboration).

| Permission | Level | What it enables |
| --- | --- | --- |
| Email & collaboration metadata | Read | View email and collaboration data in Threat Explorer, email entity page, campaigns, threat trackers, and advanced hunting |
| Email & collaboration content | Read | View and download email content and attachments |
| Email & collaboration content: Emails associated with alerts | Read | View and download email content associated with the security alerts **Email reported by user as malware or phish** and **Email reported by user as junk** |
| Email & collaboration content: Quarantine Emails | Read | View and download quarantined messages for all users |

### Authorization and settings

For detailed permission descriptions, see [Authorization and settings](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details#authorization-and-settings).

| Permission | Level | What it enables |
| --- | --- | --- |
| Core security settings | Read | View threat policies, quarantine policies, preset security policies, DKIM/DMARC/SPF settings, Configuration Analyzer, and user-reported settings |
| Core security settings | Manage | Configure threat policies, quarantine policies, preset security policies, DKIM/DMARC/SPF settings, and user-reported settings |
| Detection tuning | Manage | Manage alert policies, custom detections, Tenant Allow/Block List entries |
| System settings | Read | View user tags and priority account tags |
| System settings | Manage | Manage user tags and priority account tags |

## Feature-to-permission mapping

The following tables show the required permission for each Defender for Office 365 experience in the Defender portal.

### Threat policies and protection

All threat policy features use **Core security settings** \(read to view, manage to configure\):

- [Anti-phishing policies](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-policies-mdo-configure)
- [Anti-spam policies](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-configure)
- [Anti-malware policies](https://learn.microsoft.com/en-us/defender-office-365/anti-malware-policies-configure)
- [Safe Links policies](https://learn.microsoft.com/en-us/defender-office-365/safe-links-policies-configure)
- [Safe Attachments policies](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-policies-configure)
- [Outbound spam policies](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-policies-configure)
- [Connection filter policies](https://learn.microsoft.com/en-us/defender-office-365/connection-filter-policies-configure)
- [Preset security policies](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies)
- [Configuration Analyzer](https://learn.microsoft.com/en-us/defender-office-365/configuration-analyzer-for-security-policies)
- Email authentication settings \([SPF](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-spf-configure), [DKIM](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dkim-configure), and [DMARC](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dmarc-configure)\).
- [Safe Attachments for SharePoint, OneDrive, and Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-for-spo-odfb-teams-configure)
- [Quarantine policies](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies)

Note

Mail flow connectors are outside Unified RBAC scope and are controlled by Exchange Online roles.

### Threat investigation and hunting

For more information about these experiences, see [Advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview).

| Experience | Task | Permission required |
| --- | --- | --- |
| [Threat Explorer](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about) | View email metadata | Email & collaboration metadata \(read\) |
|  | View email content | Email & collaboration content \(read\) |
|  | Remediate emails | Email & collaboration advanced actions \(manage\) |
| [Email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page) | View metadata | Email & collaboration metadata \(read\) |
|  | View content | Email & collaboration content \(read\) |
|  | View content for emails associated with alerts | Email & collaboration content: Emails associated with alerts \(read\) |
|  | View quarantined messages | Email & collaboration content: Quarantine Emails \(read\) |
| [Campaigns](https://learn.microsoft.com/en-us/defender-office-365/campaigns) | View campaign data | Email & collaboration metadata \(read\) |
| [Threat trackers](https://learn.microsoft.com/en-us/defender-office-365/threat-trackers) | View tracker data | Email & collaboration metadata \(read\) |
| [Advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) | Read data | Security data basics \(read\) |
|  | Take actions | Response \(manage\) and Email & collaboration advanced actions \(manage\) |

### Incidents, alerts, and response

For more information about these experiences, see [Manage incidents and alerts](https://learn.microsoft.com/en-us/defender-office-365/mdo-sec-ops-manage-incidents-and-alerts).

| Experience | Task | Permission required |
| --- | --- | --- |
| [Incidents and alerts](https://learn.microsoft.com/en-us/defender-office-365/mdo-sec-ops-manage-incidents-and-alerts) | View | Security data basics \(read\) |
|  | Classify, assign, and comment | Alerts \(manage\) |
| [Alert policies](https://learn.microsoft.com/en-us/defender-office-365/alert-policies-defender-portal) | Manage | Detection tuning \(manage\) |
| [Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center) | View | Security data basics \(read\) |
|  | Approve or dismiss actions | Response \(manage\) |
| [Automated investigation and response](https://learn.microsoft.com/en-us/defender-office-365/air-about) | View | Security data basics \(read\) |
|  | Approve | Response \(manage\) |

### Quarantine and submissions

For more information about these experiences, see [Manage quarantined messages](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files) and [Admin submissions](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin).

| Experience | Task | Permission required |
| --- | --- | --- |
| [Quarantine](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files) | View | Security data basics \(read\) |
|  | Release or delete messages | Email & collaboration quarantine \(manage\) |
|  | Submit from quarantine | Response \(manage\) |
| [Submissions](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin) | View | Security data basics \(read\) |
|  | Submit messages to Microsoft | Response \(manage\) |
| [User-reported settings](https://learn.microsoft.com/en-us/defender-office-365/submissions-user-reported-messages-custom-mailbox) | View | Core security settings \(read\) |
|  | Configure | Core security settings \(manage\) |

### Tenant Allow/Block List

For more information, see [Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-about).

| Experience | Permission required |
| --- | --- |
| View entries | Core security settings \(read\) |
| Add, modify, or delete entries | Detection tuning \(manage\) |

### Reports and monitoring

For more information, see [Email security reports](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security).

| Experience | Permission required |
| --- | --- |
| Defender for Office 365 reports | Security data basics \(read\) |
| Email security reports | Security data basics \(read\) |
| Threat analytics | Security data basics \(read\) |

Note

[Mail flow reports](https://learn.microsoft.com/en-us/exchange/monitoring/mail-flow-reports/mail-flow-reports) and [message trace](https://learn.microsoft.com/en-us/defender-office-365/message-trace-defender-portal) are Exchange Online experiences outside the security portal. They're outside Unified RBAC permission scope and are controlled by [Exchange Online roles](https://learn.microsoft.com/en-us/exchange/permissions-exo/permissions-exo).

### User tags

For more information, see [User tags](https://learn.microsoft.com/en-us/defender-office-365/user-tags-about).

| Experience | Permission required |
| --- | --- |
| View user tags | System settings \(read\) |
| Manage user tags | System settings \(manage\) |
| Manage priority account tags | System settings \(manage\) |

### Microsoft Teams protection

For more information, see [Microsoft Teams protection](https://learn.microsoft.com/en-us/defender-office-365/mdo-support-teams-about). Microsoft Teams protection uses the same permissions as email features:

| Experience | Permission required |
| --- | --- |
| View Teams message data | Email & collaboration metadata \(read\) |
| Quarantine Teams messages | Email & collaboration quarantine \(manage\) |
| Submit Teams messages | Response \(manage\) |

## Experiences outside Unified RBAC scope

The following features aren't controlled by Unified RBAC. Use the specified alternative permission model:

| Feature | Permission model |
| --- | --- |
| Attack Simulation Training | Microsoft Entra roles |
| Remove users from Teams chats | Microsoft Entra roles |
| Message trace | Exchange Online roles |
| Mail flow reports | Exchange Online roles |
| Mail flow connectors | Exchange Online roles |
| PowerShell cmdlets | Exchange Online roles |

## Inverse permission matrix

Use this section to understand what experiences each permission enables.

### Security data basics \(read\)

- Incidents and alerts \(view\)
- Action center \(view\)
- Automated investigation and response \(view\)
- Quarantine \(view\)
- Submissions \(view\)
- Reports and threat analytics
- Advanced hunting \(read data\)
- Teams data access

### Alerts \(manage\)

- Incident classification, assignment, and commenting

### Response \(manage\)

- Approve or dismiss remediation actions \(automated investigation and response, Action center\)
- Submit messages to Microsoft
- Advanced hunting actions

### Email & collaboration quarantine \(manage\)

- Release or delete quarantined email and Teams messages

### Email & collaboration advanced actions \(manage\)

- Remediate emails \(Threat Explorer, email entity page\)
- Advanced hunting actions \(with Response \(manage\)\)

### Email & collaboration metadata \(read\)

- Threat Explorer \(email metadata\)
- Email entity page
- Campaigns
- Threat trackers
- Teams entity panel

### Email & collaboration content \(read\)

- Email preview
- Attachment access

### Core security settings \(read/manage\)

- All threat policy and configuration experiences \(read to view, manage to configure\)

### Detection tuning \(manage\)

- Alert policies
- Tenant Allow/Block List modifications

### System settings \(read/manage\)

- User tags
- Priority account tags

## Frequently asked questions

Common questions about Unified RBAC for Defender for Office 365:

- **Q: Who can activate Unified RBAC?**

  A: Global Administrator or Security Administrator in Microsoft Entra ID.
- **Q: Does Unified RBAC affect the Exchange admin center?**

  A: No. The Exchange admin center uses its own role-based access control.
- **Q: Does PowerShell use Unified RBAC?**

  A: No. PowerShell cmdlets continue to use [Exchange Online RBAC](https://learn.microsoft.com/en-us/exchange/permissions-exo/permissions-exo).
- **Q: Can I import legacy Email & collaboration roles?**

  A: Yes. Use the import feature in the Defender portal. For more information, see [Import existing roles](https://learn.microsoft.com/en-us/defender-xdr/import-rbac-roles).
- **Q: Can I scope roles to Defender for Office 365 only?**

  A: Yes. When you create or edit a role, select **Defender for Office 365** as the data source.
- **Q: What do I need before I activate Unified RBAC?**

  A: Review the activation prerequisites before you turn on Unified RBAC. For more information, see [Prerequisites to activate Microsoft Defender unified RBAC](https://learn.microsoft.com/en-us/defender-xdr/activate-defender-rbac#prerequisites).
- **Q: Does Unified RBAC support Privileged Identity Management \(PIM\)?**

  A: Yes. Assign Unified RBAC roles to PIM-managed groups.

## Related content

- [How to configure Unified RBAC for Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/configure-unified-rbac-defender-office-365)
- [Permissions in Microsoft Defender unified RBAC](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details)
- [Create custom roles in Microsoft Defender unified RBAC](https://learn.microsoft.com/en-us/defender-xdr/create-custom-rbac-roles)
- [Activate Microsoft Defender unified RBAC](https://learn.microsoft.com/en-us/defender-xdr/activate-defender-rbac)
- [Import existing roles to Microsoft Defender unified RBAC](https://learn.microsoft.com/en-us/defender-xdr/import-rbac-roles)
