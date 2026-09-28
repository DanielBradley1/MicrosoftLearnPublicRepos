<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-16 -->

# softwareOathAuthenticationMethod resource type

Namespace: microsoft.graph

Represents a software OATH token registered to a user. A software OATH token is a software-based number generator that uses the OATH Time-Based One Time Password \(TOTP\) standard for multi-factor authentication. This API won't return Microsoft Authenticator authentication method entities, though it returns an entity if Microsoft Authenticator was set up via the third-party software authenticator flow.

This resource type is a derived type that inherits from the [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) resource type.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authentication-list-softwareoathmethods?view=graph-rest-1.0) | [softwareOathAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethod?view=graph-rest-1.0) collection | Retrieve a list of a user's softwareOathAuthenticationMethod objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/softwareoathauthenticationmethod-get?view=graph-rest-1.0) | [softwareOathAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethod?view=graph-rest-1.0) | Read the properties of a user's softwareOathAuthenticationMethod object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/softwareoathauthenticationmethod-delete?view=graph-rest-1.0) | None | Delete a user's softwareOathAuthenticationMethod object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The authentication method identifier. |
| secretKey | String | The secret key of the method. Always returns `null`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.softwareOathAuthenticationMethod",
  "id": "String (identifier)",
  "secretKey": "String"
}
```
