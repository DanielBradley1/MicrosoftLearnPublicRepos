<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/baselineresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# baselineResource resource type

Namespace: microsoft.graph

Represents the information and properties of a [baselineResource](https://learn.microsoft.com/en-us/graph/api/resources/baselineresource?view=graph-rest-1.0) object. The baseline is a complex object that contains details of at least one resource and one property associated with the resource that the admin wants to monitor via the [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) object. The baseline resources are a collection of resources and their properties added to the baseline. At least one property of one resource must be included in the baseline.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Unique name of the resource. |
| properties | [openComplexDictionaryType](https://learn.microsoft.com/en-us/graph/api/resources/opencomplexdictionarytype?view=graph-rest-1.0) | Properties of a resource supported by Tenant Configuration Management. |
| resourceType | String | Name of the resource type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.baselineResource",
  "displayName": "String",
  "properties": {"@odata.type": "microsoft.graph.openComplexDictionaryType"},
  "resourceType": "String"
}
```
