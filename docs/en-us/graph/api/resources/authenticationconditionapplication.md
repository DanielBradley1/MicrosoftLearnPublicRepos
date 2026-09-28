<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditionapplication?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-07 -->

# authenticationConditionApplication resource type

Namespace: microsoft.graph

An object representing the application that will be triggered for an authenticationEventListener. The object is the service principal instance in the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authenticationconditionsapplications-list-includeapplications?view=graph-rest-1.0) | [authenticationConditionApplication](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditionapplication?view=graph-rest-1.0) collection | List listeners associated with an external identities self-service sign-up user flow. |
| [Add](https://learn.microsoft.com/en-us/graph/api/authenticationconditionsapplications-post-includeapplications?view=graph-rest-1.0) | None | List listeners associated with an external identities self-service sign-up user flow. |
| [Remove](https://learn.microsoft.com/en-us/graph/api/authenticationconditionapplication-delete?view=graph-rest-1.0) | None | List listeners associated with an external identities self-service sign-up user flow. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The identifier for an application corresponding to a condition which will trigger an authenticationEventListener. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationConditionApplication",
  "appId": "String"
}
```
