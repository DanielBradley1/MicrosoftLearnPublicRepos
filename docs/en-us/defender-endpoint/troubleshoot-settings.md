<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-settings -->
<!-- Sitemap-Last-Modified: 2026-07-18 -->

# Troubleshoot Microsoft Defender Antivirus settings

Microsoft Defender Antivirus provides numerous ways to manage the product, which provides small and medium-sized businesses and enterprise organizations with flexibility by working with the management tools that they already have.

- Microsoft Defender for Endpoint security settings management
- Microsoft Intune \(MDM\)
- Microsoft Configuration Manager with Tenant Attaches
- Microsoft Configuration Manager co-management
- Microsoft Configuration Manager \(standalone\)
- Group Policy \(GPO\)
- PowerShell
- Windows Management Instrumentation \(WMI\)
- Registry

Tip

For best results, use one method of managing Microsoft Defender Antivirus.

## Troubleshooting Microsoft Defender Antivirus settings

Suppose that migrating from a non-Microsoft antivirus product, and when you try enabling Microsoft Defender Antivirus, it won't start. Most likely, you're experiencing a policy conflict.

To remove policy conflicts, here's our current, recommended process:

1. Understand the order of precedence.
2. Determine where Microsoft Defender Antivirus settings are configured.
3. Identify policies and settings.
4. Work with your security team to remove or revise conflicting policies.

Tip

In versions of the Microsoft Defender antimalware platform before 4.18.2108.4 \(September 2021\), the dword registry key `DisableAntispyware` with the value 1 at `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Defender` could also prevent Microsoft Defender Antivirus from starting.

## Step 1: Understand the order of precedence

Note

Microsoft Defender for Endpoint attach configurations can be overridden by other configuration tools that write to the same registry location.

Starting in February 2026, Microsoft Defender Antivirus on Windows is changing how antivirus settings \(like exclusions\) are stored when Microsoft Defender for Endpoint configuration management is enabled in an organization. Starting with the 4.18.25110.6 release, organizations using Microsoft Defender for Endpoint configuration management can no longer read exclusion values directly from the local device registry. Instead, setting configuration must be retrieved using supported Microsoft Defender PowerShell cmdlets. Organizations using Defender for Endpoint configuration management must use supported Defender PowerShell cmdlets \(such as Get-MpPreference\).

When policies and settings are configured in multiple tools, in general, here's the order of precedence:

1. Microsoft Defender for Endpoint security settings management
2. Group Policy \(GPO\)
3. Microsoft Configuration Manager co-management
4. Microsoft Configuration Manager \(standalone\)
5. Microsoft Intune \(MDM\)
6. Microsoft Configuration Manager with Tenant Attaches
7. PowerShell \([Set-MpPreference](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference)\), [MpCmdRun command-line tool](https://learn.microsoft.com/en-us/defender-endpoint/command-line-arguments-microsoft-defender-antivirus), or [Windows Management Instrumentation](https://learn.microsoft.com/en-us/defender-endpoint/use-wmi-microsoft-defender-antivirus) \(WMI\).

Warning

[MDMWinsOverGP](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-controlpolicyconflict) is a Policy CSP setting that doesn't apply for all settings, such as [attack surface reduction \(ASR\) rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview) in Windows 10.

## Step 2: Determine where Microsoft Defender Antivirus settings are configured

Find out whether Microsoft Defender Antivirus settings are coming through a policy, MDM, or a local setting. The following table describes policies, settings, and relevant tools.

| Policy or setting | Registry location | Tools |
| --- | --- | --- |
| Policy | `HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows Defender` | - Microsoft Defender for Endpoint security settings management<br>- Microsoft Configuration Manager co-management<br>- Microsoft Configuration Manager<br>- GPO |
| MDM | `HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows Defender\\Policy Manager` | - Microsoft Intune \(MDM\)<br>- Microsoft Configuration Manager with Tenant Attaches |
| Local setting | `HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows Defender` | - PowerShell \(Set-MpPreference\)<br>- MpCmdRun command-line tool<br>- Windows Management Instrumentation \(WMI\) |

Tip

To see the actual value of each security setting on a device and the source that configured it, use the **Effective settings** tab on the device page. For more information, see [Configuration management - Effective settings](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines#configuration-management---effective-settings).

## Step 3: Identify policies or settings

The following table describes how to identify policies and settings.

| Method used | What to check |
| --- | --- |
| Policy | - **If you're using GPO**: Run the following command in an elevated Command Prompt \(a Command Prompt window you opened by selecting **Run as administrator**\): `GpResult.exe /h C:\\temp\\GpResult_output.html`.<br>- If you're using Microsoft Configuration Manager co-management or Microsoft Configuration Manager \(standalone\), go to `C:\\Windows\\CCM\\Logs`. |
| MDM | If you're using Intune, on your device, select **Start**, open Command Prompt as an administrator, and then run the command `mdmdiagnosticstool.exe -out "c:\\temp\\MDMDiagReport.zip"`. For more information, see [Collect MDM logs - Windows Client Management](https://learn.microsoft.com/en-us/windows/client-management/mdm-collect-logs). |
| Local setting | Determine whether the policy or setting was deployed during the imaging \(sysprep\), via PowerShell \(for example, Set-MpPreference\), Windows Management Instrumentation \(WMI\), or through a direct modification to the registry. |

## Step 4: Remove or revise conflicting policies

Once you have identified the conflicting policy, work with your security administrators to change device targeting so that devices receive the correct Microsoft Defender Antivirus settings.
