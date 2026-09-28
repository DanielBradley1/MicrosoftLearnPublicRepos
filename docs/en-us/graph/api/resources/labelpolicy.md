<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/labelpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-16 -->

# labelPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a reference to a sensitivity label policy that includes a specific sensitivity label.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the label policy. |
| name | String | The display name of the label policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.labelPolicy",
  "id": "String",
  "name": "String"
}
```
