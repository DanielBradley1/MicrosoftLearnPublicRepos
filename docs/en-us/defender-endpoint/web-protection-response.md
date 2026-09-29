<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/web-protection-response -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# Respond to web threats

Web protection in Microsoft Defender for Endpoint lets you efficiently investigate and respond to alerts related to malicious websites and websites in your custom indicator list.

## View web threat alerts

Microsoft Defender for Endpoint generates the following [alerts](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts?toc=/defender-endpoint/toc.json&bc=/defender-endpoint/breadcrumb/toc.json#manage-alerts) for malicious or suspicious web activity:

- **Suspicious connection blocked by network protection**: This alert is generated when network protection \(in block mode\) stops an attempt to access a malicious website or a website in your custom indicator list.
- **Suspicious connection detected by network protection**: This alert is generated when network protection \(in audit mode\) detects an attempt to access a malicious website or a website in your custom indicator list.

Each alert provides the following information:

- Device that attempted to access the blocked website
- Application or program used to send the web request
- Malicious URL or URL in the custom indicator list
- Recommended actions for responders

[![The alert related to web threat protection](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-alert.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-alert.png#lightbox)

Note

To reduce the volume of alerts, Microsoft Defender for Endpoint consolidates web threat detections for the same domain on the same device each day to a single alert. Only one alert is generated and counted into the [web protection report](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-monitoring).

## Inspect website details

You can dive deeper by selecting the URL or domain of the website in the alert. This opens a page about that particular URL or domain with various information, including:

- Devices that attempted to access website
- Incidents and alerts related to the website
- How frequent the website was seen in events in your organization

  [![The domain or URL entity details page](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-website-details.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-website-details.png#lightbox)

For more information, see [About URL or domain entity pages](https://learn.microsoft.com/en-us/defender-endpoint/investigate-domain).

## Inspect the device

You can also check the device that attempted to access a blocked URL. Selecting the name of the device on the alert page opens a page with comprehensive information about the device.

For more information, see [About device entity pages](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines).

## Web browser and Windows notifications for end users

With web protection in Defender for Endpoint, your end users are prevented from visiting malicious or unwanted websites using Microsoft Edge or other browsers. Because blocking is done by [network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection) and not their web browser, users see a generic error from the web browser. They also see a notification from Windows.

[![The Microsoft Edge showing a 403 error, and the Windows notification](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-browser-blocking-page.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-browser-blocking-page.png#lightbox)

*Web threat blocked on Microsoft Edge*

[![The Chrome web browser showing a secure connection warning, and the Windows notification](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-chrome-browser-blocking-page.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-chrome-browser-blocking-page.png#lightbox) *Web threat blocked on Chrome*

## Related articles

- [Web protection overview](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-overview)
- [Web content filtering](https://learn.microsoft.com/en-us/defender-endpoint/web-content-filtering)
- [Web threat protection](https://learn.microsoft.com/en-us/defender-endpoint/web-threat-protection)
- [Monitor web security](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-monitoring)
