<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/trellix -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Use Trellix Mobile Security with Intune

You can control mobile device access to corporate resources using Conditional Access based on a risk assessment that's conducted by Trellix Mobile Security. Trellix Mobile Security is a Mobile Threat Defense \(MTD\) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the Trellix Mobile Security app.

You can configure Conditional Access policies that are based on Trellix Mobile Security risk assessment. These policies are enabled through Intune device compliance policies for enrolled devices, which you can use to allow or block noncompliant devices to access corporate resources based on detected threats. For unenrolled devices, you can use app protection policies to enforce a block or selective wipe based on detected threats.

## Supported platforms

- **Android 6.0 and later**
- **iOS 11.0 and later**

## Prerequisites

- Microsoft Entra ID P1 or P2
- Microsoft Intune Plan 1 subscription
- Trellix Mobile Security subscription

For more information, see the documentation for Trellix Mobile Security.

## How do Intune and Trellix Mobile Security help protect your company resources?

The Trellix Mobile Security app for Android and iOS/iPadOS captures file system, network stack, device, and application telemetry where available. Trellis then sends the telemetry data to the Trellix Mobile Security cloud service to assess the device's risk for mobile threats.

- **Support for enrolled devices** - Intune device compliance policy includes a rule for Mobile Threat Defense \(MTD\), which can use risk assessment information from Trellix Mobile Security. When the MTD rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources like Exchange Online and SharePoint Online. Users also receive guidance from the Trellix Mobile Security app installed in their devices to resolve the issue and regain access to corporate resources. To support using Trellix Mobile Security with enrolled devices:

  - [Add MTD apps to devices](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/assign-apps)
  - [Create a device compliance policy that supports MTD](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-compliance-policy)
  - [Enable the MTD connector in Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector)

- **Support for unenrolled devices** - Intune can use the risk assessment data from the Trellix Mobile Security app on unenrolled devices when you use Intune app protection policies. Admins can use this combination to help protect corporate data within a Microsoft Intune protected app, Admins can also issue a block or selective wipe for corporate data on those unenrolled devices. To support using Trellix Mobile Security with unenrolled devices:

  - [Add the MTD app to unenrolled devices](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/add-apps-unenrolled-devices)
  - [Create a Mobile Threat Defense app protection policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-app-protection-policy)
  - [Enable the MTD connector in Intune for unenrolled devices](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-unenrolled-devices)

## Sample scenarios

See below a few scenarios when integrating Trellix Mobile Security with Intune:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected:*

![Product flow for blocking access due to malicious apps.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/trellix/trellix-malicious-apps-blocked.png)

*Access granted on remediation:*

![Product flow for granting access when malicious apps are remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/trellix/trellix-malicious-apps-unblocked.png)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi:*

![Product flow for blocking access through Wi-Fi due to an alert.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/trellix/trellix-network-wifi-blocked.png)

*Access granted on remediation:*

![Product flow for granting access through Wi-Fi after the alert is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/trellix/trellix-network-wifi-unblocked.png)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected:*

![Product flow for blocking access to the organizations files due to an alert.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/trellix/trellix-network-spo-blocked.png)

*Access granted on remediation:*

![Product flow for granting access to the organizations files after the alert is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/trellix/trellix-network-spo-unblocked.png)

### Control access on unenrolled devices based on threats from malicious apps

When the Trellix Mobile Security mobile threat defense solution considers a device to be infected:

![Product flow for App protection policies to block access due to malware.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/trellix/trellix-mobile-app-policy-block.png)

Access is granted on remediation:

![Product flow for App protection policies to grant access after malware is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/trellix/trellix-mobile-app-policy-remediated.png)

## Next steps

- [Integrate Trellix Mobile Security with Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-trellix)
- [Set up Trellix Mobile Security apps](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/assign-apps)
- [Create Trellix Mobile Security device compliance policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-compliance-policy)
- [Enable Trellix Mobile Security MTD connector](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector)
- [Create an MTD app protection policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-app-protection-policy)
