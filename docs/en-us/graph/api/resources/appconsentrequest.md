<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# appConsentRequest resource type

Namespace: microsoft.graph

Represents the request that a user creates when they request the tenant admin for consent to access an app or to grant permissions to an app. The details include the app that the user wants access to be granted to on their behalf and the permissions that the user is requesting.

The user can create a consent request when an app or a permission requires admin authorization and only when the [admin consent workflow](https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0) is enabled.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/appconsentapprovalroute-list-appconsentrequests?view=graph-rest-1.0) | [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) collection | Retrieve a collection of [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/appconsentrequest-get?view=graph-rest-1.0) | [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) | Read the properties and relationships of an [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) object. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/appconsentrequest-filterbycurrentuser?view=graph-rest-1.0) | [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) | Read the properties of [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) objects for which the current user is the reviewer and the status of the user consent request is `InProgress`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appDisplayName | String | The display name of the app for which consent is requested. Required. Supports `$filter` \(`eq` only\) and `$orderby`. |
| appId | String | The identifier of the application. Required. Supports `$filter` \(`eq` only\) and `$orderby`. |
| id | String | The identifier of the app consent request. Required. |
| pendingScopes | [appConsentRequestScope](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequestscope?view=graph-rest-1.0) collection | A list of pending scopes waiting for approval. Required. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| userConsentRequests | [userConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/userconsentrequest?view=graph-rest-1.0) collection | A list of pending user consent requests. Supports `$filter` \(`eq`\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appConsentRequest",
  "appDisplayName": "String",
  "appId": "String",
  "id": "String (identifier)",
  "pendingScopes": [
    {
      "@odata.type": "microsoft.graph.appConsentRequestScope"
    }
  ]
}
```
