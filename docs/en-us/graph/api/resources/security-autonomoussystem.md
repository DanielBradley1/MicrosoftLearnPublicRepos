<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-autonomoussystem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# autonomousSystem resource type

Namespace: microsoft.graph.security

Note

The Microsoft Threat Intelligence APIs are available to all customers with a Microsoft Defender XDR or Microsoft Sentinel license. No separate license is required to access these APIs.

Represents data assigned in an autonomous system.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the autonomous system. |
| number | Int32 | The autonomous system number, assigned by IANA. |
| organization | String | The name of the autonomous system organization. |
| value | String | A displayable value for these autonomous system details. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.autonomousSystem",
  "name": "String",
  "number": "Int32",
  "organization": "String",
  "value": "String"
}
```
