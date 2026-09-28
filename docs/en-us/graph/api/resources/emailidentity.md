<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# emailIdentity resource type

Namespace: microsoft.graph

Represents the email identity of a user.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the user. Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). |
| email | String | Email address of the user. |
| id | String | The unique identifier for the user. Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.emailIdentity",
  "displayName": "String",
  "email": "String",
  "id": "String (identifier)"
}
```
