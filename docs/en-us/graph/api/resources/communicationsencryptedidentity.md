<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/communicationsencryptedidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# communicationsEncryptedIdentity resource type

Namespace: microsoft.graph

Represents the identity of a user whose underlying identity isn't available to the application due to privacy restrictions. For example, in a group call, participants other than the one who invited a Skype consumer user don't have access to the identity of that user in the call roster.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name associated with the user. Inherited from **identity**. |
| id | String | The user's encrypted identifier. Inherited from **identity**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "id": "String (identifier)"
}
```
