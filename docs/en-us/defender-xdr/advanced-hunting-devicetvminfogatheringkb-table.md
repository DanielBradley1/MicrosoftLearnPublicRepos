<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvminfogatheringkb-table -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# DeviceTvmInfoGatheringKB

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The `DeviceTvmInfoGatheringKB` table in the advanced hunting schema contains metadata for [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management) assessment events data collected in the `DeviceTvmInfoGathering` table. The `DeviceTvmInfoGatheringKB` table contains the list of various configuration and attack surface area assessments used by Defender Vulnerability Management information gathering to assess devices. Use this reference to construct queries that return information from the table.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

Important

**This Defender Vulnerability Management \(TVM\) table isn't ingested into Microsoft Sentinel.** In Microsoft Sentinel, this table is exposed for schema visibility only \(for example, autocomplete and query validation\), not for data ingestion. As a result, Microsoft Sentinel can accept queries that reference this table, but those queries return no results.

To query this table’s data, run the query in Defender XDR Advanced Hunting, where the data is available. Using TVM table data directly in Microsoft Sentinel analytics and detections isn't currently supported unless you build a [custom ingestion path](https://learn.microsoft.com/en-us/azure/sentinel/create-custom-connector). For more information, see [Which Defender XDR tables aren't supported in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender#which-defender-xdr-tables-arent-supported-in-microsoft-sentinel).

| Column name | Data type | Description |
| --- | --- | --- |
| `IgId` | `string` | Unique identifier for the piece of information gathered |
| `FieldName` | `string` | Name of the field where this information appears in the AdditionalFields column of the DeviceTvmInfoGathering table |
| `Description` | `string` | Description of the information gathered |
| `Categories` | `dynamic` | List of categories that the information belongs to, in JSON array format |
| `DataStructure` | `string` | The data structure of the information gathered |

You can use this table to explore the kinds of information available in `DeviceTvmInfoGathering` so you can later fine-tune your hunting query.

For instance, to see the list of information being collected, you can try the following query:

```kusto
// Check out what is being collected 
DeviceTvmInfoGatheringKB  
```

From the results, say you become interested in the available categories, you can use the following query:

```kusto
// Return all available categories 
DeviceTvmInfoGatheringKB 
| mv-expand Categories to typeof(string) 
| distinct Categories 
```

Then, let's say you want to see the assessment categories involving the TLS protocol:

```kusto
// Return all findings for a specified category 
DeviceTvmInfoGatheringKB 
| where Categories contains "tls" 
```

Using the resulting fields, you can then use the `DeviceTvmInfoGathering` table to get a list of devices using TLS client version 1.0.

```kusto
// Return all devices on which the TLS version 1.0 is enabled 
DeviceTvmInfoGathering 
| where AdditionalFields.TlsClient10 == "Enabled" or AdditionalFields.TlsServer10 == "Enabled" 
```

## Related topics

- [DeviceTvmInfoGathering](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvminfogathering-table)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Overview Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
