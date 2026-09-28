<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowshelloforbusinessauthenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-28 -->

# windowsHelloForBusinessAuthenticationMethod resource type

Namespace: microsoft.graph

A representation of a Windows Hello for Business authentication method registered to a user. Windows Hello for Business is a sign-in authentication method for Windows devices.

This is a derived type that inherits from the [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) resource type.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/windowshelloforbusinessauthenticationmethod-list?view=graph-rest-1.0) | [windowsHelloForBusinessAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/windowshelloforbusinessauthenticationmethod?view=graph-rest-1.0) collection | Get a list of the [windowsHelloForBusinessAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/windowshelloforbusinessauthenticationmethod?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/windowshelloforbusinessauthenticationmethod-get?view=graph-rest-1.0) | [windowsHelloForBusinessAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/windowshelloforbusinessauthenticationmethod?view=graph-rest-1.0) | Read the properties and relationships of a [windowsHelloForBusinessAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/windowshelloforbusinessauthenticationmethod?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/windowshelloforbusinessauthenticationmethod-delete?view=graph-rest-1.0) | None | Deletes a [windowsHelloForBusinessAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/windowshelloforbusinessauthenticationmethod?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time that this Windows Hello for Business key was registered. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0). |
| displayName | String | The name of the device on which Windows Hello for Business is registered |
| id | String | A unique identifier for this authentication method. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) |
| keyStrength | authenticationMethodKeyStrength | Key strength of this Windows Hello for Business key. The possible values are: `normal`, `weak`, `unknown`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| device | [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) | The registered device on which this Windows Hello for Business key resides. Supports `$expand`.  <br>  <br>When you get a user's Windows Hello for Business registration information, this property is returned only on a single GET and when you specify `?$expand`. For example, GET `/users/admin@contoso.com/authentication/windowsHelloForBusinessMethods/_jpuR-TGZtk6aQCLF3BQjA2?$expand=device`. |

The following JSON representation shows the resource type. The following is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsHelloForBusinessAuthenticationMethod",
  "displayName": "String",
  "createdDateTime": "String",
  "id": "String (Identifier)",
  "keyStrength": {"@odata.type": "microsoft.graph.authenticationMethodKeyStrength"}
}
```
