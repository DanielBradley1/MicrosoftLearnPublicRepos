<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvmsoftwarevulnerabilities-table -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# DeviceTvmSoftwareVulnerabilities

Important

Some information relates to prereleased product, which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The `DeviceTvmSoftwareVulnerabilities` table in the advanced hunting schema contains the [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) list of vulnerabilities in installed software products. This table also includes operating system information, CVE IDs, and vulnerability severity information. You can use this table, for example, to hunt for events involving devices that have severe vulnerabilities in their software. Use this reference to construct queries that return information from the table.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

Note

The `DeviceTvmSoftwareInventory` and `DeviceTvmSoftwareVulnerabilities` tables have replaced the `DeviceTvmSoftwareInventoryVulnerabilities` table. Together, the first two tables include more columns you can use to help inform your vulnerability management activities or hunt for vulnerable devices.

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

Important

**This Defender Vulnerability Management \(TVM\) table isn't ingested into Microsoft Sentinel.** In Microsoft Sentinel, this table is exposed for schema visibility only \(for example, autocomplete and query validation\), not for data ingestion. As a result, Microsoft Sentinel can accept queries that reference this table, but those queries return no results.

To query this table’s data, run the query in Defender XDR Advanced Hunting, where the data is available. Using TVM table data directly in Microsoft Sentinel analytics and detections isn't currently supported unless you build a [custom ingestion path](https://learn.microsoft.com/en-us/azure/sentinel/create-custom-connector). For more information, see [Which Defender XDR tables aren't supported in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender#which-defender-xdr-tables-arent-supported-in-microsoft-sentinel).

| Column name | Data type | Description |
| --- | --- | --- |
| `DeviceId` | `string` | Unique identifier for the device in the service |
| `DeviceName` | `string` | Fully qualified domain name \(FQDN\) of the device |
| `OSPlatform` | `string` | Platform of the operating system running on the device. Indicates specific operating systems, including variations within the same family, such as Windows 11, Windows 10, and Windows 7. |
| `OSVersion` | `string` | Version of the operating system running on the device |
| `OSArchitecture` | `string` | Architecture of the operating system running on the device |
| `SoftwareVendor` | `string` | Name of the software publisher |
| `SoftwareName` | `string` | Name of the software product |
| `SoftwareVersion` | `string` | Version number of the software product |
| `CveId` | `string` | Unique identifier assigned to the security vulnerability under the Common Vulnerabilities and Exposures \(CVE\) system |
| `VulnerabilitySeverityLevel` | `string` | Severity level assigned to the security vulnerability based on the CVSS score and dynamic factors influenced by the threat landscape |
| `RecommendedSecurityUpdate` | `string` | Name or description of the security update provided by the software publisher to address the vulnerability |
| `RecommendedSecurityUpdateId` | `string` | Identifier of the applicable security updates or identifier for the corresponding guidance or knowledge base \(KB\) articles |
| `CveTags` | `dynamic` | Array of tags relevant to the CVE; example: ZeroDay, NoSecurityUpdate |

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
