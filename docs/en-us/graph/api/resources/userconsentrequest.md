<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userconsentrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# userConsentRequest resource type

Namespace: microsoft.graph

Represents the details of the consent request a user creates when they request to access an app or to grant permissions to an app. The details include justification for requesting access, the status of the request, and the approval details.

The user can create a consent request when an app or a permission requires admin authorization and only when the [admin consent workflow](https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0) is enabled.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/appconsentrequest-list-userconsentrequests?view=graph-rest-1.0) | [userConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/userconsentrequest?view=graph-rest-1.0) collection | Retrieve a collection of [userConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/userconsentrequest?view=graph-rest-1.0) objects for an [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/userconsentrequest-get?view=graph-rest-1.0) | [userConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/userconsentrequest?view=graph-rest-1.0) | Read the properties and relationships of a [userConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/userconsentrequest?view=graph-rest-1.0) object. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/userconsentrequest-filterbycurrentuser?view=graph-rest-1.0) | [userConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/userconsentrequest?view=graph-rest-1.0) collection | Read the properties of [userConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/userconsentrequest?view=graph-rest-1.0) objects for an [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) for which the current user is the reviewer. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalId | String | The id of the approval. This value is equal to the value of the `id`. |
| completedDateTime | DateTimeOffset | The date and time when the **status** of the request was marked as `Completed`. The date and time information uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the request. |
| createdDateTime | DateTimeOffset | The date and time when the request was created. The date and time information uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Supports `$filter` \(`eq` only\) and `$orderby`. |
| customData | String | Free text field to define any custom data for the user consent request. Not used. |
| id | String | Identifier of the request. |
| reason | String | The user's justification for requiring access to the app. Supports `$filter` \(`eq` only\) and `$orderby`. |
| status | String | The status of the user's app consent request. The possible values are: `Initializing`, `InProgress`, `Expired`, and `Completed`. Supports `$filter` \(`eq` only\) and `$orderby`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| approval | [approval](https://learn.microsoft.com/en-us/graph/api/resources/approval?view=graph-rest-1.0) | Approval decisions associated with a request. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userConsentRequest",
  "id": "String (identifier)",
  "status": "String",
  "completedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "approvalId": "String",
  "customData": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "reason": "String"
}
```
