<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/blackberry -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Use BlackBerry Protect Mobile with Intune

You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by BlackBerry Protect Mobile \(powered by Cylance AI\), a mobile threat defense \(MTD\) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the BlackBerry Protect Mobile app.

You can configure Conditional Access policies based on a BlackBerry Protect risk assessment, enabled through Intune device compliance policies for enrolled devices. You can set up your policies to allow or block noncompliant devices from accessing corporate resources based on detected threats. For unenrolled devices, you can use app protection policies to enforce a block or selective wipe based on detected threats.

## Supported platforms

- **Android 9.0 and later**
- **iOS 13.0 and later**

## Prerequisites

- Microsoft Entra ID P1
- Microsoft Intune Plan 1 subscription
- BlackBerry UES account with access to UES management console

## How do Intune and the BlackBerry MTD connector help protect your company resources?

For Android and iOS/iPadOS, the CylancePROTECT app captures file system, network stack, device, and application telemetry where available, then sends the data to the Cylance AI Protection cloud service to assess the device's risk for mobile threats.

- **Support for enrolled devices** - Intune device compliance policy includes a rule for MTD, which can use risk assessment information from CylancePROTECT \(BlackBerry\). When the MTD rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources, such as Exchange Online and SharePoint Online. Users also receive guidance from the BlackBerry Protect app installed on their devices to resolve the issue and regain access to corporate resources. To support using BlackBerry Protect with enrolled devices:

  - [Add MTD apps to devices](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/assign-apps)
  - [Create a device compliance policy that supports MTD](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-compliance-policy)
  - [Enable the MTD connector in Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector)

- **Support for unenrolled devices** - Intune can use the risk assessment data from the CylancePROTECT \(BlackBerry\) app on unenrolled devices when you use Intune app protection policies. Admins can use this combination to help protect corporate data within a [Microsoft Intune protected app](https://learn.microsoft.com/en-us/intune/app-management/ref-protected-apps), Admins can also issue a block or selective wipe for corporate data on those unenrolled devices. To support using Better Mobile with unenrolled devices:

  - [Add the MTD app to unenrolled devices](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/add-apps-unenrolled-devices)
  - [Create a Mobile Threat Defense app protection policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-app-protection-policy)
  - [Enable the MTD connector in Intune for unenrolled devices](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-unenrolled-devices)

## Sample scenarios

The following scenarios demonstrate the use of CylancePROTECT \(BlackBerry\) MTD when integrated with Intune:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected:*

![Diagram of product flow for blocking access due to malicious apps.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/blackberry/blackberry-malicious-apps-blocked.png)

*Access granted on remediation:*

![Diagram of product flow for granting access when malicious apps are remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/blackberry/blackberry-malicious-apps-unblocked.png)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi:*

![Diagram of product flow for blocking access through Wi-Fi due to an alert.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/blackberry/blackberry-network-wifi-blocked.png)

*Access granted on remediation:*

![Diagram of product flow for granting access through Wi-Fi after the alert is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/blackberry/blackberry-network-wifi-unblocked.png)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected:*

![Diagram of product flow for blocking access to the organizations files due to an alert.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/blackberry/blackberry-network-spo-blocked.png)

*Access granted on remediation:*

![Diagram of product flow for granting access to the organizations files after the alert is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/blackberry/blackberry-network-spo-unblocked.png)

## Control access on unenrolled devices based on threats from malicious apps

When the BlackBerry Mobile Threat Defense solution considers a device to be infected:

![Diagram of product flow for App protection policies to block access due to malware.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/blackberry/blackberry-mobile-app-policy-block.png)

Access is granted on remediation:

![Diagram of product flow for App protection policies to grant access after malware is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/blackberry/blackberry-mobile-app-policy-remediated.png)

## Next steps

- [Integrate CylancePROTECT Mobile with Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-blackberry)
- [Set up CylancePROTECT app](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/assign-apps)
- [Create CylancePROTECT device compliance policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-compliance-policy)
- [Enable CylancePROTECT Mobile MTD connector](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector)
