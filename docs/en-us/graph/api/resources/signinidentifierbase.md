<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# signInIdentifierBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the base type for sign-in identifiers that enable users to authenticate with alternative identifiers such as email addresses, usernames, or custom identifiers like account numbers or employee IDs. This is an abstract type that serves as the foundation for specific sign-in identifier implementations.

This is an abstract type from which the following types are derived.

- [upnSignInIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/upnsigninidentifier?view=graph-rest-beta) resource type
- [emailSignInIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/emailsigninidentifier?view=graph-rest-beta) resource type
- [usernameSignInIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/usernamesigninidentifier?view=graph-rest-beta) resource type
- [customUsernameSignInIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/customusernamesigninidentifier?view=graph-rest-beta) resource type

For more information, see [Sign in with an alias or username \(preview\)](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/signinidentifierbase-get?view=graph-rest-beta) | [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta) | Read the properties and relationships of [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/signinidentifierbase-update?view=graph-rest-beta) | [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta) | Update the properties of a signInIdentifierBase object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/signinidentifierbase-delete?view=graph-rest-beta) | None | Delete a signInIdentifierBase object. Supported only for the customUsernameSignInIdentifier derived type. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Indicates whether this sign-in identifier type is enabled for user authentication in the tenant. |
| name | String | The unique name identifier for this sign-in identifier configuration. Possible values include: `Email`, `UPN`, `Username`, `CustomUsername1`, `CustomUsername2`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.signInIdentifierBase",
  "name": "String (identifier)",
  "isEnabled": "Boolean"
}
```
