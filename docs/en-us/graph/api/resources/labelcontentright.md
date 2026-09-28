<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/labelcontentright?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# labelContentRight resource type

Namespace: microsoft.graph

Represents the rights associated with a specific piece of content.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cid | String | The content identifier. |
| format | String | The content format. |
| id | String | The identifier. |
| rights | [usageRights](https://learn.microsoft.com/en-us/graph/api/resources/usagerights?view=graph-rest-1.0) | A flags enum that enumerates a user's usage rights when content is protected with a sensitivity label. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| label | [microsoft.graph.security.sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-1.0) | The sensitivity label applied to the content. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.labelContentRight",
  "id": "String (identifier)",
  "cid": "String",
  "format": "String",
  "rights": "String"
}
```
