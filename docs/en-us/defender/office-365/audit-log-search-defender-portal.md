<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/audit-log-search-defender-portal -->
<!-- Sitemap-Last-Modified: 2026-08-19 -->

# Audit log search in the Microsoft Defender portal

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

## Overview

In all organizations with cloud mailboxes, the unified audit log records supported user and admin operations. Audit records for these events are searchable by security ops, IT admins, insider risk teams, and compliance and legal investigators in the organization. This capability provides visibility into the activities performed across your Microsoft 365 organization.

This article describes how to open and start an audit log search in the Microsoft Defender portal, including the required permissions and links to detailed search instructions. Before you begin, review the [prerequisites](#what-do-you-need-to-know-before-you-begin) to verify that you have the necessary permissions.

Tip

Audit log search in Microsoft Defender portal is identical to audit log search in the Microsoft Purview portal at [https://purview.microsoft.com/auditlogsearch](https://purview.microsoft.com/auditlogsearch).

## What do you need to know before you begin?

Review the following prerequisites before you search the audit log.

- You need to be assigned permissions before you can do the procedures in this article. You have the following options:

  - [Exchange Online permissions](https://learn.microsoft.com/en-us/exchange/permissions-exo/permissions-exo): Membership in the **Organization Management** or **Compliance Management** role groups.
  - [Microsoft Entra permissions](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal): Membership in the **Global Administrator**<sup>\*</sup> or **Compliance Administrator** roles gives users the required permissions *and* permissions for other features in Microsoft 365.

    Important

    \<sup>\*</sup> Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

## Open audit log search

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Audit**. Or, to go directly to the **Audit** page, use [https://security.microsoft.com/auditlogsearch](https://security.microsoft.com/auditlogsearch).
2. On the **Audit** page, create the audit log search. For instructions, see [Audit New Search](https://learn.microsoft.com/en-us/purview/audit-new-search) or [Use a PowerShell script to search the audit log](https://learn.microsoft.com/en-us/purview/audit-log-search-script).

## Related content

[Search the audit log for events in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-xdr-auditing)
