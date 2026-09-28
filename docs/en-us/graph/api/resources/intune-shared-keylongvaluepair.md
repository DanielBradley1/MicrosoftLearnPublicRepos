<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keylongvaluepair?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# keyLongValuePair resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Key long value pair

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name for this key long value pair |
| value | Int64 | Value for this key long value pair |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.keyLongValuePair",
  "name": "String",
  "value": 1024
}
```
