<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/pradeo -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Pradeo Mobile Threat Defense connector with Intune

You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by Pradeo, a Mobile Threat Defense \(MTD\) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the Pradeo app.

You can configure Conditional Access policies based on Pradeo risk assessment enabled through Intune device compliance policies, which you can use to allow or block noncompliant devices to access corporate resources based on detected threats.

Note

This Mobile Threat Defense vendor is not supported for unenrolled devices.

## Supported platforms

- **Android 5.1 and later**
- **iOS 12.1 and later**

## Prerequisites

- Microsoft Entra ID P1
- Microsoft Intune Plan 1 subscription
- Pradeo Security for Mobile Threat Defense subscription

  - For more information, see the [Pradeo website](https://pradeo.com/en/use-cases/securing-mobile-applications/).

## How do Intune and Pradeo help protect your company resources?

Pradeo app for Android and iOS/iPadOS captures file system, network stack, device, and application telemetry where available, and then sends the telemetry data to the Pradeo cloud service to assess the device's risk for mobile threats.

The Intune device compliance policy includes a rule for Pradeo Mobile Threat Defense, which is based on the Pradeo risk assessment. When this rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources like Exchange Online and SharePoint Online. Users also receive guidance from the Pradeo app installed in their devices to resolve the issue and regain access to corporate resources.

## Sample scenarios

Here are some common scenarios.

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices from the following actions until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected:*

![Product flow for blocking access due to malicious apps.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/pradeo/pradeo-maliciousapps-blocked.png)

*Access granted on remediation:*

![Product flow for granting access when malicious apps are remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/pradeo/pradeo-maliciousapps-unblocked.png)

### Control access based on threat to network

Detect threats to your network like **Man-in-the-middle** attacks, and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi:*

![Product flow for blocking access through Wi-Fi due to an alert.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/pradeo/pradeo-network-wifi-blocked.png)

*Access granted on remediation:*

![Product flow for granting access through Wi-Fi after the alert is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/pradeo/pradeo-network-wifi-unblocked.png)

### Control access to SharePoint Online based on threat to network

Detect threats to your network like **Man-in-the-middle** attacks, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected:*

![Product flow for blocking access to the organizations files due to an alert.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/pradeo/pradeo-network-spo-blocked.png)

*Access granted on remediation:*

![Product flow for granting access to the organizations files after the alert is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/pradeo/pradeo-network-spo-unblocked.png)

## Next steps

- [Integrate Pradeo with Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-pradeo)
- [Set up Pradeo apps](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/assign-apps)
- [Create Pradeo device compliance policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-compliance-policy)
- [Enable Pradeo MTD connector](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector)
