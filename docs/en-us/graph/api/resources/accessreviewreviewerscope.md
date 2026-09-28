<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# accessReviewReviewerScope resource type

Namespace: microsoft.graph

Use **accessReviewReviewerScope** to configure reviewers in the following properties:

- [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0): **reviewers**, **fallbackReviewers**, **backupReviewers**
- [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0): **reviewers**, **fallbackReviewers**
- [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0): **reviewers**, **fallbackReviewers**

This type is also used for [user consent requests](https://learn.microsoft.com/en-us/graph/api/resources/consentrequests-overview?view=graph-rest-1.0).

Reviewers can be specified as a static list of users \(that is, specific users, group owners, and group members\) or dynamically, in which every user is reviewed by their manager, group owners, or application owners. To create a self-review \(where users review their own access\) in Microsoft Entra access reviews, the **reviewers** property of the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) should be an empty collection.

Inherits from [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| query | String | The query specifying who will be the reviewer. |
| queryRoot | String | In the scenario where reviewers need to be specified dynamically, this property is used to indicate the relative source of the query. This property is only required if a relative query, for example, `./manager`, is specified. Possible value: `decisions`. |
| queryType | String | The type of query. Examples include `MicrosoftGraph` and `ARM`. |
| reviewerId | String | The identifier of the reviewer. |
| scopeType | accessReviewReviewerScopeType | The type of the reviewer scope. The possible values are: `user`, `group`, `self`, `manager`, `sponsor`, `resourceOwner`, `managerOrSponsor`, `unknownFutureValue`. |

For more about configuration options for **reviewers**, see [Assign reviewers to your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-reviewers-concept).

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewReviewerScope",
  "query": "String",
  "queryRoot": "String",
  "queryType": "String",
  "reviewerId": "String",
  "scopeType": "String"
}
```
