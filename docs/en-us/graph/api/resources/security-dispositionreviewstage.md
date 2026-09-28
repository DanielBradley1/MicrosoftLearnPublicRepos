<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-dispositionreviewstage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# dispositionReviewStage resource type

Namespace: microsoft.graph.security

Represents a multi-level review process where the reviewers indicate at each stage of the disposition whether to delete or further retain the content item. For details, see [Disposition of content](https://learn.microsoft.com/en-us/microsoft-365/compliance/disposition).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-retentionlabel?view=graph-rest-1.0) | [microsoft.graph.security.retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) | Create a new [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-retentionlabel-update?view=graph-rest-1.0) | [microsoft.graph.security.retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) | Update the [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique ID for each stage. |
| name | String | Name representing each stage within a collection. |
| reviewersEmailAddresses | String collection | A collection of reviewers at each stage. |
| stageNumber | String | The unique sequence number for each stage of the disposition review. |

## Relationships

None.

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.dispositionReviewStage",
  "id": "String (identifier)",
  "stageNumber": "String",
  "name": "String",
  "reviewersEmailAddresses": [
    "String"
  ]
}
```
