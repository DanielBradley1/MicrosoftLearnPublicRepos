<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvmsoftwareevidencebeta-table -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# DeviceTvmSoftwareEvidenceBeta

Important

The `DeviceTvmSoftwareEvidenceBeta` table is currently in beta. Once it leaves beta, the final table name changes and column names might also change. The modifications are likely to break queries that are still using previous names. Users are advised to review and adjust their queries when this table is finalized.

The `DeviceTvmSoftwareEvidenceBeta` table in the advanced hunting schema contains data from [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) related to the [software evidence section](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-software-inventory#software-evidence). This table allows you to view evidence of where a specific software was detected on a device. You can use this table, for example, to identify the file paths of specific software. Use this reference to construct queries that return information from the table.

Microsoft Defender for Endpoint data populates this advanced hunting table. If your organization didn't deploy the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

Important

**This Defender Vulnerability Management \(TVM\) table isn't ingested into Microsoft Sentinel.** In Microsoft Sentinel, this table is exposed for schema visibility only \(for example, autocomplete and query validation\), not for data ingestion. As a result, Microsoft Sentinel can accept queries that reference this table, but those queries return no results.

To query this table’s data, run the query in Defender XDR Advanced Hunting, where the data is available. Using TVM table data directly in Microsoft Sentinel analytics and detections isn't currently supported unless you build a [custom ingestion path](https://learn.microsoft.com/en-us/azure/sentinel/create-custom-connector). For more information, see [Which Defender XDR tables aren't supported in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender#which-defender-xdr-tables-arent-supported-in-microsoft-sentinel).

| Column name | Data type | Description |
| --- | --- | --- |
| `DeviceId` | `string` | Unique identifier for the device in the service |
| `SoftwareVendor` | `string` | Name of the software publisher |
| `SoftwareName` | `string` | Name of the software product |
| `SoftwareVersion` | `string` | Version number of the software product |
| `RegistryPaths` | `dynamic` | Registry paths where evidence indicating the existence of the software on a device was detected |
| `DiskPaths` | `dynamic` | Disk paths where file-level evidence indicating the existence of the software on a device was detected |
| `LastSeenTime` | `string` | Date and time when the device was last seen by this service |

## Read more

- [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [Proactively hunt for threats](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
