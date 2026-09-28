<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethod?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-16 -->

# hardwareOathAuthenticationMethod resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Exposes the hardware OATH method on the user object. The method must first be defined by the [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) policy for it to be managed on the user object.

Inherits from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authentication-list-hardwareoathmethods?view=graph-rest-beta) | [hardwareOathAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethod?view=graph-rest-beta) collection | Get a list of the [hardwareOathAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethod?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/authentication-post-hardwareoathmethods?view=graph-rest-beta) | [hardwareOathAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethod?view=graph-rest-beta) | Create a new [hardwareOathAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethod?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/hardwareoathauthenticationmethod-get?view=graph-rest-beta) | [hardwareOathAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethod?view=graph-rest-beta) | Read the properties and relationships of a [hardwareOathAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethod?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/authentication-delete-hardwareoathmethods?view=graph-rest-beta) | None | Delete a [hardwareOathAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethod?view=graph-rest-beta) object. |
| [Activate](https://learn.microsoft.com/en-us/graph/api/hardwareoathauthenticationmethod-activate?view=graph-rest-beta) | None | Activate a hardware OATH token that is already assigned to a user. |
| [Deactivate](https://learn.microsoft.com/en-us/graph/api/hardwareoathauthenticationmethod-deactivate?view=graph-rest-beta) | None | Deactive a hardware OATH token. It remains assigned to the user. |
| [Assign](https://learn.microsoft.com/en-us/graph/api/hardwareoathtokenauthenticationmethoddevice-put-assignto?view=graph-rest-beta) | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) | Assign a user a hardware token without activating it. |
| [Assign and activate](https://learn.microsoft.com/en-us/graph/api/hardwareoathauthenticationmethod-assignandactivate?view=graph-rest-beta) | None | Assign and activate a hardware token at the same time. |
| [Assign and activate by serial number](https://learn.microsoft.com/en-us/graph/api/hardwareoathauthenticationmethod-assignandactivatebyserialnumber?view=graph-rest-beta) | None | Assign and activate a hardware token at the same time by hardware token serial number. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time the authentication method was registered to the user. Read-only. Optional. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| lastUsedDateTime | DateTimeOffset | The date and time the authentication method was last used by the user. Read-only. Optional. This optional value is `null` if the authentication method doesn't populate it. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-beta). |
| id | String | Unique identifier for the device. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| device | [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) | Exposes the hardware OATH method in the directory. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.hardwareOathAuthenticationMethod",
  "createdDateTime": "String (timestamp)",
  "lastUsedDateTime": "String (timestamp)",
  "id": "String (identifier)",
}
```
