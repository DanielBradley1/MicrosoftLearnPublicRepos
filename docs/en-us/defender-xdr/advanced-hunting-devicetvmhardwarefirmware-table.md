<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvmhardwarefirmware-table -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# DeviceTvmHardwareFirmware

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The `DeviceTvmHardwareFirmware` table in the advanced hunting schema contains hardware and firmware information of devices as checked by [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). The information includes the system model, processor, and BIOS, among others.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

Important

**This Defender Vulnerability Management \(TVM\) table isn't ingested into Microsoft Sentinel.** In Microsoft Sentinel, this table is exposed for schema visibility only \(for example, autocomplete and query validation\), not for data ingestion. As a result, Microsoft Sentinel can accept queries that reference this table, but those queries return no results.

To query this table’s data, run the query in Defender XDR Advanced Hunting, where the data is available. Using TVM table data directly in Microsoft Sentinel analytics and detections isn't currently supported unless you build a [custom ingestion path](https://learn.microsoft.com/en-us/azure/sentinel/create-custom-connector). For more information, see [Which Defender XDR tables aren't supported in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender#which-defender-xdr-tables-arent-supported-in-microsoft-sentinel).

| Column name | Data type | Description |
| --- | --- | --- |
| `DeviceId` | `string` | Unique identifier for the device in the service |
| `DeviceName` | `string` | Fully qualified domain name \(FQDN\) of the device |
| `ComponentType` | `string` | Type of hardware or firmware component |
| `Manufacturer` | `string` | Manufacturer of hardware or firmware component |
| `ComponentName` | `string` | Name of hardware or firmware component |
| `ComponentFamily` | `string` | Component family or class, a grouping of components that have similar features or characteristics as determined by the manufacturer |
| `ComponentVersion` | `string` | Component version \(for example, BIOS version\) |
| `AdditionalFields` | `dynamic` | Additional information about the components in JSON array format |

You can try the following sample queries to use the information available in the `DeviceTvmHardwareFirmware` table:

```kusto
// Count the number of Lenovo devices
DeviceTvmHardwareFirmware
| where ComponentType == "Hardware" and Manufacturer == "lenovo"
| summarize count()
```

```kusto
// Find all devices with a specific BIOS version, replace ComponentVersion with what you are looking for
DeviceTvmHardwareFirmware
| where ComponentType == "Bios" and ComponentVersion contains "N2VET29W"
|project DeviceId, DeviceName
```

## Related topics

- [Proactively hunt for threats](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Overview of Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
