<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-updates -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Create a custom gradual rollout process for Microsoft Defender updates

Create a custom gradual rollout process to control when Windows devices receive Microsoft Defender Antivirus platform, engine, and security intelligence updates. Use Group Policy, Microsoft Intune, or PowerShell to assign update channels based on your validation and production needs. Before you begin, verify the platform version in [Prerequisites](#prerequisites).

> Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

## Prerequisites

Before you configure a custom gradual rollout process, make sure your devices meet the following requirements:

- Windows operating system.
- Microsoft Defender Antivirus platform version `4.18.2106.6` or later.

Important

Use one management authority for these settings. Mobile device management \(MDM\) and Group Policy settings can conflict, and [ControlPolicyConflict \(MDMWinsOverGP\)](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-controlpolicyconflict) doesn't apply to the Defender configuration service provider \(CSP\). If you use MDM, remove conflicting Defender Group Policy settings.

## Review Group Policy settings

The following table lists the Group Policy settings for update channels:

| Setting title | Description | Location |
| --- | --- | --- |
| Select the channel for Microsoft Defender monthly platform updates | Select when devices receive monthly platform updates. Available channels are Beta, Preview, Staged, Broad, Critical: Time Delay, and Not configured. | Windows Components\\Microsoft Defender Antivirus |
| Select the channel for Microsoft Defender monthly engine updates | Select when devices receive monthly engine updates. Available channels are Beta, Preview, Staged, Broad, Critical: Time Delay, and Not configured. | Windows Components\\Microsoft Defender Antivirus |
| Select the channel for Microsoft Defender daily security intelligence updates | Select Staged, Broad, or Not configured for security intelligence rollout cycles, which occur multiple times each day. | Windows Components\\Microsoft Defender Antivirus |
| Disable gradual rollout of Microsoft Defender updates | Disable gradual rollout for monthly and security intelligence updates. This setting overrides configured platform and engine update channels. | Windows Components\\Microsoft Defender Antivirus\\MpEngine |

For monthly platform and engine updates, use the following channels:

- **Beta Channel**: Receive prerelease updates first. Use this channel only for a limited number of devices in manual test environments. Devices in the Windows Insider Program are subscribed to this channel by default.
- **Current Channel \(Preview\)**: Receive updates earliest during gradual release. Use this channel for preproduction or validation environments.
- **Current Channel \(Staged\)**: Receive updates later during gradual release. Use this channel for a small, representative group of production devices.
- **Current Channel \(Broad\)**: Receive updates after gradual release completes. Use this channel for a broad group of production devices.
- **Critical: Time Delay**: Receive updates with a 48-hour delay. Use this channel only for critical environments.
- **Not configured**: Allow Microsoft to assign devices to channels during gradual release. This setting is suitable for most devices.

For security intelligence updates, select Staged, Broad, or Not configured. The Defender CSP currently documents Staged as equivalent to Broad. Don't rely on a timing difference between Staged and Broad without validating the behavior in your environment. For more rollout guidance, see [Manage the gradual rollout process for Microsoft Defender updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-gradual-rollout).

## Configure a gradual rollout by using Group Policy

Note

Use the latest Windows administrative templates available for your environment. If the templates don't contain these settings, a temporary, English-only template is available from the [Microsoft Defender update controls repository](https://github.com/microsoft/defender-updatecontrols) on GitHub.

You can use [Group Policy](https://learn.microsoft.com/en-us/windows/win32/srvnodes/group-policy?redirectedfrom=MSDN) to configure and manage Microsoft Defender Antivirus on your endpoints. To configure an update channel:

1. On your Group Policy management machine, open the **Group Policy Management Console**, right-click the **Group Policy Object** \(GPO\) you want to configure, and select **Edit**.
2. In the Group Policy Management Editor, go to **Computer configuration**.
3. Select **Administrative templates**.
4. Expand the tree to **Windows components** > **Microsoft Defender Antivirus**.
5. Expand the section in the **Location** column of the [Group Policy settings table](#group-policy-settings), double-click the setting, and configure the update channel.
6. Deploy the updated GPO as you normally do. For guidance, see [Group Policy](https://learn.microsoft.com/en-us/windows/win32/srvnodes/group-policy).

## Configure a gradual rollout by using Microsoft Intune

Create a Windows [Settings Catalog policy in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/). In the **Defender** category, configure one or more of the following settings:

- **Platform Updates Channel**
- **Engine Updates Channel**
- **Security Intelligence Updates Channel**
- **Disable Gradual Release**

If you need to use a custom Open Mobile Alliance Uniform Resource Identifier \(OMA-URI\) policy, follow the instructions in [Add custom settings for Windows 10 devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/configuration/custom-settings-windows-10) and use the following values:

| Setting | OMA-URI | Allowed values |
| --- | --- | --- |
| Platform updates channel | `./Device/Vendor/MSFT/Defender/Configuration/PlatformUpdatesChannel` | `0` Not configured, `2` Beta, `3` Preview, `4` Staged, `5` Broad, `6` Critical: Time Delay |
| Engine updates channel | `./Device/Vendor/MSFT/Defender/Configuration/EngineUpdatesChannel` | `0` Not configured, `2` Beta, `3` Preview, `4` Staged, `5` Broad, `6` Critical: Time Delay |
| Security intelligence updates channel | `./Device/Vendor/MSFT/Defender/Configuration/SecurityIntelligenceUpdatesChannel` | `0` Not configured, `4` Staged, `5` Broad |
| Disable gradual release | `./Device/Vendor/MSFT/Defender/Configuration/DisableGradualRelease` | `0` False, `1` True |

For more information about the OMA-URI settings and values, see [Defender CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/defender-csp).

## Configure a gradual rollout by using PowerShell

Use the **Set-MpPreference** cmdlet to configure Defender Antivirus update and protection preferences.

Use the following parameters:

- *PlatformUpdatesChannel* \(`Beta`, `Preview`, `Staged`, `Broad`, `Delayed`, or `NotConfigured`\)
- *EngineUpdatesChannel* \(`Beta`, `Preview`, `Staged`, `Broad`, `Delayed`, or `NotConfigured`\)
- *DefinitionUpdatesChannel* \(`Staged`, `Broad`, or `NotConfigured`\)
- *DisableGradualRelease* \(`$true` or `$false`\)

For example, run the following command in an elevated PowerShell session \(a PowerShell window you opened by selecting **Run as administrator**\) to configure platform updates to arrive from the Beta Channel:

```powershell
Set-MpPreference -PlatformUpdatesChannel Beta
```

For more information about these parameters, see [Set-MpPreference](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference).

## Verify gradual rollout configuration in the registry

To verify the effective PowerShell configuration, run `Get-MpPreference | Select-Object PlatformUpdatesChannel, EngineUpdatesChannel, DefinitionUpdatesChannel, DisableGradualRelease`.

Policy-backed update channel settings can appear under `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`:

- `EngineRing`
- `PlatformRing`
- `SignaturesRing`

The `DisableGradualRelease` value appears under `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\MpEngine`.

Note

You can also use a management tool such as Microsoft Configuration Manager to run PowerShell scripts. See [Create and run PowerShell scripts from the Configuration Manager console](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/create-deploy-scripts).

Tip

For antivirus information for other platforms, see:

> - [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
> - [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
> - [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
> - [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
> - [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
> - [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
> - [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
