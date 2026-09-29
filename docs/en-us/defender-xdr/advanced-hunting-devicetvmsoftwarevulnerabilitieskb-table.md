<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# DeviceTvmSoftwareVulnerabilitiesKB

The `DeviceTvmSoftwareVulnerabilitiesKB` table in the advanced hunting schema contains the list of vulnerabilities [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) assesses devices for. Use this reference to construct queries that return information from the table.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

Important

**This Defender Vulnerability Management \(TVM\) table isn't ingested into Microsoft Sentinel.** In Microsoft Sentinel, this table is exposed for schema visibility only \(for example, autocomplete and query validation\), not for data ingestion. As a result, Microsoft Sentinel can accept queries that reference this table, but those queries return no results.

To query this table’s data, run the query in Defender XDR Advanced Hunting, where the data is available. Using TVM table data directly in Microsoft Sentinel analytics and detections isn't currently supported unless you build a [custom ingestion path](https://learn.microsoft.com/en-us/azure/sentinel/create-custom-connector). For more information, see [Which Defender XDR tables aren't supported in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender#which-defender-xdr-tables-arent-supported-in-microsoft-sentinel).

| Column name | Data type | Description |
| --- | --- | --- |
| `CveId` | `string` | Unique identifier assigned to the security vulnerability under the Common Vulnerabilities and Exposures \(CVE\) system |
| `CvssScore` | `string` | Severity score assigned to the security vulnerability under the Common Vulnerability Scoring System \(CVSS\) |
| `IsExploitAvailable` | `boolean` | Indicates whether exploit code for the vulnerability is publicly available |
| `VulnerabilitySeverityLevel` | `string` | Severity level assigned to the security vulnerability based on the CVSS score and dynamic factors influenced by the threat landscape |
| `LastModifiedTime` | `datetime` | Date and time the item or related metadata was last modified |
| `PublishedDate` | `datetime` | Date vulnerability was disclosed to the public |
| `VulnerabilityDescription` | `string` | Description of the vulnerability and associated risks |
| `AffectedSoftware` | `dynamic` | List of all software products affected by the vulnerability |

## Related topics

- [Proactively hunt for threats](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Overview of Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
