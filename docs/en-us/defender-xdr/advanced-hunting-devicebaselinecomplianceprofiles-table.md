<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicebaselinecomplianceprofiles-table -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# DeviceBaselineComplianceProfiles \(Preview\)

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The `DeviceBaselineComplianceProfiles` table in the advanced hunting schema contains baseline profiles used for monitoring device baseline compliance. Use this reference to construct queries that return information from the table.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `ProfileId` | `string` | Unique identifier for the profile |
| `ProfileName` | `string` | Display name of the profile |
| `ProfileDescription` | `string` | Optional description providing additional information related to the profile |
| `OSPlatform` | `dynamic` | Platform of the operating system running on the device. This indicates specific operating systems, including variations within the same family, such as Windows 11, Windows 10 and Windows 7. |
| `OSVersion` | `string` | Version of the operating system running on the device |
| `BaseBenchmark` | `string` | Industry benchmark on top of which the profile was created |
| `BenchmarkVersion` | `string` | Version of the industry benchmark on top of which the profile was created |
| `BenchmarkProfileLevel` | `string` | Benchmark compliance level set for the profile |
| `Status` | `boolean` | Indicator of the profile status - can be Enabled or Disabled |
| `CreatedBy` | `string` | Identity of the user account who created the profile |
| `CreatedOn` | `datetime` | Date and time when the profile was created |
| `LastUpdatedBy` | `string` | Identity of the user account who last updated the profile |
| `LastUpdatedOn` | `datetime` | Date and time when the profile was last updated |

## Related topics

- [Proactively hunt for threats](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Overview Defender Vulnerability Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
