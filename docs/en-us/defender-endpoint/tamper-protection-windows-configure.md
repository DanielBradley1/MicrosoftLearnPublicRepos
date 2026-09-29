<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-windows-configure -->
<!-- Sitemap-Last-Modified: 2026-09-08 -->

# Configure tamper protection for Microsoft Defender Antivirus on Windows

[Tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview) helps prevent certain security settings, such as virus and threat protection, from being disabled or changed. Use the methods described in this article to configure tamper protection for Microsoft Defender Antivirus on Windows devices.

To configure tamper protection for Microsoft Defender for Endpoint on macOS, see [Configure tamper protection for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-macos-configure).

To protect organization-managed Microsoft Defender Antivirus exclusion lists from unauthorized changes, see [Protect Microsoft Defender Antivirus exclusions with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-antivirus-exclusions).

For answers to common questions, see [Frequently asked questions about tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-faq). For help with blocked settings and exclusion protection, see [Troubleshoot problems with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-troubleshoot).

Important

When tamper protection is turned on, [tamper-protected settings](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview#what-happens-when-tamper-protection-is-turned-on) can't be changed. Changes to these settings might appear to succeed, but tamper protection blocks the changes. Use [troubleshooting mode](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable) to temporarily disable tamper protection when you need to change a protected setting.

A policy that manages tamper protection takes precedence over the organization-wide setting in the Microsoft Defender portal. A policy or portal setting also takes precedence over a setting that a local administrator configures in the Windows Security app.

## Prerequisites

For operating system, product version, licensing, permissions, and device-management requirements, see [Requirements for tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview#requirements-for-tamper-protection).

## Configure tamper protection in Microsoft Intune

Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

To configure tamper protection in Intune, use an endpoint security **Antivirus** policy. For detailed instructions, see [Create endpoint security policies](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-policy#create-endpoint-security-policies) or [Modify existing policies](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies#modify-existing-policies) \(links open new tabs in the Intune documentation\).

Assign the policy to your entire organization or to selected user or device groups. You can also exclude specific groups from the policy assignment.

When you create the policy, use these specific settings:

- **Policy type**: Go to **Manage** > **Antivirus** on the **Endpoint security \| Overview** page at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Workflows/SecurityManagementMenu/~/overview](https://intune.microsoft.com/#view/Microsoft_Intune_Workflows/SecurityManagementMenu/%7E/overview), and then select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-create.png) **Create policy**.
- **Platform**: Select **Windows**.
- **Profile**: Select **Windows Security Experience**.

When you create or modify the policy, use these specific settings on the **Configuration settings** tab:

- **Tamper protection \(device\)** in the **Defender** section: Select **On**.

## Configure tamper protection in the Microsoft Defender portal

Note

Tamper protection is on by default for new deployments as part of [built-in protection](https://learn.microsoft.com/en-us/defender-endpoint/built-in-protection).

If tamper protection is deployed and managed through Intune, the Intune policy takes precedence. Changing the setting in the Defender portal doesn't change the policy-managed state. Instead, the Defender portal setting restricts tamper-protected settings to their secure default values.

On the **Advanced features** page in the Microsoft Defender portal at [https://security.microsoft.com/preferences2/endpoints](https://security.microsoft.com/preferences2/endpoints), slide the **Tamper protection** toggle to ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-on.png) **On** or ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-off.png) **Off**.

[![Screenshot of tamper protection turned on in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender/media/mde-turn-tamperprotectionon.png)](https://learn.microsoft.com/en-us/defender/media/mde-turn-tamperprotectionon.png#lightbox)

## Configure tamper protection using Microsoft Configuration Manager

Note

Configuration Manager doesn't support configuring tamper protection directly. Use [tenant attach](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/endpoint-security-get-started) to deploy the setting from the Intune admin center. Tenant attach synchronizes on-premises Configuration Manager devices with the Microsoft Intune admin center so you can deploy endpoint security policies to device collections.

To configure tamper protection for tenant-attached devices, use an endpoint security **Antivirus** policy. For detailed instructions, see [Create endpoint security policies](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-policy#create-endpoint-security-policies) or [Modify existing policies](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies#modify-existing-policies) \(links open new tabs in the Intune documentation\).

When you create the policy, use these specific settings:

- **Policy type**: Go to **Manage** > **Antivirus** on the **Endpoint security \| Overview** page at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Workflows/SecurityManagementMenu/~/overview](https://intune.microsoft.com/#view/Microsoft_Intune_Workflows/SecurityManagementMenu/%7E/overview), and then select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-create.png) **Create policy**.
- **Platform**: Select **Windows \(ConfigMgr\)**.
- **Profile**: Select **Windows Security experience \(ConfigMgr\)**.

When you create or modify the policy, use these specific settings on the **Configuration settings** tab:

- **Enable tamper protection to prevent Microsoft Defender from being disabled** in the **Windows Security** section: Select **Enabled**.

![Screenshot of Windows Security settings with tamper protection enabled.](https://learn.microsoft.com/en-us/defender-endpoint/media/tamper-protect-configmgr.png)

## Configure tamper protection using the Windows Security app

You can use the [Windows Security app](https://support.microsoft.com/Windows/Security/Windows-Security/stay-protected-with-the-windows-security-app) to configure tamper protection on an individual device.

Use the following steps to turn tamper protection on or off:

1. In the **Windows Security** app on the device, go to **Virus & threat protection**.
2. In the **Virus & threat protection** pane, in the **Virus & threat protection settings** section, select **Manage settings**.
3. In the **Virus & threat protection settings** pane, slide the **Tamper Protection** toggle to ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-on.png) **On** or ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-off.png) **Off**.

   [![Screenshot of tamper protection turned on in the Windows Security app.](https://learn.microsoft.com/en-us/defender-endpoint/media/tamperprotectionturnedon.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/tamperprotectionturnedon.png#lightbox)

## Configure tamper protection using PowerShell

You can't use PowerShell to configure tamper protection during normal operation.

### Temporarily disable tamper protection using PowerShell

The PowerShell command to temporarily disable tamper protection works only while the device is in [Defender for Endpoint troubleshooting mode](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable).

For instructions, see [Temporarily disable tamper protection using PowerShell](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable#temporarily-disable-tamper-protection-using-powershell).

### Determine the status of tamper protection and real-time protection using PowerShell

To determine the current status of tamper protection and real-time protection on a device, run the following command:

```powershell
Get-MpComputerStatus | Select-Object IsTamperProtected, RealTimeProtectionEnabled
```

The value `True` means the setting is enabled. The value `False` means the setting is disabled.

## Related content

- [Tamper protection overview](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview)
- [Protect Microsoft Defender Antivirus exclusions with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-antivirus-exclusions)
- [Frequently asked questions on tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-faq)
- [Troubleshoot problems with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-troubleshoot)
- [Configure tamper protection for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-macos-configure)
