<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/protectedcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# protectedContent resource type

Namespace: microsoft.graph

Represents the content that is protected by a sensitivity label.

This entity provides the details of the content that is being evaluated for rights and inheritance.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cid | String | The content id |
| format | String | The content format. |
| labelId | String | The unique identifier for the sensitivity label applied to the content. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.protectedContent",
  "labelId": "String",
  "cid": "String",
  "format": "String"
}
```
