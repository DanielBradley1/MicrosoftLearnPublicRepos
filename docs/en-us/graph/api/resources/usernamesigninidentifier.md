<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usernamesigninidentifier?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# usernameSignInIdentifier resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a username sign-in identifier that enables users to authenticate using a simple username. This is a built-in sign-in identifier that cannot be created or deleted, but can be enabled or disabled.

Inherits from [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Indicates whether this username sign-in identifier type is enabled for user authentication in the tenant. Inherited from [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta). |
| name | String | The unique name identifier for this username sign-in identifier configuration. Always set to "Username" for this identifier type. Inherited from [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.usernameSignInIdentifier",
  "name": "String (identifier)",
  "isEnabled": "Boolean"
}
```
