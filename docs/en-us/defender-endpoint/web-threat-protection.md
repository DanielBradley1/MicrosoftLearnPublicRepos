<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/web-threat-protection -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Protect your organization against web threats

Web threat protection is part of [Web protection](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-overview) in Defender for Endpoint. It uses [network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection) to secure your devices against web threats. By integrating with Microsoft Edge and popular third-party browsers like Chrome and Firefox, web threat protection stops web threats without a web proxy and can protect devices while they're away or on premises. Web threat protection stops access to phishing sites, malware vectors, exploit sites, untrusted or low-reputation sites, and sites that you've blocked because they're in your [custom indicator list](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview).

Before you configure web threat protection, review the [Prerequisites](#prerequisites) section, which requires enabling network protection or Microsoft Defender SmartScreen.

Note

It might take up to two hours for devices to receive new custom indicators.

## Prerequisites

Web threat protection uses network protection to provide web browsing security in Edge \(excepting Windows devices\), non-Microsoft web browsers and nonbrowser processes. On Windows devices, web threat protection in Edge uses Microsoft Defender SmartScreen and network protection isn't required to be enabled.

To turn on Microsoft Defender SmartScreen in Edge: [Configure Microsoft Defender SmartScreen](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-policies#smartscreenenabled).

To turn on network protection on your devices:

- Edit the Defender for Endpoint security baseline under **Web & Network Protection** to enable network protection before deploying or redeploying it. [Learn about reviewing and assigning the Defender for Endpoint security baseline](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines-security-baseline#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline)
- Turn network protection on using Intune device configuration, SCCM, Group Policy, or your MDM solution. [Read more about enabling network protection](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection)

Note

If you set network protection to **Audit only**, blocking is unavailable. Also, you are able to detect and log attempts to access malicious and unwanted websites on Microsoft Edge only.

## Configure web threat protection

The legacy **Web protection** policy in Intune has been deprecated and web threat protection is enabled if [network protection](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection) or [Microsoft Defender SmartScreen](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-policies#smartscreenenabled) is enabled on your devices.

## Related articles

- [Web protection overview](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-overview)
- [Web threat protection](https://learn.microsoft.com/en-us/defender-endpoint/web-threat-protection)
- [Monitor web security](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-monitoring)
- [Respond to web threats](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-response)
- [Network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection)
