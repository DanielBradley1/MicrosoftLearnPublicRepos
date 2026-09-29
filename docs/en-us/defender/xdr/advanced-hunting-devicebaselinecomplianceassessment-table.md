<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicebaselinecomplianceassessment-table -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# DeviceBaselineComplianceAssessment \(Preview\)

**Applies to:**

- Microsoft Defender
- Microsoft Defender for Endpoint

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The `DeviceBaselineComplianceAssessment` table in the advanced hunting schema contains baseline compliance assessment snapshot, which indicates the status of various security configurations related to baseline profiles on devices.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `DeviceId` | `string` | Unique identifier for the device in the service |
| `DeviceName` | `string` | Fully qualified domain name \(FQDN\) of the device |
| `OSPlatform` | `string` | Platform of the operating system running on the device. This indicates specific operating systems, including variations within the same family, such as Windows 11, Windows 10 and Windows 7. |
| `OSVersion` | `string` | Version of the operating system running on the device |
| `ConfigurationId` | `string` | Identifier for a configuration within a specific benchmark and benchmark version |
| `ProfileId` | `string` | Unique identifier for the profile |
| `IsCompliant` | `nullable bool` | Indicates whether the device that initiated the event is compliant or not |
| `IsApplicable` | `boolean` | Indicates whether the configuration or policy is applicable |
| `Source` | `dynamic` | The registry path or other location used to determine the current device setting |
| `RecommendedValue` | `dynamic` | Set of expected values for the current device setting to be compliant |
| `CurrentValue` | `dynamic` | Set of detected values found on the device |
| `IsExempt` | `boolean` | Indicates whether the device is exempt from having the baseline configuration |

## Related topics

- [Proactively hunt for threats](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Overview of Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
