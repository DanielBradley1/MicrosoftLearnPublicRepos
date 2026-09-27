<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-security -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Configure Microsoft Intune for increased security \(Preview\)

The security recommendations in this document are designed to help you improve your organization's security posture by using Microsoft Intune. These recommendations are influenced by accepted industry standards like those developed by NIST, the configuration baselines we use internally at Microsoft, and our experiences with customers. The recommendations in this article for Intune are focused on devices, but guided by the following Microsoft [Secure Future Initiative](https://www.microsoft.com/trust-center/security/secure-future-initiative?msockid=2bad2df65a416adb0e5838355b3e6b95#SFI-pillars) pillars:

- Protect identities and secrets
- Protect tenants and isolate production systems
- Protect networks
- Protect engineering systems
- Monitor and detect cyberthreats
- Accelerate response and remediation

Tip

Some organizations might take these recommendations exactly as written, while others might choose to make modifications based on their own business needs.

We recommend that all of the following controls be implemented where licenses are available. These patterns and practices help to provide a secure foundation for other resources built on top of this solution. More controls will be added to this document over time.

## Automated assessment

Manually checking this guidance against a tenant's configuration can be time-consuming and error-prone. The Zero Trust Assessment transforms this process with automation to test for these security configuration items and more. Learn more in [What is the Zero Trust Assessment](https://learn.microsoft.com/en-us/security/zero-trust/assessment/overview)?

## Secure Tenant

Ensure tenant-level governance, identity, and configuration consistency.

| Check | Minimum License Requirements |
| --- | --- |
| [Scope tag configuration is enforced to support delegated administration and least-privilege access](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#scope-tag-configuration-is-enforced-to-support-delegated-administration-and-least-privilege-access) | Microsoft Intune Plan 1 |
| [Device enrollment notifications are enforced to ensure user awareness and secure onboarding](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#device-enrollment-notifications-are-enforced-to-ensure-user-awareness-and-secure-onboarding) | Microsoft Intune Plan 1 |
| [Windows automatic device enrollment is enforced to eliminate risks from unmanaged endpoints](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#windows-automatic-device-enrollment-is-enforced-to-eliminate-risks-from-unmanaged-endpoints) | Microsoft Intune Plan 1  <br>Microsoft Entra ID P1 *\(for Conditional Access\)* |
| [Compliance policies protect Windows devices](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#compliance-policies-protect-windows-devices) | Microsoft Intune Plan 1 |
| [Compliance policies protect macOS devices](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#compliance-policies-protect-macos-devices) | Microsoft Intune Plan 1 |
| [Compliance policies protect fully managed and corporate-owned Android devices](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#compliance-policies-protect-fully-managed-and-corporate-owned-android-devices) | Microsoft Intune Plan 1 |
| [Compliance policies protect personally owned Android devices](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#compliance-policies-protect-personally-owned-android-devices) | Microsoft Intune Plan 1 |
| [Compliance policies protect iOS/iPadOS devices](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#compliance-policies-protect-iosipados-devices) | Microsoft Intune Plan 1 |
| [Platform SSO is configured to strengthen authentication on macOS devices](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#platform-sso-is-configured-to-strengthen-authentication-on-macos-devices) | Microsoft Intune Plan 1  <br>Microsoft Entra ID P1 *\(for Conditional Access\)* |
| [Defender for Endpoint automatic enrollment is enforced to reduce risk from unmanaged Android threats](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#defender-for-endpoint-automatic-enrollment-is-enforced-to-reduce-risk-from-unmanaged-android-threats) | Microsoft Intune Plan 1  <br>Defender for Endpoint Plan 1 |
| [Device cleanup rules maintain tenant hygiene by hiding inactive devices](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#device-cleanup-rules-maintain-tenant-hygiene-by-hiding-inactive-devices) | Microsoft Intune Plan 1 |
| [Terms and Conditions policies protect access to sensitive data](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#terms-and-conditions-policies-protect-access-to-sensitive-data) | Microsoft Intune Plan 1 |
| [Company Portal branding and support settings enhance user experience and trust](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#company-portal-branding-and-support-settings-enhance-user-experience-and-trust) | Microsoft Intune Plan 1 |
| [Endpoint Analytics is enabled to help identify risks on Windows devices](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant#endpoint-analytics-is-enabled-to-help-identify-risks-on-windows-devices) | Microsoft Intune Plan 1 |

For license details, see:

- [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/fundamentals/licensing)
- [Microsoft Entra licensing](https://learn.microsoft.com/en-us/entra/fundamentals/licensing)
- [Overview of Microsoft Defender for Endpoint Plan 1](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1)

## Secure Devices

Secure endpoints through device configuration and security policies.

| Check | Minimum License Requirements |
| --- | --- |
| [Local administrator credentials on Windows are protected by Windows LAPS](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#local-administrator-credentials-on-windows-are-protected-by-windows-laps) | Microsoft Intune Plan |
| [Local administrator credentials on macOS are protected during enrollment by macOS LAPS](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#local-administrator-credentials-on-macos-are-protected-during-enrollment-by-macos-laps) | Microsoft Intune Plan 1 |
| [Local account usage on Windows is restricted to reduce unauthorized access](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#local-account-usage-on-windows-is-restricted-to-reduce-unauthorized-access) | Microsoft Intune Plan 1 |
| [Data on Windows is protected by BitLocker encryption](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#data-on-windows-is-protected-by-bitlocker-encryption) | Microsoft Intune Plan 1 |
| [FileVault encryption protects data on macOS devices](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#filevault-encryption-protects-data-on-macos-devices) | Microsoft Intune Plan 1 |
| [Authentication on Windows uses Windows Hello for Business](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#authentication-on-windows-uses-windows-hello-for-business) | Microsoft Intune Plan 1 |
| [Attack Surface Reduction rules are applied to Windows devices to prevent exploitation of vulnerable system components](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#attack-surface-reduction-rules-are-applied-to-windows-devices-to-prevent-exploitation-of-vulnerable-system-components) | Microsoft Intune Plan 1  <br>Defender for Endpoint Plan 1 |
| [Defender Antivirus policies protect Windows devices from malware](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#defender-antivirus-policies-protect-windows-devices-from-malware) | Microsoft Intune Plan 1  <br>Defender for Endpoint Plan 1 |
| [Defender Antivirus policies protect macOS devices from malware](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#defender-antivirus-policies-protect-macos-devices-from-malware) | Microsoft Intune Plan 1  <br>Defender for Endpoint Plan 1 |
| [Windows Firewall policies protect against unauthorized network access](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#windows-firewall-policies-protect-against-unauthorized-network-access) | Microsoft Intune Plan 1 |
| [macOS Firewall policies protect against unauthorized network access](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#macos-firewall-policies-protect-against-unauthorized-network-access) | Microsoft Intune Plan 1 |
| [Windows Update policies are enforced to reduce risk from unpatched vulnerabilities](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#windows-update-policies-are-enforced-to-reduce-risk-from-unpatched-vulnerabilities) | Microsoft Intune Plan 1 |
| [Security baselines are applied to Windows devices to strengthen security posture](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#security-baselines-are-applied-to-windows-devices-to-strengthen-security-posture) | Microsoft Intune Plan 1 |
| [Update policies for macOS are enforced to reduce risk from unpatched vulnerabilities](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#update-policies-for-macos-are-enforced-to-reduce-risk-from-unpatched-vulnerabilities) | Microsoft Intune Plan 1 |
| [Update policies for iOS/iPadOS are enforced to reduce risk from unpatched vulnerabilities](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices#update-policies-for-iosipados-are-enforced-to-reduce-risk-from-unpatched-vulnerabilities) | Microsoft Intune Plan 1 |

For license details, see:

- [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/fundamentals/licensing)
- [Overview of Microsoft Defender for Endpoint Plan 1](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1)

## Secure Data

Protect data on devices and in transit, and enforce secure access to organizational data.

| Check | Minimum License Requirements |
| --- | --- |
| [Data on Android is protected by app protection policies](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-data#data-on-android-is-protected-by-app-protection-policies) | Microsoft Intune Plan 1 |
| [Data on iOS/iPadOS is protected by app protection policies](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-data#data-on-iosipados-is-protected-by-app-protection-policies) | Microsoft Intune Plan 1 |
| [Conditional Access policies block access from unmanaged apps](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-data#conditional-access-policies-block-access-from-unmanaged-apps) | Microsoft Intune Plan 1  <br>Microsoft Entra ID P1 *\(for Conditional Access\)* |
| [Conditional Access policies block access from noncompliant devices](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-data#conditional-access-policies-block-access-from-noncompliant-devices) | Microsoft Intune Plan 1  <br>Microsoft Entra ID P1 *\(for Conditional Access\)* |
| [Secure Wi-Fi profiles protect iOS devices from unauthorized network access](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-data#secure-wi-fi-profiles-protect-ios-devices-from-unauthorized-network-access) | Microsoft Intune Plan 1 |
| [Secure Wi-Fi profiles protect macOS devices from unauthorized network access](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-data#secure-wi-fi-profiles-protect-macos-devices-from-unauthorized-network-access) | Microsoft Intune Plan 1 |
| [Secure Wi-Fi profiles protect Android devices from unauthorized network access](https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-data#secure-wi-fi-profiles-protect-android-devices-from-unauthorized-network-access) | Microsoft Intune Plan 1 |

For license details, see:

- [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/fundamentals/licensing)
- [Microsoft Entra licensing](https://learn.microsoft.com/en-us/entra/fundamentals/licensing)

## Related content

- [Zero Trust deployment approach with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/zero-trust-deployment)
- [Deployment guide for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/get-started)
- [Protect data and devices with Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-security/overview)
- [Configure Microsoft Entra for increased security \(Preview\)](https://learn.microsoft.com/en-us/entra/fundamentals/configure-security)
