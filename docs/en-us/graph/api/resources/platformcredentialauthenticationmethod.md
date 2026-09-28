<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/platformcredentialauthenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-28 -->

# platformCredentialAuthenticationMethod resource type

Namespace: microsoft.graph

Represents a platform credential instance registered to a user on Mac OS. Platform Credential is a sign-in authentication method for Mac OS devices.

This derived type inherits from the [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) resource type.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/platformcredentialauthenticationmethod-list?view=graph-rest-1.0) | [platformCredentialAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/platformcredentialauthenticationmethod?view=graph-rest-1.0) collection | Get a list of the [platformCredentialAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/platformcredentialauthenticationmethod?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/platformcredentialauthenticationmethod-get?view=graph-rest-1.0) | [platformCredentialAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/platformcredentialauthenticationmethod?view=graph-rest-1.0) | Read the properties and relationships of a [platformCredentialAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/platformcredentialauthenticationmethod?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/platformcredentialauthenticationmethod-delete?view=graph-rest-1.0) | None | Delete a [platformCredentialAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/platformcredentialauthenticationmethod?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time that this Platform Credential Key was registered. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0). |
| displayName | String | The name of the device on which Platform Credential is registered. |
| id | String | A unique identifier for this authentication method. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) |
| keyStrength | authenticationMethodKeyStrength | Key strength of this Platform Credential key. The possible values are: `normal`, `weak`, `unknown`. |
| platform | authenticationMethodPlatform | Platform on which this Platform Credential key is present. The possible values are: `unknown`, `windows`, `macOS`,`iOS`, `android`, `linux`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| device | [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) | The registered device on which this Platform Credential resides. Supports `$expand`.  <br>  <br>When you get a user's Platform Credential registration information, this property is returned only on a single GET and when you specify `?$expand`. For example, GET `/users/admin@contoso.com/authentication/platformCredentialAuthenticationMethod/_jpuR-TGZtk6aQCLF3BQjA2?$expand=device`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.platformCredentialAuthenticationMethod",
  "id": "String (Identifier)",
  "displayName": "String",
  "createdDateTime": "String (timestamp)",
  "keyStrength": {"@odata.type": "microsoft.graph.authenticationMethodKeyStrength"},
  "platform": {"@odata.type": "microsoft.graph.authenticationMethodPlatform"}
}
```
