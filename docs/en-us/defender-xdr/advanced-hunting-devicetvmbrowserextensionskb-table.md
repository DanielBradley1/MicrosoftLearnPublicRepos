<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvmbrowserextensionskb-table -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# DeviceTvmBrowserExtensionsKB \(Preview\)

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The `DeviceTvmBrowserExtensionsKB` table in the advanced hunting schema contains information about browser extension details and permission information used in [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) browser extensions page.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

Important

**This Defender Vulnerability Management \(TVM\) table isn't ingested into Microsoft Sentinel.** In Microsoft Sentinel, this table is exposed for schema visibility only \(for example, autocomplete and query validation\), not for data ingestion. As a result, Microsoft Sentinel can accept queries that reference this table, but those queries return no results.

To query this table’s data, run the query in Defender XDR Advanced Hunting, where the data is available. Using TVM table data directly in Microsoft Sentinel analytics and detections isn't currently supported unless you build a [custom ingestion path](https://learn.microsoft.com/en-us/azure/sentinel/create-custom-connector). For more information, see [Which Defender XDR tables aren't supported in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender#which-defender-xdr-tables-arent-supported-in-microsoft-sentinel).

| Column name | Data type | Description |
| --- | --- | --- |
| `BrowserName` | `string` | Name of the web browser with the extension |
| `ExtensionId` | `string` | Unique identifier for the browser extension |
| `ExtensionName` | `string` | Name of the extension |
| `ExtensionDescription` | `string` | Description from the publisher about the extension |
| `ExtensionVersion` | `dynamic` | Version number of the extension |
| `ExtensionRisk` | `string` | Risk level for the extension based on the permissions it has requested |
| `PermissionId` | `string` | Unique identifier for the permission |
| `PermissionName` | `string` | Name given to each permission based on what the extension is asking for |
| `PermissionDescription` | `string` | Explanation of what the permission is supposed to do |
| `PermissionRisk` | `string` | Risk level for the permission based on the type of access it would allow |
| `IsPermissionRequired` | `string` | Whether the permission is required for the extension to run, or optional |

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
