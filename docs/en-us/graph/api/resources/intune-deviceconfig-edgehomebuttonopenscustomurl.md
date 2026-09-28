<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-edgehomebuttonopenscustomurl?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# edgeHomeButtonOpensCustomURL resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Show the home button; clicking the home button loads a specific URL.

Inherits from [edgeHomeButtonConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-edgehomebuttonconfiguration?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| homeButtonCustomURL | String | The specific URL to load. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.edgeHomeButtonOpensCustomURL",
  "homeButtonCustomURL": "String"
}
```
