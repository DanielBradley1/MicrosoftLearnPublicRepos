<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sensitivitylabelinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# sensitivityLabelInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the sensitivity label applied to a search result. This complex type is returned in the **sensitivityLabel** property of the [searchHit](https://learn.microsoft.com/en-us/graph/api/resources/searchhit?view=graph-rest-beta) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| color | String | The color that the UI should display for the label, if configured. |
| displayName | String | The display name of the sensitivity label. |
| priority | Int32 | The display priority of the sensitivity label. |
| sensitivityLabelId | String | The identifier of the sensitivity label. |
| tooltip | String | The tooltip that the UI should display for the sensitivity label. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sensitivityLabelInfo",
  "sensitivityLabelId": "String",
  "displayName": "String",
  "tooltip": "String",
  "priority": "Int32",
  "color": "String"
}
```
