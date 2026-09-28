<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-ipv4range?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# iPv4Range resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

IPv4 Range definition.

Inherits from [ipRange](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iprange?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lowerAddress | String | Lower address. |
| upperAddress | String | Upper address. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iPv4Range",
  "lowerAddress": "String",
  "upperAddress": "String"
}
```
