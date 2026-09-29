<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/tamper-resiliency -->
<!-- Sitemap-Last-Modified: 2026-09-08 -->

# Protect your organization from the effects of tampering

Tampering describes attempts by attackers to weaken Microsoft Defender for Endpoint. Attackers might target security controls on individual devices as part of a larger objective, such as deploying ransomware. Tamper resiliency combines device-level protections, centralized management, and detection to help prevent these changes and reduce their impact.

For tamper protection modes, protected settings, requirements, exclusions, and investigation guidance, see [Tamper protection overview](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview).

Build organization-wide tamper resiliency on a [Zero Trust](https://learn.microsoft.com/en-us/windows/security/book/security-foundation) model:

- Follow the best practice of least privilege. See [Access control overview for Windows](https://learn.microsoft.com/en-us/windows/security/identity-protection/access-control/access-control).
- Configure [Conditional Access policies](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/overview) to apply access controls based on user and device signals.

Keep devices healthy and centrally managed:

- [Onboard devices to Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-configure).
- Make sure [security intelligence and antivirus updates](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates) are installed.
- Manage devices centrally by using [Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/advanced-threat-protection-configure), [Microsoft Defender for Endpoint security settings management](https://learn.microsoft.com/en-us/intune/intune-service/protect/mde-security-integration), or [Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection-configure).

Note

On Windows devices, you can manage Microsoft Defender Antivirus by using Group Policy, Windows Management Instrumentation \(WMI\), and PowerShell cmdlets. These methods are more susceptible to tampering than centralized management through Intune, Configuration Manager, or Defender for Endpoint security settings management.

If you're using Group Policy, we recommend [disabling local overrides for Microsoft Defender Antivirus settings](https://learn.microsoft.com/en-us/defender-endpoint/configure-local-policy-overrides-microsoft-defender-antivirus#configure-local-overrides-for-microsoft-defender-antivirus-settings-using-group-policy) and [disabling local list merging](https://learn.microsoft.com/en-us/defender-endpoint/configure-local-policy-overrides-microsoft-defender-antivirus#configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged).

Use the [device health reports in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/device-health-reports) to review the health of [Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/device-health-microsoft-defender-antivirus-health) and [Defender for Endpoint sensors](https://learn.microsoft.com/en-us/defender-endpoint/device-health-sensor-health-os).

## Prevent tampering on individual devices

Different controls protect against different tampering techniques:

| Control | Platform | Tampering techniques |
| --- | --- | --- |
| [Tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview) | Windows | Terminate or suspend processes, stop services, modify registry settings or exclusions, hijack DLLs, modify the file system, or impair agent integrity. |
| [Tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-macos-configure) | macOS | Terminate or suspend processes, modify Defender for Endpoint files, or impair agent integrity. |
| [Attack surface reduction \(ASR\) rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview) | Windows | Prevent apps from writing exploited vulnerable signed drivers to disk. See [Block abuse of exploited vulnerable signed drivers \(Device\)](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-abuse-of-exploited-vulnerable-signed-drivers-device). |
| [App Control for Business](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/app-control-for-business/operations/appcontrol-operational-guide), formerly Windows Defender Application Control \(WDAC\) | Windows | Prevent vulnerable kernel drivers from loading. See [Microsoft vulnerable driver block list](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/app-control-for-business/design/microsoft-recommended-driver-block-rules). |

## Protect against driver-based tampering on Windows

Attackers can exploit vulnerabilities in signed drivers to gain kernel access and disable or bypass security controls. Use the Microsoft vulnerable driver blocklist, an ASR rule, and App Control for Business policies to reduce this risk.

### Use the Microsoft vulnerable driver blocklist

Since the Windows 11 2022 Update, the vulnerable driver blocklist is enabled by default. Except on Windows Server 2016, the blocklist is also enforced when memory integrity, also known as hypervisor-protected code integrity \(HVCI\), Smart App Control, or S mode is active. The blocklist is updated quarterly, and updates are delivered through monthly Windows updates.

See [Microsoft vulnerable driver block list](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/app-control-for-business/design/microsoft-recommended-driver-block-rules#microsoft-vulnerable-driver-blocklist).

To deploy the latest recommended blocklist through an App Control for Business policy, see [Vulnerable driver blocklist XML](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/app-control-for-business/design/microsoft-recommended-driver-block-rules#microsoft-vulnerable-driver-blocklist).

### Use the vulnerable signed drivers ASR rule

The **Block abuse of exploited vulnerable signed drivers** ASR rule prevents apps from saving vulnerable signed drivers on a device. It doesn't prevent an existing driver from loading. Run the rule in **Audit** mode to evaluate its effect before you use **Block** mode. For more information, see [Block abuse of exploited vulnerable signed drivers \(Device\)](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-abuse-of-exploited-vulnerable-signed-drivers).

### Use App Control for Business to block drivers

[App Control for Business operational guidance](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/app-control-for-business/operations/appcontrol-operational-guide) explains how to create policies that control which drivers can run. Use audit mode to evaluate compatibility before you enforce an App Control policy.

## Protect Microsoft Defender Antivirus exclusions on Windows

Attackers might add or modify Microsoft Defender Antivirus exclusions to avoid scanning. Tamper protection can protect organization-managed exclusion lists when devices meet the platform, management, sensor, and policy requirements. For the complete requirements and verification steps, see [Protect Microsoft Defender Antivirus exclusions with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-antivirus-exclusions).

The `DisableLocalAdminMerge` setting is one of the exclusion-protection requirements. For configuration information, see [Disable local list merging](https://learn.microsoft.com/en-us/defender-endpoint/configure-local-policy-overrides-microsoft-defender-antivirus#use-microsoft-intune-to-disable-local-list-merging).

As a separate protection, enable [HideExclusionsFromLocalAdmin](https://learn.microsoft.com/en-us/windows/client-management/mdm/defender-csp#configurationhideexclusionsfromlocaladmins) to prevent local administrators from viewing existing exclusions through Registry Editor or the **Get-MpPreference** PowerShell cmdlet. This setting doesn't remove the exclusions.

## Detecting potential tampering activity in the Microsoft Defender portal

Some potential tampering activity generates an alert in the Microsoft Defender portal. To reduce unnecessary alert noise, activity that isn't correlated with suspicious behavior might not generate a standalone alert. The activity remains available in the device timeline and advanced hunting. For investigation guidance, see [View information about tampering attempts](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview#view-information-about-tampering-attempts).

Tampering alert titles can include:

- Attempt to bypass Microsoft Defender for Endpoint client protection
- Attempt to stop Microsoft Defender for Endpoint sensor
- Attempt to tamper with Microsoft Defender on multiple devices
- Attempt to turn off Microsoft Defender Antivirus protection
- Defender detection bypass
- Driver-based tampering attempt blocked
- Image file execution options set for tampering purposes
- Microsoft Defender Antivirus protection turned off
- Microsoft Defender Antivirus tampering
- Modification attempt in Microsoft Defender Antivirus exclusion list
- Pending file operations mechanism abused for tampering purposes
- Possible anti-malware Scan Interface \(AMSI\) tampering
- Possible remote tampering
- Possible sensor tampering in memory
- Potential attempt to tamper with MDE via drivers
- Security software tampering
- Suspicious Microsoft Defender Antivirus exclusion
- Tamper protection bypass
- Tampering activity typical to ransomware attacks
- Tampering with Microsoft Defender for Endpoint sensor communication
- Tampering with Microsoft Defender for Endpoint sensor settings
- Tampering with the Microsoft Defender for Endpoint sensor

If the [Block abuse of exploited vulnerable signed drivers \(Device\)](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-abuse-of-exploited-vulnerable-signed-drivers) ASR rule is triggered, view the event in the [attack surface reduction rules report](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-report) or [advanced hunting](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-monitor#asr-rule-events-in-advanced-hunting).

If [App Control for Business](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/app-control-for-business/deployment/appcontrol-deployment-guide) is enabled, you can view [block and audit activity in advanced hunting](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/app-control-for-business/operations/querying-application-control-events-centrally-using-advanced-hunting).
