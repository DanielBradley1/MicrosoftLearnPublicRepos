<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-faq -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# Frequently asked questions \(FAQs\) about tamper protection

Get answers about tamper protection requirements, supported platforms, configuration methods, policy precedence, exclusions, and alerts.

**Applies to:**

- [Microsoft Defender for Endpoint Plan 1](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [Microsoft Defender for Endpoint Plan 2](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows)
- [Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview)
- [Microsoft 365 Business Premium](https://learn.microsoft.com/en-us/Microsoft-365/business-premium/m365bp-overview)

**Platforms**

- Windows
- macOS

## What requirements must devices meet to receive the tamper protection setting from the Microsoft Defender portal?

See [Requirements for tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview#requirements-for-tamper-protection) for supported operating systems, permissions, product versions, onboarding, and cloud-delivered protection requirements.

## On which versions of Windows can I configure tamper protection?

Tamper protection supports Windows 10 and later, including Enterprise multi-session; Windows Server 2016 and later; Windows Server version 1803 and later; Windows Server 2012 R2 using the modern unified solution; and Azure Stack HCI OS version 23H2 and later. See [Supported operating systems](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview#supported-operating-systems).

## How do I configure tamper protection on macOS devices?

See [Configure tamper protection for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-macos-configure) for configuration methods, mode behavior, status verification, exclusions, and troubleshooting guidance.

## Does tamper protection affect non-Microsoft antivirus registration in the Windows Security app?

No. Non-Microsoft antivirus apps continue to register with the Windows Security app.

## Does tamper protection work when Microsoft Defender Antivirus is in passive mode?

Tamper protection continues to protect the Microsoft Defender Antivirus service and its features when Defender Antivirus runs in passive mode. The mode used by Defender Antivirus depends on the operating system, onboarding state, and installed antivirus products. For more information, see [Microsoft Defender Antivirus compatibility with other security products](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility).

## How do I turn tamper protection on or off on Windows devices?

See [Configure tamper protection on Windows devices](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-windows-configure) for instructions that use Intune, the Microsoft Defender portal, Configuration Manager with tenant attach, or the Windows Security app.

## Does tamper protection apply to Microsoft Defender Antivirus exclusions?

Yes, when the required conditions are met. See [Protect Microsoft Defender Antivirus exclusions with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-antivirus-exclusions).

## How does configuring tamper protection in Intune affect how I manage Microsoft Defender Antivirus with Group Policy?

When tamper protection is on, Group Policy changes to tamper-protected settings might appear to succeed, but tamper protection blocks the changes. To make a temporary change on a device, use [troubleshooting mode](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable). To make permanent changes, adjust the tamper protection policy or exclude the affected devices from tamper protection through Intune or Configuration Manager. For more help, see [Troubleshoot problems with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-troubleshoot).

## If my organization uses Microsoft Intune to configure tamper protection, does the policy apply only to the entire organization?

No. You can assign the Intune policy to your entire organization or to selected user or device groups. You can also exclude groups from the policy assignment. See [Configure tamper protection in Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-windows-configure#configure-tamper-protection-in-microsoft-intune).

## What settings can't be changed when tamper protection is turned on?

See [Tamper protection overview](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview#what-happens-when-tamper-protection-is-turned-on) for the current list of protected settings.

## If tamper protection is turned on in the Microsoft Defender portal, can a policy in Intune or Configuration Manager override it?

Yes. A policy that manages tamper protection takes precedence over the organization-wide setting in the Defender portal. See [Configure tamper protection on Windows devices](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-windows-configure).

## How do I deploy DisableLocalAdminMerge?

Use Intune to configure [DisableLocalAdminMerge](https://learn.microsoft.com/en-us/windows/client-management/mdm/defender-csp#configurationdisablelocaladminmerge). This setting is required when you [protect Microsoft Defender Antivirus exclusions with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-antivirus-exclusions).

## How can I confirm whether exclusions are tamper protected on a Windows device?

Follow the guidance in [Protect Microsoft Defender Antivirus exclusions with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-antivirus-exclusions).

## When antivirus exclusions are tamper protected, do I need to disable tamper protection to apply new exclusion policy settings from Intune or Configuration Manager?

No. You don't need to disable tamper protection to apply new exclusion policy settings from Intune or Configuration Manager. See [Protect Microsoft Defender Antivirus exclusions with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-antivirus-exclusions).

## Can I configure tamper protection with Configuration Manager?

Yes. Configuration Manager uses tenant attach to deploy tamper protection from the Intune admin center. See [Configure tamper protection using Microsoft Configuration Manager](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-windows-configure#configure-tamper-protection-using-microsoft-configuration-manager).

## Can local administrators change tamper protection on organization-managed devices?

On organization-managed devices, a policy or Defender portal setting takes precedence over changes made by a local administrator in the Windows Security app. See [Configure tamper protection on Windows devices](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-windows-configure).

## Are tampering attempts shown as alerts in the Microsoft Defender portal?

Some tampering activity generates alerts. To reduce unnecessary alert noise, activity that isn't correlated with suspicious behavior might not generate an alert. The activity is still available in the device timeline and advanced hunting. See [View information about tampering attempts](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview#view-information-about-tampering-attempts).
