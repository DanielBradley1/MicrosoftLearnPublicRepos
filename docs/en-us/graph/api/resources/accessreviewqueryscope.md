<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewqueryscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewQueryScope resource type

Namespace: microsoft.graph

Use **accessReviewQueryScope** to configure what is reviewed in the following properties:

- [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0): **scope**, **instanceEnumerationScope**
- [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0): **scopes**

To scope an access review to inactive users, see [accessReviewInactiveUsersQueryScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinactiveusersqueryscope?view=graph-rest-1.0).

Inherits from [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| query | String | The query representing what will be reviewed in an access review. |
| queryRoot | String | In the scenario where reviewers need to be specified dynamically, this property is used to indicate the relative source of the query. This property is only required if a relative query is specified. For example, `./manager`. |
| queryType | String | Indicates the type of query. Types include `MicrosoftGraph` and `ARM`. |

Specifying the **@odata.type** type property with the value `#microsoft.graph.accessReviewQueryScope` is highly recommended. For more about configuration options for **scope** using **accessReviewQueryScope**, see [Configure the scope of your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept).

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewQueryScope",
  "query": "String",
  "queryRoot": "String",
  "queryType": "String"
}
```
