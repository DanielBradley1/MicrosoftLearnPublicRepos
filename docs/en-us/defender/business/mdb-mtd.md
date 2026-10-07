<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-mtd -->
<!-- Sitemap-Last-Modified: 2026-01-20 -->

# Mobile threat defense capabilities in Microsoft Defender for Business

Microsoft Defender for Business provides advanced threat protection capabilities for devices, such as Windows and Mac clients. Defender for Business also includes mobile threat defense. Mobile threat defense capabilities help protect Android and iOS devices, without requiring you to use Microsoft Intune to onboard mobile devices.

In addition, mobile threat defense capabilities integrate with [Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-overview), where Cloud Solution Providers \(CSPs\) can view information about vulnerable devices and help mitigate detected threats.

## What does mobile threat defense include?

The following table summarizes the capabilities that are included in mobile threat defense in Defender for Business:

| Capability | Android | iOS |
| --- | --- | --- |
| **Web Protection**  <br>Anti-phishing, blocking unsafe network connections, and support for custom indicators.  <br>Web protection is turned on by default with [web content filtering](https://learn.microsoft.com/en-us/defender-business/mdb-web-content-filtering). | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-present-icon.png) | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-present-icon.png) |
| **Malware protection**  <br>Scanning for malicious apps, including system apps. | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-present-icon.png) | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-absent-icon.png) |
| **Jailbreak detection**  <br>Detection of jailbroken devices. | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-absent-icon.png) | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-present-icon.png) |
| **Microsoft Defender Vulnerability Management**  <br>Vulnerability assessment of onboarded mobile devices. Includes vulnerability assessments for operating systems and apps for Android and iOS.  <br>For more information, see [Use your vulnerability management dashboard in Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-view-tvm-dashboard). | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-present-icon.png) | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-present-icon.png) ¹ |
| **Network Protection**  <br>Protection against rogue Wi-Fi related threats and rogue certificates.  <br>Network protection is turned on by default with [next-generation protection](https://learn.microsoft.com/en-us/defender-business/mdb-next-generation-protection).  <br>As part of mobile threat defense, network protection also includes the ability to allow root certification authority and private root certification authority certificates in Intune. It also establishes trust with endpoints. | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-present-icon.png) ² | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-present-icon.png) ² |
| **Unified alerting**  <br>Alerts from all platforms are listed in the unified [Microsoft Defender portal](https://security.microsoft.com). In the navigation pane, choose **Incidents**.  <br>For more information, see [View and manage incidents in Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-view-manage-incidents) | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-present-icon.png) | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-present-icon.png) |
| **Conditional Access** and **conditional launch**  <br>[Conditional Access](https://learn.microsoft.com/en-us/intune/intune-service/protect/conditional-access) and [conditional launch](https://learn.microsoft.com/en-us/intune/intune-service/apps/app-protection-policies-access-actions) block risky devices from accessing corporate resources.<br><br>- Conditional Access policies require certain criteria to be met before a user can access company data on their mobile device.<br>- Conditional launch policies enable your security team to block access or wipe devices that don't meet certain criteria.<br>- Defender for Business risk signals can also be added to app protection policies. | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-absent-icon.png) ³ | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-absent-icon.png) ³ |
| **Privacy controls**  <br>Configure privacy in threat reports by controlling the data sent by Defender for Business. Privacy controls are available for admin and end users, and for both enrolled and unenrolled devices. | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-absent-icon.png) ³ | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-absent-icon.png) ³ |
| **Integration with Microsoft Tunnel**  <br>Integration with [Microsoft Tunnel](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-tunnel-overview), a VPN gateway solution for Microsoft Intune. | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-absent-icon.png) ⁴ | ![](https://learn.microsoft.com/en-us/defender-business/media/feature-absent-icon.png) ⁴ |

¹ Operating system vulnerabilities are included. Software and app vulnerabilities require Microsoft Intune. ² You can manage an allowlist of root certification authority certificates and private root certification authority certificates in Microsoft Intune. ³ Requires Microsoft Intune. ⁴ Requires Microsoft Intune. For more information, see [Prerequisites for the Microsoft Tunnel in Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-tunnel-prerequisites).

## How to get mobile threat defense capabilities

Mobile threat defense capabilities are now generally available to [Defender for Business](https://learn.microsoft.com/en-us/defender-business/get-defender-business) customers. Here's how to get these capabilities for your organization:

1. Make sure that Defender for Business finished provisioning. In the [Microsoft Defender portal](https://security.microsoft.com), go to **Assets** > **Devices**.

   - The message, *Hang on! We're preparing new spaces for your data and connecting them* means Defender for Business isn't finished provisioning. The process can take up to 24 hours to complete.
   - If you see a list of devices, or you're prompted to onboard devices, it means Defender for Business provisioning is complete.

2. Review and, if necessary, edit your [next-generation protection policies](https://learn.microsoft.com/en-us/defender-business/mdb-next-generation-protection).
3. Review and, if necessary, edit your [firewall policies and custom rules](https://learn.microsoft.com/en-us/defender-business/mdb-firewall).
4. Review and, if necessary, edit your [web content filtering](https://learn.microsoft.com/en-us/defender-business/mdb-web-content-filtering) policy.
5. To onboard mobile devices, see the "Use the Microsoft Defender app" procedures in [Onboard devices to Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-onboard-devices).

## Related content

- [Set up and configure Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-setup-configuration)
- [View and edit security policies and settings in Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-configure-security-settings)
- [What's new in Microsoft 365 Business Premium and Microsoft Defender for Business](https://learn.microsoft.com/en-us/microsoft-365/business-premium/m365bp-mdb-whats-new)
