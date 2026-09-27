<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/jamf -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Jamf Mobile Threat Defense connector with Intune

Control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by Jamf. Jamf is a Mobile Threat Defense \(MTD\) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices by the Jamf service, including:

- Operating system vulnerabilities
- Malicious apps installed
- Malicious network profiles
- Cryptojacking

You can configure *Conditional Access* policies that are based on Jamf's risk assessment, enabled through Intune device compliance policies. Risk assessment policy can allow or block noncompliant devices from accessing corporate resources based on detected threats.

## How do Intune and Jamf Mobile Threat Defense help protect your company resources?

Jamf's mobile app seamlessly installs using Microsoft Intune. This app captures file system, network stack, and device and application telemetry \(where available\). This information synchronizes to the Jamf cloud service to assess the device's risk for mobile threats. These risk level classifications are configurable to suit your needs in the Jamf administrator console.

The compliance policy in Intune includes a rule for MTD based on Jamf's risk assessment. When this rule is enabled, Intune evaluates device compliance with the policy that you enabled.

For devices that are noncompliant, access to resources like Microsoft 365 can be blocked. Users on blocked devices receive guidance from the Jamf app to resolve the issue and regain access.

Jamf updates Intune with each device's latest threat level \(Secure, Low, Medium, or High\) whenever it changes. This threat level is continuously recalculated by the Jamf Security Cloud and is based upon device state, network activity, and numerous mobile threat intelligence feeds across various threat categories.

These categories and their associated threat levels are configurable in Jamf Security Cloud portal such that the total calculated threat level for each device is customizable per your organization's security requirements. With threat level in hand, there are two Intune policy types that make use of this information to manage access to corporate data:

- Using **Device Compliance Policies** with Conditional Access, administrators set policies to automatically mark a managed device as “out of compliance” based upon the Jamf-reported threat level. This compliance flag empowers Conditional Access policies to allow or deny access to applications that utilize modern authentication. See [Create Mobile Threat Defense \(MTD\) device compliance policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-compliance-policy) with Intune for configuration details.
- Using **App Protection Policies** with Conditional Launch, administrators can set policies that are enforced at the native app level \(for example, Android and iOS/iPad OS apps like Outlook, OneDrive, etc.\) based upon the Jamf-reported threat level. These policies can also be used for unenrolled devices with MAM managed applications to provide uniform policy across all device platforms and ownership modes. See [Create Mobile Threat Defense app protection policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-app-protection-policy) with Intune for configuration details.

## Supported platforms

The following platforms are supported for Jamf when enrolled in Intune:

- Android 11 and later
- iOS / iPadOS 15.6 and later \(iOS App Bundle ID: com.jamf.trust\)

For more information about platform and device, see the [Jamf website](https://www.jamf.com/products/jamf-protect/).

## Prerequisites

- Microsoft Intune Plan 1 subscription
- Microsoft Entra ID
- Jamf Mobile Threat Defense

For more information, see [Jamf Mobile Security](https://www.jamf.com/solutions/threat-prevention-remediation/).

## Sample scenarios

Here are the common scenarios when using Jamf MTD with Intune.

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices from common tools until you can resolve the threat. Common blocks include:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected*:

![Product flow for blocking access due to malicious apps.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/jamf/jamf-malicious-apps-blocked.png)

*Access granted on remediation*:

![Product flow for granting access when malicious apps are remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/jamf/jamf-malicious-apps-unblocked.png)

### Control access based on threat to network

Detect threats to your network such as man-in-the-middle attacks and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi*:

![Product flow for blocking access through Wi-Fi due to an alert.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/jamf/jamf-network-wifi-blocked.png)

*Access granted on remediation*:

![Product flow for granting access through Wi-Fi after the alert is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/jamf/jamf-network-wifi-unblocked.png)

## Control access to SharePoint Online based on threat to network

Detect threats to your network such as Man-in-the-middle attacks, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected*:

![Product flow for blocking access to the organizations files due to an alert.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/jamf/jamf-network-spo-blocked.png)

*Access granted on remediation*:

![Product flow for granting access to the organizations files after the alert is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/jamf/jamf-network-spo-unblocked.png)

### Control access on unenrolled devices based on threats from malicious apps

When the Jamf Mobile Threat Defense solution considers a device to be infected:

![Product flow for App protection policies to block access due to malware.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/jamf/jamf-mobile-app-policy-block.png)

*Access is granted on remediation*:

![Product flow for App protection policies to grant access after malware is remediated.](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/jamf/jamf-mobile-app-policy-remediated.png)

## Related content

- [Integrate Jamf with Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-jamf)
- [Set up Jamf apps](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/assign-apps)
- [Create Jamf device compliance policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-compliance-policy)
- [Enable Jamf MTD connector](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector)
