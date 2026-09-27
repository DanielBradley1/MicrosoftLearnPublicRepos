<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-data -->
<!-- Sitemap-Last-Modified: 2026-04-16 -->

# Configure Microsoft Intune for Zero Trust: Secure data on devices \(Preview\)

Protecting sensitive data across mobile apps and networks is a key part of a Zero Trust strategy. The following Intune recommendations reflect Microsoft’s [Secure Future Initiative](https://www.microsoft.com/trust-center/security/secure-future-initiative?msockid=2bad2df65a416adb0e5838355b3e6b95#SFI-pillars) by enforcing secure access, safeguarding information, and reducing risk across platforms. These checks help keep business data safe by applying app protections, ensuring device compliance, and securing connections to corporate networks.

## Zero Trust security recommendations

### Data on Android is protected by app protection policies

Without app protection policies, corporate data accessed on Android devices is vulnerable to leakage through unmanaged or malicious apps. Users can unintentionally copy sensitive information into personal apps, store data insecurely, or bypass authentication controls. This risk is amplified on devices that aren't fully managed, where corporate and personal contexts coexist, increasing the likelihood of data exfiltration or unauthorized access.

Enforcing app protection policies ensures that corporate data is only accessible through trusted apps and remains protected even on personal or BYOD Android devices.

These policies enforce encryption, restrict data sharing, and require authentication, reducing the risk of data leakage and aligning with Zero Trust principles of data protection and Conditional Access.

**Remediation action**

Deploy Intune app protection policies that encrypt data, restrict sharing, and require authentication in approved Android apps:

- [Deploy Intune app protection policies](https://learn.microsoft.com/en-us/intune/app-management/protection/create-policy#create-an-iosipados-or-android-app-protection-policy)
- [Review the Android app protection settings reference](https://learn.microsoft.com/en-us/intune/app-management/protection/ref-settings-android)

For more information, see:

- [Learn about using app protection policies](https://learn.microsoft.com/en-us/intune/app-management/protection/overview)

### Data on iOS/iPadOS is protected by app protection policies

Without app protection policies, corporate data accessed on iOS/iPadOS devices is vulnerable to leakage through unmanaged or personal apps. Users can unintentionally copy sensitive information into unsecured apps, store data outside corporate boundaries, or bypass authentication controls. This risk is especially high on BYOD devices, where personal and work contexts coexist, increasing the likelihood of data exfiltration or unauthorized access.

App protection policies ensure corporate data remains secure within approved apps, even on personal devices. These policies enforce encryption, restrict data sharing, and require authentication, reducing the risk of data leakage and aligning with Zero Trust principles of data protection and Conditional Access.

**Remediation action**

Deploy Intune app protection policies that encrypt corporate data, restrict sharing, and require authentication in approved iOS/iPadOS apps:

- [Deploy Intune app protection policies](https://learn.microsoft.com/en-us/intune/app-management/protection/create-policy#create-an-iosipados-or-android-app-protection-policy)
- [Review the iOS app protection settings reference](https://learn.microsoft.com/en-us/intune/app-management/protection/ref-settings-ios)

For more information, see:

- [Learn about using app protection policies](https://learn.microsoft.com/en-us/intune/app-management/protection/overview)

### Conditional Access policies block access from unmanaged apps

If Microsoft Entra Conditional Access policies aren't combined with app protection controls, users can connect to corporate resources through unmanaged or unsecured applications. This exposes sensitive data to risks such as data leakage, unauthorized access, and regulatory noncompliance. Without safeguards like app-level data protection, access restrictions, and data loss prevention, threat actors can exploit unprotected apps to bypass security controls and compromise organizational data.

Enforcing Intune app protection policies within Conditional Access ensures only trusted apps can access corporate data. This supports Zero Trust by enforcing access decisions based on app trust, data containment, and usage restrictions.

**Remediation action**

Configure app-based Conditional Access policies in Microsoft Entra and Intune to require app protection for access to corporate resources:

- [Set up app-based Conditional Access policies with Intune](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/create-app-based-policy)

For more information, see:

- [What is Conditional Access?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
- [Learn about app-based Conditional Access policies with Intune](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/app-based-policies)

### Conditional Access policies block access from noncompliant devices

If Microsoft Entra Conditional Access policies don't enforce device compliance, users can connect to corporate resources from devices that don't meet security standards. This exposes sensitive data to risks like malware, unauthorized access, and regulatory noncompliance. Without controls like encryption enforcement, device health checks, and access restrictions, threat actors can exploit noncompliant devices to bypass security measures and maintain persistence.

Requiring device compliance in Conditional Access policies ensures only trusted and secure devices can access corporate resources. This supports Zero Trust by enforcing access decisions based on device health and compliance posture.

**Remediation action**

Configure Conditional Access policies in Microsoft Entra to require device compliance before granting access to corporate resources:

- [Create a device compliance-based Conditional Access policy](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-device-compliance)

For more information, see:

- [What is Conditional Access?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
- [Integrate device compliance results with Conditional Access](https://learn.microsoft.com/en-us/intune/device-security/compliance/overview#integrate-with-conditional-access)

### Secure Wi-Fi profiles protect iOS devices from unauthorized network access

If Wi-Fi profiles aren't properly configured and assigned, users can connect insecurely or fail to connect to trusted networks, exposing corporate data to interception or unauthorized access. Without centralized management, devices rely on manual configuration, increasing the risk of misconfiguration, weak authentication, and connection to rogue networks.

Centrally managing Wi-Fi profiles for iOS devices in Intune ensures secure and consistent connectivity to enterprise networks. This enforces authentication and encryption standards, simplifies onboarding, and supports Zero Trust by reducing exposure to untrusted networks.

**Remediation action**

Use Intune to configure and assign secure Wi-Fi profiles for iOS/iPadOS devices to enforce authentication and encryption standards:

- [Deploy Wi-Fi profiles to devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wifi#create-the-profile)

For more information, see:

- [Review the available Wi-Fi settings for iOS and iPadOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-apple)

### Secure Wi-Fi profiles protect macOS devices from unauthorized network access

If Wi-Fi profiles aren't properly configured and assigned, macOS devices can fail to connect to secure networks or connect insecurely, exposing corporate data to interception or unauthorized access. Without centralized management, devices rely on manual configuration, increasing the risk of misconfiguration, weak authentication, and connection to rogue networks. These gaps can lead to data interception, unauthorized network access, and compliance violations.

Centrally managing Wi-Fi profiles for macOS devices in Intune ensures secure and consistent connectivity to enterprise networks. This enforces authentication and encryption standards, simplifies onboarding, and supports Zero Trust by reducing exposure to untrusted networks.

**Remediation action**

Use Intune to configure and assign secure Wi-Fi profiles for macOS devices to enforce authentication and encryption standards:

- [Configure Wi-Fi settings for macOS devices in Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wifi#create-the-profile)

For more information, see:

- [Review the available Wi-Fi settings for macOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-apple)

### Secure Wi-Fi profiles protect Android devices from unauthorized network access

If Wi-Fi profiles aren't properly configured and assigned, Android devices can fail to connect to secure networks or connect insecurely, exposing corporate data to interception or unauthorized access. Without centralized management, devices rely on manual configuration, increasing the risk of misconfiguration, weak authentication, and connection to rogue networks.

Centrally managing Wi-Fi profiles for Android devices in Intune ensures secure and consistent connectivity to enterprise networks. This enforces authentication and encryption standards, simplifies onboarding, and supports Zero Trust by reducing exposure to untrusted networks.

Use Intune to configure secure Wi-Fi profiles that enforce authentication and encryption standards.

**Remediation action**

Use Intune to configure and assign secure Wi-Fi profiles for Android devices to enforce authentication and encryption standards:

- [Deploy Wi-Fi profiles to devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wifi#create-the-profile)

For more information, see:

- [Review the available Wi-Fi settings for Android devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-android-enterprise)

## Related content

- [Deployment guide for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/get-started)
- [Protect data and devices with Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-security/overview)
- [Configure Microsoft Entra for increased security \(Preview\)](https://learn.microsoft.com/en-us/entra/fundamentals/configure-security)
