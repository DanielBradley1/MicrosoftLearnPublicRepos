<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicebaselinecomplianceassessmentkb-table -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# DeviceBaselineComplianceAssessmentKB \(Preview\)

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The `DeviceBaselineComplianceAssessmentKB` table in the advanced hunting schema contains information about various security configurations used by baseline compliance to assess devices.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `ConfigurationId` | `string` | Identifier for a configuration within a specific benchmark and benchmark version |
| `ConfigurationName` | `string` | Display name of the configuration |
| `ConfigurationDescription` | `string` | Description of the configuration |
| `ConfigurationRationale` | `string` | Description of any associated risks and rationale behind the configuration |
| `ConfigurationCategory` | `string` | Category or grouping to which the configuration belongs |
| `BenchmarkProfileLevels` | `dynamic` | List of benchmark compliance levels for which the configuration is applicable |
| `CCEReference` | `string` | Unique Common Configuration Enumeration \(CCE\) identifier for the configuration |
| `RemediationOptions` | `string` | Recommended actions to reduce or address any associated risks |
| `ConfigurationBenchmark` | `string` | Industry benchmark recommending the configuration |
| `ConfigurationBenchmarkVersion` | `string` | Version of the industry benchmark recommending the configuration |
| `Source` | `dynamic` | The registry path or other location used to determine the current device setting |
| `RecommendedValue` | `dynamic` | Set of expected values for the current device setting to be compliant |

## Related topics

- [DeviceBaselineComplianceAssessment](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicebaselinecomplianceassessment-table)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Overview of Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
