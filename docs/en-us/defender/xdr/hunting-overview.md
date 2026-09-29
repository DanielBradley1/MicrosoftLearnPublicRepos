<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/hunting-overview -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Hunting in the Microsoft Defender portal

Hunting for security threats is a highly customizable activity that's most effective throughout all stages of threat hunting: proactive, reactive, and post incident. The Defender portal provides hunting tools from Microsoft Defender XDR and Microsoft Sentinel for every stage. These tools are well suited for analysts who are just starting their careers and experienced threat hunters who use advanced hunting methods. Threat hunters of all levels benefit from features that let them share techniques, queries, and findings with their teams.

## Hunting tools

The foundation of hunting queries in the Defender portal rests on Kusto Query Language \(KQL\). KQL is a powerful and flexible language that's optimized for searching through big-data stores in cloud environments. However, crafting complex queries isn't the only way to hunt for threats. Here are some more hunting tools and resources within the Defender portal designed to bring hunting into your reach:

- [**Microsoft Security Copilot in advanced hunting**](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-security-copilot) provides prerelease capabilities that include the Threat Hunting Assistant for conversational hunting and the Query assistant for generating KQL from natural language.
- [**Guided mode**](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-builder) uses a query builder for crafting meaningful hunting queries without knowing KQL or the data schema.
- [**Get help as you write queries**](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language#get-help-as-you-write-queries) with features like autosuggest, schema tree, and sample queries.
- [**Content hub**](https://learn.microsoft.com/en-us/azure/sentinel/sentinel-solutions-deploy?tabs=defender-portal#hunting-query) provides expert queries to match out-of-the-box solutions in Microsoft Sentinel.
- [**Microsoft Defender Experts Hunting**](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-overview) is a separately sold managed threat hunting service that complements security operations teams that want assistance.

Maximize the full extent of your team's hunting prowess with the following hunting tools in the Defender portal:

| Hunting tool | Description |
| --- | --- |
| [**Advanced hunting**](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) | View and query data sources available from Defender portal services and share queries with your team. After you onboard a Microsoft Sentinel workspace, use its content, including queries and functions. |
| [**Microsoft Sentinel hunting**](https://learn.microsoft.com/en-us/azure/sentinel/hunting) | Hunt for security threats in your data sources. Use specialized search and query tools such as **hunts** and **bookmarks**. |
| [**Go hunt**](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-go-hunt) | Quickly pivot an investigation to entities found within an incident. |
| [**Hunts \(preview\)**](https://learn.microsoft.com/en-us/azure/sentinel/hunts) | An end-to-end, proactive threat hunting process with collaboration features. |
| [**Bookmarks**](https://learn.microsoft.com/en-us/azure/sentinel/bookmarks) | Preserve queries and their results, and add notes and contextual observations. In the Defender portal, you can view existing Microsoft Sentinel bookmarks but can't create them. Bookmarks aren't available in Advanced hunting. |
| [**Hunting with summary rules**](https://learn.microsoft.com/en-us/azure/sentinel/summary-rules#quickly-find-a-malicious-ip-address-in-your-network-traffic) | Use summary rules to save costs hunting for threats in verbose logs. |
| [**MITRE ATT&CK map \(preview\)**](https://learn.microsoft.com/en-us/azure/sentinel/mitre-coverage#use-the-mitre-attck-framework-in-analytics-rules-and-incidents) | When creating a new hunting query, select specific tactics and techniques to apply. |
| [**Restore historical data**](https://learn.microsoft.com/en-us/azure/sentinel/restore) | Restore data from archived logs to use in high-performance queries. |
| [**Search large data sets**](https://learn.microsoft.com/en-us/azure/sentinel/search-jobs?tabs=defender-portal) | Search for specific events in up to one year of data in a table using KQL. |
| [**Threat analytics**](https://learn.microsoft.com/en-us/defender-xdr/threat-analytics) | Track emerging threats and review Microsoft threat research and insights. |
| [**Threat explorer**](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-threat-hunting) | Hunt for specialized threats related to email. |

## Hunting stages

The following table describes how you can make the most of the Defender portal's hunting tools throughout all stages of threat hunting:

| Hunting stage | Hunting tools |
| --- | --- |
| **Proactive** - Find the weak areas in your environment before threat actors do. Detect suspicious activity extra early. | - Regularly conduct end-to-end [hunts \(preview\)](https://learn.microsoft.com/en-us/azure/sentinel/hunts) to proactively seek out undetected threats and malicious behaviors, validate hypotheses, and act on findings by creating new detections, incidents, or threat intelligence.  <br>  <br>- Use the [MITRE ATT&CK map \(preview\)](https://learn.microsoft.com/en-us/azure/sentinel/mitre-coverage#use-the-mitre-attck-framework-in-analytics-rules-and-incidents) to identify detection gaps, and then run predefined hunting queries for highlighted techniques.  <br>  <br>- Insert new threat intelligence into proven queries to tune detections and confirm if a compromise is in process.  <br>  <br>- Take proactive steps to build and test queries against data from new or updated sources.  <br>  <br>- Use [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) to find early-stage attacks or threats that don't have alerts. |
| **Reactive** - Use hunting tools during an active investigation. | - Quickly pivot on incidents with the [**Go hunt**](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-go-hunt) button to search broadly for suspicious entities found during an investigation.  <br>  <br>- Use [threat analytics](https://learn.microsoft.com/en-us/defender-xdr/threat-analytics) to investigate emerging threats and assess their potential impact.  <br>  <br>- Use the prerelease [Microsoft Security Copilot capabilities in advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-security-copilot) to investigate threats or generate queries. |
| **Post incident** - Improve coverage and insights to prevent similar incidents from recurring. | - Turn successful hunting queries into new [analytics and detection rules](https://learn.microsoft.com/en-us/azure/sentinel/threat-detection), or refine existing ones.  <br>  <br>- [Restore historical data](https://learn.microsoft.com/en-us/azure/sentinel/restore) and [search large datasets](https://learn.microsoft.com/en-us/azure/sentinel/search-jobs?tabs=defender-portal) for specialized hunting as part of full incident investigations. |

## Related content

- [Incidents and alerts in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview)
- [Microsoft Security Exposure Management](https://learn.microsoft.com/en-us/security-exposure-management/microsoft-security-exposure-management)
