<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/alert-policies-defender-portal -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Alert policies in the Microsoft Defender portal

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

In organizations with cloud mailboxes, alert policies generate alerts in the alert dashboard when users take actions that match the conditions of the policy. There are many default alert policies that help you monitor activities. For example, default alert policies can monitor assigning admin privileges in Exchange Online, malware attacks, phishing campaigns, and unusual levels of file deletions and external sharing.

This article explains how to view and create alert policies on the **Alert policy** page in the Microsoft Defender portal. Before you begin, review the [prerequisites](#what-do-you-need-to-know-before-you-begin) for required permissions.

## What do you need to know before you begin?

Review the following prerequisites before you view or manage alert policies.

- You need to be assigned permissions before you can view or manage alert policies. You have the following options:

  - [Microsoft Defender XDR Unified role based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac) \(If **Email & collaboration** > **Defender for Office 365** permissions is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **Active**. Affects the Defender portal only, not PowerShell\):

    - *Read only access to the Alert policies page*: **Security operations / Security data / Security data basics \(read\)**.
    - *Manage alert policies*: **Authorization and settings / Security settings / Detection tuning \(manage\)**.

  - [Email & collaboration permissions in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-office-365/mdo-portal-permissions):

    - *Create and manage alert policies in the Threat management category*: Membership in the **Organization Management** or **Security Administrator** role groups.
    - *View alerts in the Threat management* category: Membership in the **Security Reader** role group.

  - [Microsoft Entra permissions](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal): Membership in the **Global Administrator**<sup>\*</sup>, **Security Administrator**, or **Security Reader** roles gives users the required permissions and permissions for other features in Microsoft 365.

    Important

    \<sup>\*</sup> Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

- For information about other alert policy categories, see [Permissions required to view alerts](https://learn.microsoft.com/en-us/defender-xdr/alert-policies#rbac-permissions-required-to-view-alerts).

## Built-in alert tuning rules

Microsoft Defender includes built-in alert tuning rules that help reduce reporting noise from common benign activity. These built-in rules suppress alerts without affecting other features like AIR investigations and email notifications. If the AIR investigation detects malicious or suspicious activity, the new alert is reactivated.

To see the built-in alert tuning rules in the [Microsoft Defender portal](https://security.microsoft.com), go to **System** > **Settings** > **Microsoft Defender XDR** > **Rules** section > **Alert tuning** or directly on the **Alert tuning** page at [https://security.microsoft.com/securitysettings/defender/alert\_suppression](https://security.microsoft.com/securitysettings/defender/alert_suppression).

Be sure to review these rules to understand how they might affect which alerts appear in the Microsoft Defender portal.

Important

Built-in alert tuning rules don't apply to alerts from [custom detection rules](https://learn.microsoft.com/en-us/defender-xdr/custom-detections-overview) and [Custom TI](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview).

Note

The [Microsoft Security Copilot Phishing Triage Agent](https://learn.microsoft.com/en-us/defender-xdr/phishing-triage-agent) doesn't classify alerts suppressed by [alert tuning](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts#tune-an-alert). Be sure to disable the **Auto-Resolve - Email reported by user as malware or phish** built-in alert tuning rule and any custom tuning rules that suppress this alert.

## Open alert policies

In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Policies & rules** > **Alert policy**. Or, to go directly to the **Alert policy** page, use [https://security.microsoft.com/alertpoliciesv2](https://security.microsoft.com/alertpoliciesv2).

On the **Alert policy** page, you can view and create alert policies. For more information, see [Alert policies in Microsoft 365](https://learn.microsoft.com/en-us/defender-xdr/alert-policies)

## Related content

[Manage incidents and alerts from Microsoft Defender for Office 365 in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-office-365/mdo-sec-ops-manage-incidents-and-alerts)
