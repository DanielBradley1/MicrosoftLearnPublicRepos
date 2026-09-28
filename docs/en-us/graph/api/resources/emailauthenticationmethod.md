<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/emailauthenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-16 -->

# emailAuthenticationMethod resource type

Namespace: microsoft.graph

Represents an email address registered to a user. Email as an authentication method is available only for self-service password reset \(SSPR\). Users may only have one email authentication method.

This is a derived type that inherits from the [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) resource type.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authentication-list-emailmethods?view=graph-rest-1.0) | [emailAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/emailauthenticationmethod?view=graph-rest-1.0) collection | Retrieve a list of a user's email authentication methods. Users may only have one email authentication method. |
| [Add](https://learn.microsoft.com/en-us/graph/api/authentication-post-emailmethods?view=graph-rest-1.0) | [emailAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/emailauthenticationmethod?view=graph-rest-1.0) | Create a user's **emailAuthenticationMethod** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/emailauthenticationmethod-get?view=graph-rest-1.0) | [emailAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/emailauthenticationmethod?view=graph-rest-1.0) | Retrieve the properties of the user's **emailAuthenticationMethod** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/emailauthenticationmethod-update?view=graph-rest-1.0) | None | Update the properties of a user's **emailAuthenticationMethod** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/emailauthenticationmethod-delete?view=graph-rest-1.0) | None | Delete a user's **emailAuthenticationMethod** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emailAddress | String | The email address registered to this user. |
| id | String | The identifier of the email address registered to this user. The ID is always `3ddfcfc8-9383-446f-83cc-3ab9be4be18f`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.emailAuthenticationMethod",
  "emailAddress": "String",
  "id": "String (identifier)"
}
```
