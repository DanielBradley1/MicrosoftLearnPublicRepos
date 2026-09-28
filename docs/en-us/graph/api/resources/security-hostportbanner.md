<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hostportbanner?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# hostPortBanner resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents a banner retrieved from scanning a port on a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| banner | String | The text response received from a web component when scanning a **hostPort**. |
| firstSeenDateTime | DateTimeOffset | The first date and time when Microsoft Defender Threat Intelligence observed the **hostPortBanner**. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. |
| lastSeenDateTime | DateTimeOffset | The last date and time when Microsoft Defender Threat Intelligence observed the **hostPortBanner**. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. |
| scanProtocol | String | The specific protocol used to scan the **hostPort**. |
| timesObserved | Int32 | The total amount of times that Microsoft Defender Threat Intelligence has observed the **hostPortBanner** in all its scans. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hostPortBanner",
  "banner": "String",
  "firstSeenDateTime": "String (timestamp)",
  "lastSeenDateTime": "String (timestamp)",
  "scanProtocol": "String",
  "timesObserved": "Int32"
}
```
