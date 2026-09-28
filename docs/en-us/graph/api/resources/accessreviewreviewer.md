<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewReviewer resource type

Namespace: microsoft.graph

In an [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0), the **contactedReviewers** property contains the identities of reviewers who were contacted to complete the review.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date when the reviewer was added for the access review. |
| displayName | String | Name of reviewer. |
| id | String | Identifier of the reviewer. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| userPrincipalName | String | User principal name of the reviewer. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewReviewer",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String",
  "userPrincipalName": "String"
}
```
