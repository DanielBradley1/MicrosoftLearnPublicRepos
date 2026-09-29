<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvmsecureconfigurationassessmentkb-table -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# DeviceTvmSecureConfigurationAssessmentKB

The `DeviceTvmSecureConfigurationAssessmentKB` table in the advanced hunting schema contains information about the various secure configurations checked by [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). It also includes risk information, related industry benchmarks, and applicable MITRE ATT&CK techniques and tactics.

This table doesn't return events or records. We recommend joining this table to the [DeviceTvmSecureConfigurationAssessment](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvmsecureconfigurationassessment-table) table using `ConfigurationId` to view text information about the security configurations in the returned assessments.

For example, when you query the `DeviceTvmSecureConfigurationAssessment` table you might want to view the `ConfigurationDescription` for the security configurations that come up in the assessment results. You can see this information by joining this table to `DeviceTvmSecureConfigurationAssessment` using `ConfigurationId` and project `ConfigurationDescription`.

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

Important

**This Defender Vulnerability Management \(TVM\) table isn't ingested into Microsoft Sentinel.** In Microsoft Sentinel, this table is exposed for schema visibility only \(for example, autocomplete and query validation\), not for data ingestion. As a result, Microsoft Sentinel can accept queries that reference this table, but those queries return no results.

To query this table’s data, run the query in Defender XDR Advanced Hunting, where the data is available. Using TVM table data directly in Microsoft Sentinel analytics and detections isn't currently supported unless you build a [custom ingestion path](https://learn.microsoft.com/en-us/azure/sentinel/create-custom-connector). For more information, see [Which Defender XDR tables aren't supported in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender#which-defender-xdr-tables-arent-supported-in-microsoft-sentinel).

| Column name | Data type | Description |
| --- | --- | --- |
| `ConfigurationId` | `string` | Unique identifier for a specific configuration |
| `ConfigurationImpact` | `real` | Rated impact of the configuration to the overall configuration score \(1-10\) |
| `ConfigurationName` | `string` | Display name of the configuration |
| `ConfigurationDescription` | `string` | Description of the configuration |
| `RiskDescription` | `string` | Description of the associated risk |
| `ConfigurationCategory` | `string` | Category or grouping to which the configuration belongs: Application, OS, Network, Accounts, Security controls |
| `ConfigurationSubcategory` | `string` | Subcategory or subgrouping to which the configuration belongs. In many cases, this describes specific capabilities or features. |
| `ConfigurationBenchmarks` | `dynamic` | List of industry benchmarks recommending the same or similar configuration |
| `Tags` | `dynamic` | Labels representing various attributes used to identify or categorize a security configuration |
| `RemediationOptions` | `string` | Recommended actions to reduce or address any associated risks |

You can try this example query to return relevant configuration metadata along with information on devices with non-compliant antivirus configurations from the `DeviceTvmSecureConfigurationAssessment` table:

```kusto
// Get information on devices with antivirus configurations issues
DeviceTvmSecureConfigurationAssessment
| where ConfigurationSubcategory == 'Antivirus' and IsApplicable == 1 and IsCompliant == 0
| join kind=leftouter (
    DeviceTvmSecureConfigurationAssessmentKB
    | project ConfigurationId, ConfigurationName, ConfigurationDescription, RiskDescription, Tags, ConfigurationImpact
) on ConfigurationId
| project DeviceName, OSPlatform, ConfigurationId, ConfigurationName, ConfigurationCategory, ConfigurationSubcategory, ConfigurationDescription, RiskDescription, ConfigurationImpact, Tags
```

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
