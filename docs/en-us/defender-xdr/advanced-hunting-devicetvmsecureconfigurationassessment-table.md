<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvmsecureconfigurationassessment-table -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# DeviceTvmSecureConfigurationAssessment

Each row in the `DeviceTvmSecureConfigurationAssessment` table contains an assessment event for a specific security configuration from [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Use this reference to check the latest assessment results and determine whether devices are compliant.

You can join this table with the [DeviceTvmSecureConfigurationAssessmentKB](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicetvmsecureconfigurationassessmentkb-table) table using `ConfigurationId` so you can, for example, view the text description of the configuration from the `ConfigurationDescription` column of the `DeviceTvmSecureConfigurationAssessmentKB` table, in the configuration assessment results.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

Important

**This Defender Vulnerability Management \(TVM\) table isn't ingested into Microsoft Sentinel.** In Microsoft Sentinel, this table is exposed for schema visibility only \(for example, autocomplete and query validation\), not for data ingestion. As a result, Microsoft Sentinel can accept queries that reference this table, but those queries return no results.

To query this table’s data, run the query in Defender XDR Advanced Hunting, where the data is available. Using TVM table data directly in Microsoft Sentinel analytics and detections isn't currently supported unless you build a [custom ingestion path](https://learn.microsoft.com/en-us/azure/sentinel/create-custom-connector). For more information, see [Which Defender XDR tables aren't supported in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender#which-defender-xdr-tables-arent-supported-in-microsoft-sentinel).

| Column name | Data type | Description |
| --- | --- | --- |
| `DeviceId` | `string` | Unique identifier for the device in the service |
| `DeviceName` | `string` | Fully qualified domain name \(FQDN\) of the device |
| `OSPlatform` | `string` | Platform of the operating system running on the device. Indicates specific operating systems, including variations within the same family, such as Windows 11, Windows 10, and Windows 7. |
| `Timestamp` | `datetime` | Date and time when the record was generated |
| `ConfigurationId` | `string` | Unique identifier for a specific configuration |
| `ConfigurationCategory` | `string` | Category or grouping to which the configuration belongs: Application, OS, Network, Accounts, Security controls |
| `ConfigurationSubcategory` | `string` | Subcategory or subgrouping to which the configuration belongs. In many cases, string describes specific capabilities or features. |
| `ConfigurationImpact` | `real` | Rated impact of the configuration to the overall configuration score \(1-10\) |
| `IsCompliant` | `boolean` | Indicates whether the configuration or policy is properly configured  <br>\* A value of True is Compliant  <br>\* A value of False is Not Compliant |
| `IsApplicable` | `boolean` | Indicates whether the configuration or policy applies to the device  <br>\* A value of True is Applicable  <br>\* A value of False is Not Applicable |
| `Context` | `dynamic` | Additional contextual information about the configuration or policy |
| `IsExpectedUserImpact` | `boolean` | Indicates whether there will be user impact if the configuration or policy is applied |

You can try this example query to return information on devices with non-compliant antivirus configurations along with the relevant configuration metadata from the `DeviceTvmSecureConfigurationAssessmentKB` table:

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
