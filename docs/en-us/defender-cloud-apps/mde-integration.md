<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/mde-integration -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Integrate Microsoft Defender for Endpoint with Microsoft Defender for Cloud Apps

[Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) is a security platform for intelligent protection, detection, investigation, and response. Defender for Endpoint protects endpoints from cyber threats, detects advanced attacks and data breaches, automates security incidents, and improves security posture.

The out-of-the-box integration between Microsoft Defender for Cloud Apps and Microsoft Defender for Endpoint simplifies cloud discovery and enables device-based investigation.

Important

This article focuses on shadow IT discovery capabilities from Defender for Endpoint logs. For more information on shadow IT governing capabilities via Defender for Endpoint, see [Govern discovered apps using Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-cloud-apps/mde-govern).

## Prerequisites

Before you configure the integration, make sure you meet the following prerequisites:

- Microsoft Defender for Cloud Apps license
- Devices must be onboarded to [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-client)
- One of the following:

  - Microsoft Defender for Endpoint with Plan 2
  - Microsoft Defender for Business \(standalone or as part of Microsoft 365 Business Premium\)


  For more information, see [Compare Microsoft endpoint security plans](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1-2).

- Apps using one of the following operating systems:

  - Windows 10 version 1709 \(OS Build 16299.1085 with KB4493441\)
  - Windows 10 version 1803 \(OS Build 17134.704 with KB4493464\)
  - Windows 10 version 1809 \(OS Build 17763.379 with KB4489899\), or later Windows 10 and Windows 11 versions
  - macOS, on devices with [Defender for Endpoint version 20.123072.25.0](https://learn.microsoft.com/en-us/defender-endpoint/mac-whatsnew) or higher

- To support integrations for macOS apps, you must turn on network protection capabilities in Microsoft Defender for Endpoint. Since network protection only audits TCP connection close events, UDP protocols aren't covered for macOS support. For more information, see [Turn on network protection](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection)
- \(Recommended\) Enable Microsoft Defender Antivirus:

  - **[Real-time protection enabled](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus)**
  - **[Cloud-delivered protection enabled](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-configure)**
  - **[Network protection enabled and configured to block mode](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/enable-network-protection)**

Note

While Microsoft Defender Antivirus is highly recommended for discovery, it's not mandatory. Some discovery data is still available when Defender Antivirus is disabled.

## How it works

On its own, Defender for Cloud Apps collects logs from your endpoints using either [logs you upload](https://learn.microsoft.com/en-us/defender-cloud-apps/create-snapshot-cloud-discovery-reports) or by [configuring automatic log upload](https://learn.microsoft.com/en-us/defender-cloud-apps/discovery-docker). The out-of-the-box integration enables you to take advantage of the logs Defender for Endpoint's agent creates when it runs on Windows and monitors network transactions. Use these Defender for Endpoint network transaction logs for Shadow IT discovery across the Windows devices on your network.

The integration doesn't require extra deployment steps or routing or mirroring traffic from your endpoints. It provides the following capabilities:

- **Logs from your endpoints that are sent to Defender for Cloud Apps provide user and device information for traffic activities**. Pairing device context with the username provides a full picture across your network enabling you to determine which user did which activity from which device.
- **When you identify a risky user, check the devices that the user accessed to detect potential risks**. If you identify a risky device, check all the users who used it to detect further potential risks.
- **Once traffic information is collected, you're ready to [deep dive into cloud app use](https://learn.microsoft.com/en-us/defender-cloud-apps/discovered-apps#deep-dive-into-discovered-apps) in your organization**. Defender for Cloud Apps takes advantage of Defender for Endpoint Network Protection capabilities to block endpoint device access to cloud apps. For more information about governing the discovered apps, see [Govern discovered apps using Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-cloud-apps/mde-govern).

Customers integrating with macOS devices may observe a spike in CPU consumption.

Tip

Watch these videos showing the benefits of using Defender for Endpoint with Defender for Cloud Apps: [Discover and block Shadow IT using Defender for Endpoint](https://www.youtube.com/watch?v=MsHkTOoqSQo) and [Shadow IT discovery beyond the corporate network](https://www.youtube.com/watch?v=f8hbvbY1Hnc).

## Integrate Microsoft Defender for Endpoint with Defender for Cloud Apps 

Use the [Microsoft Defender portal](https://security.microsoft.com), the central management portal for Microsoft Defender services, to configure the integration.

To enable Defender for Endpoint integration with Defender for Cloud Apps:

1. In the Microsoft Defender portal, from the navigation pane, select **Settings** > **Endpoints** > **General** > **Advanced features**.
2. Toggle the **Microsoft Defender for Cloud Apps** to **On**.
3. Select **Save preferences**.

Note

It takes up to two hours after you enable the integration for the data to show up in Defender for Cloud Apps.

![Screenshot of the Defender for Endpoint Advanced features settings page with the Microsoft Defender for Cloud Apps toggle enabled.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/turn-on-advanced-features-for-microsoft-defender-for-cloud-apps.png)

To configure the severity for alerts sent to Microsoft Defender for Endpoint:

1. In the Microsoft Defender Portal, select **Settings** > **Cloud Apps** > **Cloud Discovery** > **Microsoft Defender for Endpoint**.
2. Under **Alerts**, select the global severity level for alerts.
3. Select **Save**.

   [![Screenshot that shows the Defender for Endpoint alert settings.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/mde-alert-severity-settings.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/mde-alert-severity-settings.png#lightbox)

## Next steps

After you enable the integration, use the following articles to investigate and govern discovered apps:

[Investigate apps discovered by Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-cloud-apps/mde-investigation)

[Govern apps discovered by Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-cloud-apps/mde-govern)

## Related videos

The following videos provide additional background and examples for using Defender for Endpoint with Defender for Cloud Apps.

[Discover and block Shadow IT using Defender for Endpoint](https://www.youtube.com/watch?v=MsHkTOoqSQo)

[Shadow IT discovery beyond the corporate network](https://www.youtube.com/watch?v=f8hbvbY1Hnc)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
