<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/entity-page-ip -->
<!-- Sitemap-Last-Modified: 2026-06-23 -->

# IP address entity page in Microsoft Defender

The IP address entity page in the Microsoft Defender portal helps you examine possible communication between your devices and external internet protocol \(IP\) addresses.

Identifying all devices in the organization that communicated with a suspected or known malicious IP address, such as Command and Control \(C2\) servers, helps determine the potential scope of breach, associated files, and infected devices.

You can find information from the following sections in the IP address entity page:

- [Overview](#overview)
- [Incidents and alerts](#incidents-and-alerts)
- [Observed in organization](#observed-in-organization)
- [Threat Intelligence Insights](#threat-intelligence-insights)
- [Sentinel events](#sentinel-events)

Important

Microsoft Sentinel is generally available in the Microsoft Defender portal, with or without Microsoft Defender XDR or an E5 license. For more information, see [Microsoft Sentinel in the Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2263690).

After **March 31, 2027**, Microsoft Sentinel will no longer be supported in the Azure portal and will be available only in the Microsoft Defender portal.

If you're currently using Microsoft Sentinel in the Azure portal, we recommend that you start planning your transition to the Defender portal now to ensure a smooth transition and take full advantage of the [unified security operations experience offered by Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview). For more information, see [Transition your Microsoft Sentinel environment to the Defender portal](https://learn.microsoft.com/en-us/azure/sentinel/move-to-defender) and [Planning your move to Microsoft Defender portal for all Microsoft Sentinel customers](https://techcommunity.microsoft.com/blog/microsoft-security-blog/planning-your-move-to-microsoft-defender-portal-for-all-microsoft-sentinel-custo/4428613) \(blog\).

## Overview

In the left pane, the **Overview** page provides a summary of IP details \(if available\).

| Section | Details |
| --- | --- |
| Security info | <li>Open incidents</li><br><br><li>Active alerts</li> |
| IP details | <li>Organization (ISP)</li><br><br><li>ASN</li><br><br><li>Country/Region, State, City</li><br><br><li>Carrier</li><br><br><li>Latitude and longitude</li><br><br><li>Postal code</li> |

The left side also has a panel showing Log activity \(time first seen/last seen, data source\) collected from several log sources, and another panel showing a list of logged hosts collected from Azure Monitoring Agent heartbeat tables.

The main body of the **Overview** page contains dashboard cards showing a count of incidents and alerts \(grouped by severity\) containing the IP address, and a chart of the prevalence of the IP address in the organization over the indicated time period.

## Incidents and alerts

The **Incidents and alerts** page shows a list of incidents and alerts that include the IP address as part of their story. These incidents and alerts come from any of a number of Microsoft Defender detection sources, including, if onboarded, Microsoft Sentinel. This list is a filtered version of the [incidents queue](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview), and shows a short description of the incident or alert, its severity \(high, medium, low, informational\), its status in the queue \(new, in progress, resolved\), its classification \(not set, false alert, true alert\), investigation state, category, who is assigned to address it, and last activity observed.

You can customize which columns are displayed for each item. You can also filter the alerts by severity, status, or any other column in the display.

The *impacted assets* column refers to all the user, application, and other entities referenced in the incident or alert.

When an incident or alert is selected, a fly-out appears. From this panel you can manage the incident or alert and view more details such as incident/alert number and related devices. Multiple alerts can be selected at a time.

To see a full page view of an incident or alert, select its title.

## Observed in organization

The **Observed in organization** section provides a list of devices that have a connection with this IP and the last event details for each device \(the list is limited to 100 devices\).

## Threat Intelligence Insights

The **Threat Intelligence Insights** tab surfaces enrichment data from [Microsoft Threat Intelligence](https://learn.microsoft.com/en-us/defender-xdr/defender-threat-intelligence) directly on the IP address entity page. These enrichments provide globally observed intelligence to help you assess the risk of an IP address during an investigation.

For a general overview of entity enrichments, see [View threat intelligence in entity pages](https://learn.microsoft.com/en-us/defender-xdr/entity-page-threat-intelligence).

### Reputation

The reputation section displays a risk assessment for the IP address based on Microsoft's detection rules and intelligence. The reputation score indicates whether the IP address is known to be malicious, suspicious, or benign, helping analysts quickly prioritize their investigation.

### Attributed threat reports

When Microsoft has linked the IP address to a known threat actor or campaign, this section shows related threat analytics reports. These reports provide context about the threat actor's tactics, techniques, and procedures \(TTPs\).

### Infrastructure relationships

The infrastructure relationships section provides detailed data about the IP address, including:

| Data set | Description |
| --- | --- |
| **DNS records** | Historical and current DNS resolution data associated with the IP address. |
| **WHOIS information** | Registration details for the IP address, including registrant, dates, and registrar. |
| **Host pairs** | Relationships between hosts based on observed connections in web content. |
| **Subdomains** | Known subdomains that resolve to the IP address. |
| **TLS/SSL certificates** | Certificate details including issuer, validity, and subject alternative names. |
| **Services** | Detected network services running on the IP address. |
| **Components** | Web technologies and frameworks identified on the IP address. |
| **Trackers** | Web analytics and tracking codes observed on the IP address. |
| **Cookies** | Cookie names observed in responses from the IP address. |

## Sentinel events

If your organization onboarded Microsoft Sentinel to the Defender portal, this additional tab is on the IP address entity page. This tab imports the [IP entity page from Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/entity-pages).

### Sentinel timeline

This timeline shows alerts associated with the IP address entity. These alerts include those seen on the **Incidents and alerts** tab and those created by Microsoft Sentinel from third-party, non-Microsoft data sources.

This timeline also shows [bookmarked hunts](https://learn.microsoft.com/en-us/azure/sentinel/bookmarks) from other investigations that reference this IP entity, IP activity events from external data sources, and unusual behaviors detected by Microsoft Sentinel's [anomaly rules](https://learn.microsoft.com/en-us/azure/sentinel/soc-ml-anomalies).

### Insights

Entity insights are queries defined by Microsoft security researchers to help you investigate more efficiently and effectively. These insights automatically ask the big questions about your IP entity, providing valuable security information in the form of tabular data and charts. The insights include data from various IP threat intelligence sources, network traffic inspection, and more, and include advanced machine learning algorithms to detect anomalous behavior.

The following are some of the insights shown:

- Microsoft Defender Threat Intelligence reputation.
- Virus Total IP Address.
- Recorded Future IP Address.
- Anomali IP Address
- AbuseIPDB.
- Anomalies count by IP address.
- Network traffic inspection.
- IP address remote connections with TI match.
- IP address remote connections.
- This IP has a TI match.
- Watchlist insights \(Preview\).

The insights are based on the following data sources:

- Syslog \(Linux\)
- SecurityEvent \(Windows\)
- AuditLogs \(Microsoft Entra ID\)
- SigninLogs \(Microsoft Entra ID\)
- OfficeActivity \(Office 365\)
- BehaviorAnalytics \(Microsoft Sentinel UEBA\)
- Heartbeat \(Azure Monitor Agent\)
- CommonSecurityLog \(Microsoft Sentinel\)

If you want to further explore any of the insights in this panel, select the link accompanying the insight. The link takes you to the **Advanced hunting** page, where it displays the query underlying the insight, along with its raw results. You can modify the query or drill down into the results to expand your investigation or just satisfy your curiosity.

## Response actions

Response actions offer shortcuts to analyze, investigate, and defend against threats.

Response actions run along the top of a specific IP entity page and include:

| Action | Description |
| --- | --- |
| **Add indicator** | Opens a wizard for you to add this IP address as an Indicator of Compromise \(IoC\) to your Threat Intelligence knowledgebase. |
| **Open cloud app IP settings** | Opens the IP address ranges configuration screen for you to add the IP address to it. |
| **Investigate in Activity log** | Opens the Microsoft 365 Activity log screen for you to look for the IP address in other logs. |
| **Go hunt** | Opens the **Advanced hunting** page, with a built-in hunting query to find instances of this IP address. |

## Related content

- [Microsoft Defender overview](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)
- [Turn on Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable)
- [Device entity page in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/entity-page-device)
- [User entity page in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/investigate-users)
- [Microsoft Defender XDR integration with Microsoft Sentinel](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender-integration-with-azure-sentinel)
- [Connect Microsoft Sentinel to Microsoft Defender XDR](https://learn.microsoft.com/en-us/azure/sentinel/microsoft-sentinel-onboard)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bd-p/MicrosoftDefenderATP).
