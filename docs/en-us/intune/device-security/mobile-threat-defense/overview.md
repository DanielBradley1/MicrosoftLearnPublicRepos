<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/overview -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Mobile Threat Defense integration with Microsoft Intune

Note

This article is about third-party Mobile Threat Defense vendors. For more information on Microsoft Defender for Endpoint, see [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/overview).

Intune can integrate data from a Mobile Threat Defense \(MTD\) vendor as an information source for device compliance policies and device Conditional Access rules. Use this information to help protect corporate resources like Exchange and SharePoint by blocking access from compromised mobile devices.

Intune can use this same data as a source for unenrolled devices using Intune app protection policies. As such, admins can use this information to help protect corporate data within a [Microsoft Intune protected app](https://learn.microsoft.com/en-us/intune/app-management/ref-protected-apps), and issue a block or selective wipe.

## Government cloud support

Mobile Threat Defense \(MTD\) connectors for Android and iOS/iPadOS devices are available in the following sovereign clouds, provided that the MTD partners also support these environments. When you sign in to your tenant, you can view the available connectors in that specific environment:

- U.S. Government Community Cloud \(GCC\) High
- 21Vianet

To learn more about Intune and government clouds, see:

- [Microsoft Intune for US Government GCC High support](https://learn.microsoft.com/en-us/enterprise-mobility-security/solutions/ems-intune-govt-service-description)
- [Microsoft Intune for US Government GCC High and DoD service description](https://learn.microsoft.com/en-us/intune/fundamentals/government-service)
- [Microsoft Intune operated by 21Vianet in China](https://learn.microsoft.com/en-us/intune/fundamentals/china)

## Protect corporate resources

Integrating information from MTD vendors can help you protect your corporate resources from threats that affect mobile platforms.

Typically, companies are proactive in protecting PCs from vulnerabilities and attacks while mobile devices often go unmonitored and unprotected. Where mobile platforms have built-in protection such as app isolation and vetted consumer app stores, these platforms remain vulnerable to sophisticated attacks. As more employees use devices for work and to access sensitive information, the information from MTD vendors can help you protect devices and your resources from increasingly sophisticated attacks.

## Intune Mobile Threat Defense connectors

Intune uses a Mobile Threat Defense connector to create a channel of communication between Intune and your chosen MTD vendor. Intune MTD partners offer intuitive, easy-to-deploy applications for mobile devices. These applications actively scan and analyze threat information to share with Intune. Intune can use the data for either reporting or enforcement purposes.

For example, a connected MTD app reports to the MTD vendor that a phone on your network is currently connected to a network that is vulnerable to man-in-the-middle attacks. This information is categorized to an appropriate risk level of low, medium, or high. This risk level is then compared with the risk level allowances you set in Intune. Based on this comparison, you can revoke access to certain resources while the device is compromised.

### Mobile Threat Defense role for Android

On Android Enterprise fully managed and corporate-owned with work profile devices, you can grant your MTD partner enhanced security permissions through the MTD connector. When enabled, the MTD app receives exemptions from app suspension, hibernation, power restrictions, and user controls, helping the app maintain continuous threat protection on managed devices. You can grant these permissions to one MTD partner at a time. For Microsoft Defender for Endpoint, you can also enable automatic launch of the app during device setup. For details about configuring the MTD role toggles, see [Mobile Threat Defense toggle options](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector#mobile-threat-defense-role).

### Connector status

When you add a Mobile Threat Defense connector to your tenant, the status displays one of the following states:

| Connector status | Definition | Device threat messages blocked? | App Sync request messages blocked? | Certificate Sync request messages blocked? |
| --- | --- | --- | --- | --- |
| **Unavailable** | Connector is deprovisioned. The MTD partner needs to talk to Intune to provision it again. | Yes \(starting 2308\) | Yes \(starting 2308\) | Yes \(starting 2601\) |
| **Not Set Up** | Connector setup isn't complete. There might be additional steps or permissions required within Intune or the MTD partner for this status to change to **Available**. | Yes \(starting 2309\) | Yes \(starting 2309\) | Yes \(starting 2601\) |
| **Available** | Connector setup is complete. At least one platform toggle must be turned on for this status to change to **Enabled**. | No | No | No |
| **Enabled** | Connector setup is complete, and at least one platform toggle is currently turned on for this connector. | No | No | No |
| **Unresponsive** | Connector isn't responsive. If the connector status continues to be unresponsive for the number of days defined in **Number of days until partner is unresponsive**, Intune ignores the compliance state. | No | No | No |
| **Error** | Connector has an error code. Some MTD partners might choose to send this code in an error case. | No | No | No |

## Data that Intune collects for Mobile Threat Defense

Intune can collect and share two types of inventory data with Mobile Threat Defense \(MTD\) partners to enhance threat analysis capabilities. Both services are opt-in; no information is shared by default. An Intune administrator must explicitly enable these features in the Mobile Threat Defense connector settings before any data is shared.

### App inventory \(App Sync\)

**App Sync for iOS/iPadOS devices** enables MTD partners to request metadata about applications installed on enrolled devices. When you turn on this feature, your MTD service provider receives inventories from both corporate and personally owned iOS/iPadOS devices during device check-in intervals.

**Data shared includes:**

- App ID
- App Version
- App Short Version
- App Name
- App Bundle Size
- App Dynamic Size
- Whether the app is ad-hoc code-signed \(starting 2309\)
- Whether the app is installed from the app Microsoft Store \(starting 2309\)
- Whether the app is a beta app \(installed via TestFlight\) \(starting 2309\)
- Whether the app is a device-based volume purchased app \(starting 2309\)
- Whether the app is validated or not
- Whether the app is managed or not

### Certificate inventory \(Certificate Sync\)

**Certificate Sync for iOS/iPadOS devices** enables supported MTD partners to request information about certificates installed on enrolled devices. When you enable this feature, your MTD service provider receives certificate inventories from both corporate and personally owned iOS/iPadOS devices during device check-in intervals.

**Data shared includes:**

- Account ID
- Entra ID Device ID
- Device Owner
- Certificate List

  - Common Name
  - Data
  - Is Identity

**The following Mobile Threat Defense partners support Certificate Sync:**

- Zimperium

## Sample scenarios for enrolled devices using device compliance policies

When the Mobile Threat Defense solution considers a device infected:

![Image showing a Mobile Threat Defense infected device](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/overview/mtd-image-1.png)

Access is granted when the device is remediated:

![Image showing a Mobile Threat Defense Access granted](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/overview/mtd-image-2.png)

## Sample scenarios for unenrolled devices using Intune app protection policies

When the Mobile Threat Defense solution considers a device infected:  
![Image that shows a Mobile Threat Defense infected device](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/overview/mtd-image-3.png)

Access is granted when the device is remediated:  
![Image showing a Mobile Threat Defense access granted](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/media/overview/mtd-image-4.png)

Note

Use one Mobile Threat Defense vendor per tenant per platform.

For Device Compliance, you can use multiple Mobile Threat Defense vendors with a single Intune tenant. However, when you configure two or more vendors for the same platform, all devices that run that platform must install each MTD app and scan for threats. If any configured app fails to submit a scan, the device is marked as non-compliant.

This recommendation doesn't apply to Defender for Endpoint. You can use Defender for Endpoint with a third-party MTD app and check compliance separately by deploying different compliance policies to different groups.

## Mobile Threat Defense partners

Learn how to protect access to company resources based on device, network, and application risk by using:

- [Better Mobile](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/better-mobile) - *\(Android, iOS/iPadOS\)*
- [BlackBerry Protect Mobile](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/blackberry) - *\(Android, iOS/iPadOS\)*
- [Check Point Harmony Mobile](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/checkpoint-harmony) - *\(Android, iOS/iPadOS\)*
- [CrowdStrike Falcon for Mobile](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/crowdstrike-falcon) - *\(Android, iOS/iPadOS\)*
- [iVerify Enterprise](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/iverify) - *\(Android, iOS/iPadOS\)*
- [Jamf Mobile Threat Defense](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/jamf) - *\(Android, iOS/iPadOS\)*
- [Lookout for Work](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/lookout) - *\(Android, iOS/iPadOS\)*
- [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/overview) - *\(Android, iOS/iPadOS, Windows\)*
- [Pradeo](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/pradeo) - *\(Android, iOS/iPadOS\)*
- [SentinelOne](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/sentinelone) - *\(Android, iOS/iPadOS\)*
- [Sophos Mobile](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/sophos) - *\(Android, iOS/iPadOS\)*
- [Symantec Endpoint Protection Mobile](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/symantec) - *\(Android, iOS/iPadOS\)*
- [Trellix Mobile Security](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/trellix) - *\(Android, iOS/iPadOS\)*
- [Trend Micro Mobile Security as a Service](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/trend-micro) - *\(Android, iOS/iPadOS\)*
- [Trustd Mobile](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/trustd-mobile) - *\(Android, iOS/iPadOS\)*
- [Windows Security Center](https://learn.microsoft.com/en-us/intune/app-management/protection/enable-mam-windows) - *\(Windows\)* - *For information about the Windows versions that support this connector, see [Data protection for Windows MAM](https://learn.microsoft.com/en-us/intune/app-management/protection/enable-mam-windows).*
- [Zimperium](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/zimperium) - *\(Android, iOS/iPadOS\)*
