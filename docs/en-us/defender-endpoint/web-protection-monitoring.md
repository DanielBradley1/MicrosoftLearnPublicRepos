<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/web-protection-monitoring -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Monitor web browsing security in Microsoft Defender for Endpoint

Web protection lets you monitor your organization's web browsing security through reports under **Reports > Web protection** in the Microsoft Defender portal. The report contains cards that provide web threat detection statistics.

- **Web threat protection detections over time** - this trending card displays the number of web threats detected by type during the selected time period \(Last 30 days, Last 3 months, Last 6 months\)

  [![The card showing web threats protection detections over time](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-blocks-over-time.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-blocks-over-time.png#lightbox)
- **Web threat protection summary** - this card displays the total web threat detections in the past 30 days, showing distribution across the different types of web threats. Selecting a slice opens the list of the domains that were found with malicious or unwanted websites.

  [![The card showing web threats protection summary](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-summary.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/wtp-summary.png#lightbox)

Note

It can take up to 12 hours before a block is reflected in the cards or the domain list.

## Types of web threats

Web protection categorizes malicious and unwanted websites as:

- **Phishing** - websites that contain spoofed web forms and other phishing mechanisms designed to trick users into divulging credentials and other sensitive information
- **Malicious** - websites that host malware and exploit code
- **Custom indicator** - websites whose URLs or domains you've added to your [custom indicator list](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview) for blocking

## View the domain list

Select a specific web threat category in the **Web threat protection summary** card to open the **Domains** page. The **Domains** page displays the list of the domains under that threat category. The **Domains** page provides the following information for each domain:

- **Access count** - number of requests for URLs in the domain
- **Blocks** - number of times requests were blocked
- **Access trend** - change in number of access attempts
- **Threat category** - type of web threat
- **Devices** - number of devices with access attempts

Select a domain to view the list of devices that have attempted to access URLs in that domain and the list of URLs.

## Related content

- [Web protection overview](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-overview)
- [Web content filtering](https://learn.microsoft.com/en-us/defender-endpoint/web-content-filtering)
- [Web threat protection](https://learn.microsoft.com/en-us/defender-endpoint/web-threat-protection)
- [Respond to web threats](https://learn.microsoft.com/en-us/defender-endpoint/web-protection-response)
