<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# configurationBaseline resource type

Namespace: microsoft.graph

Represents a baseline that contains details of at least one resource and one property associated with the resource that the admin wants to monitor via the [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) object.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/configurationbaseline-get?view=graph-rest-1.0) | [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) | Read the properties and relationships of a [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) object that is attached to a specific monitor. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | User-friendly description of the baseline given by the user. |
| displayName | String | User-friendly name given by the user to the baseline. |
| id | String | The unique identifier for the **configurationBaseline** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| parameters | [baselineParameter](https://learn.microsoft.com/en-us/graph/api/resources/baselineparameter?view=graph-rest-1.0) collection | Collection of parameters attached to the baseline. |
| resources | [baselineResource](https://learn.microsoft.com/en-us/graph/api/resources/baselineresource?view=graph-rest-1.0) collection | Collection of resources and their properties that are added to the baseline. At least one property of one resource must be present in the baseline. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.configurationBaseline",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "parameters": [{"@odata.type": "microsoft.graph.baselineParameter"}],
  "resources": [{"@odata.type": "microsoft.graph.baselineResource"}]
}
```
