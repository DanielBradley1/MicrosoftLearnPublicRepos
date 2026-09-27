<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/protect/understand/protect-data-and-site-infrastructure -->
<!-- Sitemap-Last-Modified: 2023-02-22 -->

# Protect data and site infrastructure

*Applies to: Configuration Manager \(current branch\)*

You want your users to securely access your organization's resources. Protect both your infrastructure and your data from exposure or malicious attack. Use Configuration Manager to enable access and help protect your organization's resources.

- [Endpoint Protection](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection) lets you manage the following Microsoft Defender policies for client computers:

  - Microsoft Defender Antimalware
  - Microsoft Defender Firewall
  - Microsoft Defender for Endpoint
  - Microsoft Defender Exploit Guard
  - Microsoft Defender Application Guard
  - Microsoft Defender Application Control


  Tip


  To manage endpoint protection on co-managed Windows 10 or later devices using the Microsoft Intune cloud service, switch the [**Endpoint Protection** workload](https://learn.microsoft.com/en-us/intune/configmgr/comanage/workloads#endpoint-protection) to Intune. For more information, see [Endpoint protection for Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-endpoint-protection-settings-windows).

- Protect data stored on on-premises Windows clients with BitLocker Drive Encryption \(BDE\). Configuration Manager provides full BitLocker lifecycle management that can replace the use of Microsoft BitLocker Administration and Monitoring \(MBAM\). For more information, see [Plan for BitLocker management](https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/bitlocker-management).

Use other components of Microsoft Intune to protect your devices. For more information, see [Protect devices with Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-security/overview).
