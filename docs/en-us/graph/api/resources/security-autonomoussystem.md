<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-autonomoussystem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# autonomousSystem resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

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
