<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/priority-accounts-turn-on-priority-account-protection -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Configure and review priority account protection in Microsoft Defender for Office 365

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

In Microsoft 365 organizations with Microsoft Defender for Office 365 Plan 2, *priority account protection* is a differentiated level of protection applied to accounts that have the **Priority account** tag applied to them. For more information about the Priority account tag and how to apply it to users, see [Manage and monitor priority accounts](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/priority-accounts).

Priority account protection offers extra heuristics tailored to company executives that don't benefit regular users. Priority account protection is better suited to the mail flow patterns of company executives based on extensive data from the Microsoft datacenters.

By default, priority account protection is turned on in organizations with Defender for Office 365 Plan 2. This default behavior means an account tagged as a Priority account automatically receives priority account protection.

The following sections explain how to verify or enable priority account protection and where to view its results.

## What do you need to know before you begin?

Before you begin, make sure you have access to the Microsoft Defender portal and the required permissions.

- You open the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com).
- You need to be assigned permissions before you can do the procedures in this section. You have the following options:

  - [Microsoft Defender XDR Unified role based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac) \(If **Email & collaboration** > **Defender for Office 365** permissions is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **Active**. Affects the Defender portal only, not PowerShell\): **Authorization and settings/System settings/Read and manage** or **Authorization and settings/System settings/Read-only**.
  - [Exchange Online permissions](https://learn.microsoft.com/en-us/exchange/permissions-exo/permissions-exo): Membership in the **Organization Management** or **Security Administrator** role groups.
  - [Microsoft Entra permissions](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal): Membership in the **Global Administrator**<sup>\*</sup> or **Security Administrator** roles gives users the required permissions *and* permissions for other features in Microsoft 365.

    Important

    \<sup>\*</sup> Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

- Priority account protection is applied to accounts that have the **Priority account** tag applied to them. For instructions, see [Manage and monitor priority accounts](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/priority-accounts).
- The Priority account tag is a type of *user tag*. You can create custom user tags to differentiate specific groups of users in reporting and other features. For more information about user tags, see [User tags in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/user-tags-about).
- To use the PowerShell procedures in this section, connect to [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell).

## Review or turn on priority account protection in the Microsoft Defender portal

Note

We don't recommend turning off priority account protection.

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Settings** > **Email & collaboration** > **Priority account protection**. Or, to go directly to the **Priority account protection** page, use [https://security.microsoft.com/securitysettings/priorityAccountProtection](https://security.microsoft.com/securitysettings/priorityAccountProtection).
2. On the **Priority account protection** page, verify that **Priority account protection** is turned on \(![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) \).

   [![Turn on Priority account protection.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-priority-account-protection.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-priority-account-protection.png#lightbox)

### Review or turn on priority account protection in Exchange Online PowerShell

If you'd rather use PowerShell to verify that priority account protection is turned on, run the following command in [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-EmailTenantSettings | Format-List Identity,EnablePriorityAccountProtection
```

The value True for the EnablePriorityAccountProtection property means priority account protection is turned on. The value False means priority account protection is turned off.

To turn on priority account protection, run the following command:

```powershell
Set-EmailTenantSettings -EnablePriorityAccountProtection $true
```

For detailed syntax and parameter information, see [Get-EmailTenantSettings](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/get-emailtenantsettings) and [Set-EmailTenantSettings](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/set-emailtenantsettings).

## Review differentiated protection from priority account protection

The effects of priority account protection are visible in the following reporting features:

- [Threat protection status report](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#threat-protection-status-report)

  - [View data by Email > Phish and Chart breakdown by Detection Technology](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#view-data-by-email--phish-and-chart-breakdown-by-detection-technology)
  - [View data by Email > Spam and Chart breakdown by Detection Technology](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#view-data-by-email--spam-and-chart-breakdown-by-detection-technology)
  - [View data by Email > Malware and Chart breakdown by Detection Technology](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#view-data-by-email--malware-and-chart-breakdown-by-detection-technology)
  - [Chart breakdown by Policy type](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#chart-breakdown-by-policy-type)
  - [Chart breakdown by Delivery status](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#chart-breakdown-by-delivery-status)

- [Threat Explorer and real-time detections](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about)
- [Email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page)

For information about where the Priority account tag and other user tags are available as filters, see [User tags in reports and features](https://learn.microsoft.com/en-us/defender-office-365/user-tags-about#user-tags-in-reports-and-features).

### Threat protection status report

The **Threat protection status** report brings together information about malicious content and malicious email detected and blocked by the built-in protections in Microsoft 365 and by Defender for Office 365. For more information, see [Threat protection status report](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#threat-protection-status-report).

In the **Email > Phish**, **Email > Spam**, **Email > Malware**, **Policy type**, and **Delivery status** views of the report, the option **Priority account protection** and the value **Yes** is available when you select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-filter.png) **Filter**. This option allows you to filter the data in the report by priority account protection detections.

### Threat Explorer

For more information about Threat Explorer, see [Threat Explorer and Real-time detections](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about).

To view the results of priority account protection in Threat Explorer, do the following steps:

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Explorer**. Or, to go directly to the **Explorer** page, use [https://security.microsoft.com/threatexplorer](https://security.microsoft.com/threatexplorer).
2. On the **Explorer** page, on the **All email**, **Malware**, or **Phish** tabs, select **Context** > **Equal any of** > **Priority account protection**, and then select **Refresh**.

   [![Context filter within Threat Explorer.](https://learn.microsoft.com/en-us/defender-office-365/media/threat-explorer-context-filter.png)](https://learn.microsoft.com/en-us/defender-office-365/media/threat-explorer-context-filter.png#lightbox)

### Email entity page

The Email entity page is available from many locations in the Defender portal, including **Threat Explorer** \(also known as **Explorer**\). For more information, see [The Email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page).

On the Email entity page, select the **Analysis** tab. **Priority account protection** is listed in the **Threat detection details** section.

[![The Analysis tab of the Email entity page showing Priority account protection results.](https://learn.microsoft.com/en-us/defender-office-365/media/email-entity-priority-account-protection.png)](https://learn.microsoft.com/en-us/defender-office-365/media/email-entity-priority-account-protection.png#lightbox)

## Related content

- [User tags in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/user-tags-about)
- [Manage and monitor priority accounts](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/priority-accounts)
