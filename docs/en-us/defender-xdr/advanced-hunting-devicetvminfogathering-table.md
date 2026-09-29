<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvminfogathering-table -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# DeviceTvmInfoGathering

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The `DeviceTvmInfoGathering` table in the advanced hunting schema contains [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management) assessment events including the status of various configurations and attack surface area states of devices. You can use this table to hunt for assessment events related to mitigation for zero-days, posture assessment for emerging threats supporting threat analytics mitigation status reports, enabled TLS protocol versions on servers, and more. Use this reference to construct queries that return information from the table.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

Important

**This Defender Vulnerability Management \(TVM\) table isn't ingested into Microsoft Sentinel.** In Microsoft Sentinel, this table is exposed for schema visibility only \(for example, autocomplete and query validation\), not for data ingestion. As a result, Microsoft Sentinel can accept queries that reference this table, but those queries return no results.

To query this table’s data, run the query in Defender XDR Advanced Hunting, where the data is available. Using TVM table data directly in Microsoft Sentinel analytics and detections isn't currently supported unless you build a [custom ingestion path](https://learn.microsoft.com/en-us/azure/sentinel/create-custom-connector). For more information, see [Which Defender XDR tables aren't supported in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender#which-defender-xdr-tables-arent-supported-in-microsoft-sentinel).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the record was generated |
| `LastSeenTime` | `datetime` | Date and time when the service last saw the device |
| `DeviceId` | `string` | Unique identifier for the device in the service |
| `DeviceName` | `string` | Fully qualified domain name \(FQDN\) of the device |
| `OSPlatform` | `string` | Platform of the operating system running on the device. This indicates specific operating systems, including variations within the same family, such as Windows 10 and Windows 7. |
| `AdditionalFields` | `dynamic` | Additional information about the entity or event |

For example, to view devices affected by the [Log4Shell vulnerability](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/) where the workaround mitigation hasn't been applied yet, or has been applied and is pending reboot, you can use the following query.

```kusto
DeviceTvmInfoGathering
| where AdditionalFields.Log4JEnvironmentVariableMitigation in ("RebootRequired", "false")
| join kind=inner (
    DeviceTvmSoftwareVulnerabilities
    | where CveId == "CVE-2021-44228"
) on DeviceId
| summarize any(DeviceName), any(AdditionalFields.Log4JEnvironmentVariableMitigation) by DeviceId
```

## Related topics

- [DeviceTvmInfoGatheringKB](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvminfogatheringkb-table)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Overview of Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [Learn how to manage the Log4Shell vulnerability in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-manage-Log4shell-guidance)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
