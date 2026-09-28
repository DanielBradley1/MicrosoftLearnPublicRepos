<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/communicationsguestidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# communicationsGuestIdentity resource type

Namespace: microsoft.graph

Represents the identity of a participant who joined a communication without authentication.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name associated with the guest user. Inherited from **identity**. |
| email | String | The email of the guest user. |
| id | String | The unique identifier for the guest user. Inherited from **identity**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "email": "String",
  "id": "String (identifier)"
}
```
