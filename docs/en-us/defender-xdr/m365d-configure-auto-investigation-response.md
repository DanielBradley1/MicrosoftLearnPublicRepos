<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/m365d-configure-auto-investigation-response -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Configure automated investigation and response capabilities in Microsoft Defender XDR

Microsoft Defender XDR includes powerful [automated investigation and response capabilities](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir) that can save your security operations team much time and effort. With [self-healing](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir#how-automated-investigation-and-self-healing-works), these capabilities mimic the steps a security analyst would take to investigate and respond to threats, only faster, and with more ability to scale.

This article describes how to configure automated investigation and response in [Microsoft Defender XDR](https://go.microsoft.com/fwlink/p/?linkid=2077139) with these steps:

1. [Review the prerequisites](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).
2. [Review or change the automation level for device groups](#review-or-change-the-automation-level-for-device-groups).
3. [Review your security and alert policies in Office 365](#review-your-security-and-alert-policies-in-office-365).

After configuring automated investigation and response, you can [view and manage remediation actions in the Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir-actions) and [update automated investigation settings](#need-to-make-changes-to-automated-investigation-settings) as needed.

## Prerequisites for automated investigation and response in Microsoft Defender XDR

The following table lists the requirements for automated investigation and response in Microsoft Defender XDR.

| Requirement | Details |
| --- | --- |
| Subscription requirements | One of these subscriptions:<br><br>- Microsoft 365 E5<br>- Microsoft 365 A5<br>- Microsoft 365 E3 with the Microsoft Defender Suite add-on<br>- Microsoft 365 A3 with the Microsoft 365 A5 Security add-on<br>- Office 365 E5 plus Enterprise Mobility + Security E5 plus Windows E5<br><br>  <br>See [Microsoft Defender XDR licensing requirements](https://learn.microsoft.com/en-us/defender-xdr/prerequisites#licensing-requirements). |
| Network requirements | - [Microsoft Defender for Identity](https://learn.microsoft.com/en-us/azure-advanced-threat-protection/what-is-atp) enabled<br>- [Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/what-is-cloud-app-security) configured<br>- [Microsoft Defender for Identity integration](https://learn.microsoft.com/en-us/cloud-app-security/mdi-integration) |
| Windows device requirements | - Windows 11<br>- Windows 10, version 1709 or later installed \(See [Windows release information](https://learn.microsoft.com/en-us/windows/release-information/)\)<br>- The following threat protection services are configured:<br><br>  - [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-windows-client)<br>  - [Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features) |
| Protection for email content and Office files | - [Microsoft Defender for Office 365 is configured](https://learn.microsoft.com/en-us/defender-office-365/mdo-deployment-guide#step-2-configure-protection-policies)<br>- [Automated investigation and remediation capabilities in Defender for Endpoint are configured](https://learn.microsoft.com/en-us/defender-endpoint/configure-automated-investigations-remediation) \(required for manual response actions, such as deleting email messages on devices\) |
| Permissions | To configure automated investigation and response capabilities, you must have one of the following roles assigned in either Microsoft Entra ID \([https://portal.azure.com](https://portal.azure.com)\) or in the Microsoft 365 admin center \([https://admin.microsoft.com](https://admin.microsoft.com)\):<br><br>- Security Administrator or higher<br><br>To work with automated investigation and response capabilities, such as by reviewing, approving, or rejecting pending actions, see [Required permissions for Action center tasks](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center#required-permissions-for-action-center-tasks). |

## Review or change the automation level for device groups

Whether automated investigations run, and whether remediation actions are taken automatically or only upon approval for your devices depend on certain settings, such as your organization's device group policies. Review the configured automation level for your device group policies. You must be at least a security administrator to perform the following procedure:

1. Go to the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com) and sign in.
2. Go to **System** > **Settings** > **Endpoints** > **Device groups** under **Permissions**.
3. Review your device group policies. In particular, look at the **Remediation level** column. We recommend using **Full - remediate threats automatically**. You might need to create or edit your device groups to get the level of automation you want. To get help creating or editing device groups, see the following articles:

   - [How threats are remediated](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations#how-threats-are-remediated)
   - [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups)

## Review your security and alert policies in Office 365

Microsoft provides built-in [alert policies](https://learn.microsoft.com/en-us/defender-xdr/alert-policies) that help identify certain risks. These risks include Exchange admin permissions abuse, malware activity, potential external and internal threats, and data lifecycle management risks. Some alerts can trigger [automated investigation and response in Office 365](https://learn.microsoft.com/en-us/defender-office-365/air-about). Make sure your [Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about) features are configured correctly.

Although certain alerts and security policies can trigger automated investigations, *no remediation actions are taken automatically for email and content*. Instead, all remediation actions for email and email content await approval by your security operations team in the [Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center).

[The built-in security features for all cloud mailboxes](https://learn.microsoft.com/en-us/defender-office-365/eop-about) and Defender for Office 365 help protect email and content. We recommend using the Standard and Strict [preset security policies](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies#preset-security-policies-in-eop-and-microsoft-defender-for-office-365) to assign protection to users.

If you're using custom policies, use the [Configuration analyzer](https://learn.microsoft.com/en-us/defender-office-365/configuration-analyzer-for-security-policies) to compare your policy settings to the Standard and Strict preset security policy settings. For a detailed listing of all policy settings, see the tables in [Recommended email and collaboration threat policy settings for cloud organizations](https://learn.microsoft.com/en-us/defender-office-365/recommended-settings-for-eop-and-office365).

You can review your [alert policies](https://learn.microsoft.com/en-us/defender-office-365/alert-policies-defender-portal) in the Defender portal at [https://security.microsoft.com](https://security.microsoft.com) > **Policies & rules** > **Alert policy** or directly at [https://security.microsoft.com/alertpoliciesv2](https://security.microsoft.com/alertpoliciesv2). Several default alert policies are in the **Threat management** category. Some of the alert policies in the **Threat management** category can trigger automated investigation and response. To learn more, see [Threat management alert policies](https://learn.microsoft.com/en-us/defender-xdr/alert-policies#threat-management-alert-policies).

## Change automated investigation settings

You can choose from several options to change settings for your automated investigation and response capabilities. Some options are listed in the following table:

| To do this | Follow these steps |
| --- | --- |
| Specify automation levels for groups of devices | 1. Set up one or more device groups. See [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).<br>2. In the Microsoft Defender portal, go to **Permissions** > **Endpoints roles & groups** > **Device groups**.<br>3. Select a device group and review its **Automation level** setting. \(We recommend using **Full - remediate threats automatically**\). See [Automation levels in automated investigation and remediation capabilities](https://learn.microsoft.com/en-us/defender-endpoint/automation-levels).<br>4. Repeat steps 2 and 3 as appropriate for all your device groups. |

## Next steps

Learn more about automated investigation and response capabilities in Microsoft Defender XDR.

### Related content

- [Remediation actions in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-remediation-actions)
- [Visit the Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
