<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/microsoft-cloud-app-security-integration -->
<!-- Sitemap-Last-Modified: 2026-06-14 -->

# Microsoft Defender for Cloud Apps in Defender for Endpoint overview

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Microsoft Defender for Cloud Apps is a comprehensive solution that gives visibility into cloud apps and services by allowing you to control and limit access to cloud apps, while enforcing compliance requirements on data stored in the cloud. For more information, see [Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/what-is-cloud-app-security).

Note

This feature is available with an E5 license for [Enterprise Mobility + Security](https://www.microsoft.com/en-us/security) on devices running Windows 10 version 1809 or later, or Windows 11.

## Microsoft Defender for Endpoint and Defender for Cloud Apps integration

Defender for Cloud Apps discovery relies on cloud traffic logs being forwarded to it from enterprise firewall and proxy servers. Microsoft Defender for Endpoint integrates with Defender for Cloud Apps by collecting and forwarding all cloud app networking activities, providing unparalleled visibility to cloud app usage. The monitoring functionality is built into the device, providing complete coverage of network activity.

<iframe src="https://learn-video.azurefd.net/vod/player?id=0bba87dc-5047-492b-add5-c942faa050d4" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

The integration provides the following major improvements to the existing Defender for Cloud Apps discovery:

- Available everywhere - Since the network activity is collected directly from the endpoint, it's available wherever the device is, on or off corporate network, as it's no longer depended on traffic routed through the enterprise firewall or proxy servers.
- Works out of the box, no configuration required - Forwarding cloud traffic logs to Defender for Cloud Apps requires firewall and proxy server configuration. With the Defender for Endpoint and Defender for Cloud Apps integration, there's no configuration required. Just switch it on in the Defender portal settings and you're good to go.
- Device context - Cloud traffic logs lack device context. Defender for Endpoint network activity is reported with the device context \(which device accessed the cloud app\), so you are able to understand exactly where \(device\) the network activity took place, in addition to who \(user\) performed it.

For more information about cloud discovery, see [Working with discovered apps](https://learn.microsoft.com/en-us/cloud-app-security/discovered-apps).

## Related topic

- [Configure Microsoft Defender for Cloud Apps integration](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-cloud-app-security-config)
