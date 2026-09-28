<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-keyvaluepair?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# keyValuePair resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Key value pair for storing custom settings

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name for this key-value pair |
| value | String | Value for this key-value pair |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.keyValuePair",
  "name": "String",
  "value": "String"
}
```
