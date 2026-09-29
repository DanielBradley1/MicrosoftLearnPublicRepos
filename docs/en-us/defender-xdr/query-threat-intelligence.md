<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/query-threat-intelligence -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Query threat intelligence in Microsoft Defender

Use the `ThreatIntelEntities` table in advanced hunting to query Microsoft's built-in threat intelligence, including known indicators of compromise \(IOCs\), threat actors, and malicious infrastructure. Correlate this intelligence with activity in your environment to support threat hunting, custom detections, and response.

## Query threat intelligence in advanced hunting

Built-in threat intelligence is available in the `ThreatIntelEntities` table.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Select **Advanced hunting**.
3. Select **Schema**.
4. Expand the **Threat intelligence** group.
5. Select the `ThreatIntelEntities` table.

## ThreatIntelEntities table columns

The `ThreatIntelEntities` table includes the following columns:

| Column | Type | Description |
| --- | --- | --- |
| `TenantId` | string | The Log Analytics workspace ID. |
| `Id` | string | A value that uniquely identifies the indicator STIX object. |
| `SourceSystem` | string | The source system that collected the entity. |
| `LastUpdateMethod` | string | The component that last updated the entity. |
| `AdditionalFields` | dynamic | Type-specific fields associated with the entity. |
| `Data` | dynamic | All object properties, formatted according to the [STIX 2.1 specification](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html). |
| `IsActive` | bool | Indicates whether the indicator is active and valid for detections. |
| `Revoked` | bool | Indicates whether the indicator was revoked. |
| `ValidUntil` | datetime | The time at which the indicator is no longer considered valid for the behaviors it represents. |
| `ValidFrom` | datetime | The time from which the indicator is considered valid for the behaviors it represents. |
| `Created` | datetime | The date and time when the indicator was created. |
| `Modified` | datetime | The date and time when the indicator was last modified. |
| `Tags` | string | Tags associated with the indicator. |
| `Confidence` | int | The creator's confidence in the correctness of the data. The value must be from 0 through 100. |
| `Pattern` | string | The detection pattern for the indicator, which might be expressed as a STIX pattern. |
| `ObservableKey` | string | The entire left-hand side of an equality comparison in the pattern. |
| `ObservableValue` | string | The entire right-hand side of an equality comparison in the pattern. |
| `Type` | string | The name of the table. |

## Expand threat intelligence coverage

Use Microsoft Sentinel to integrate external threat intelligence feeds with your Microsoft Defender data.

For more information, see [Threat intelligence in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/understand-threat-intelligence).
