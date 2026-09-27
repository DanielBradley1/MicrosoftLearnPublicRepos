<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/sentinelone -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# SentinelOne Mobile Threat Defense connector with Intune

You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by SentinelOne, a Mobile Threat Defense \(MTD\) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the SentinelOne app.

You can configure Conditional Access policies that are based on SentinelOne risk assessment, enabled through Intune device compliance policies for enrolled devices. You can use these policies to allow or block noncompliant devices access to corporate resources based on detected threats. For unenrolled devices, you can use app protection policies to enforce a block or selective wipe based on detected threats.

## Supported platforms

- **Android 5.0 and later**
- **iOS 10.0 and later**

## Prerequisites

- Microsoft Entra ID P1
- Microsoft Intune Plan 1 subscription
- SentinelOne Mobile Threat Defense subscription

  - For more information, see [SentinelOne website](https://www.sentinelone.com/).

## How do Intune and SentinelOne help protect your company resources?

For Android and iOS/iPadOS The SentinelOne app captures file system, network stack, device, and application telemetry where available. Then the app sends the data to the SentinelOne cloud service to assess the device's risk for mobile threats.

- **Support for enrolled devices** - Intune device compliance policy includes a rule for Mobile Threat Defense \(MTD\), which can use risk assessment information from SentinelOne. When the MTD rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources like Exchange Online and SharePoint Online. Users also receive guidance from the SentinelOne app installed in their devices to resolve the issue and regain access to corporate resources. To support using SentinelOne with enrolled devices:

  - [Add MTD apps to devices](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/assign-apps)
  - [Create a device compliance policy that supports MTD](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-compliance-policy)
  - [Enable the MTD connector in Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector)

- **Support for unenrolled devices** - Intune can use the risk assessment data from the SentinelOne app on unenrolled devices when you use Intune app protection policies. Admins can use this combination to help protect corporate data within a [Microsoft Intune protected app](https://learn.microsoft.com/en-us/intune/app-management/ref-protected-apps), Admins can also issue a block or selective wipe for corporate data on those unenrolled devices. To support using SentinelOne with unenrolled devices:

  - [Add the MTD app to unenrolled devices](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/add-apps-unenrolled-devices)
  - [Create a Mobile Threat Defense app protection policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-app-protection-policy)
  - [Enable the MTD connector in Intune for unenrolled devices](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-unenrolled-devices)

## Sample scenarios

See below a few scenarios when integrating SentinelOne with Intune:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected:*

![Product flow for blocking access due to malicious apps.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/sentinelone/malicious-apps-blocked-sentinelone.png)

*Access granted on remediation:*

![Product flow for granting access when malicious apps are remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/sentinelone/malicious-apps-unblocked-sentinelone.png)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi:*

![Product flow for blocking access through Wi-Fi due to an alert.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/sentinelone/network-wifi-blocked-sentinelone.png)

*Access granted on remediation:*

![Product flow for granting access through Wi-Fi after the alert is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/sentinelone/network-wifi-unblocked-sentinelone.png)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected:*

![Product flow for blocking access to the organizations files due to an alert.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/sentinelone/network-spo-blocked-sentinelone.png)

*Access granted on remediation:*

![Product flow for granting access to the organizations files after the alert is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/sentinelone/network-spo-unblocked-sentinelone.png)

### Control access on unenrolled devices based on threats from malicious apps

When the sentinelone Mobile Threat Defense solution considers a device to be infected:

![Product flow for App protection policies to block access due to malware.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/sentinelone/mobile-app-policy-block-sentinelone.png)

*Access is granted on remediation*:

![Product flow for App protection policies to grant access after malware is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/sentinelone/mobile-app-policy-remediated-sentinelone.png)

## Next steps

- [Integrate sentinelone with Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-sentinelone)
- [Set up sentinelone apps](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/assign-apps)
- [Create sentinelone device compliance policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-compliance-policy)
- [Enable sentinelone MTD connector](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector)
- [Create an MTD app protection policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-app-protection-policy)
