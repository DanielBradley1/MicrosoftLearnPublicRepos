<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-16 -->

# hardwareOathTokenAuthenticationMethodDevice resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Exposes hardware OATH devices in the directory. For more information, see \[Hardware OATH tokens\]\(/entra/identity/authentication/concept-authentication-oath-tokens#oath-hardware-tokens-preview\].

Inherits from [authenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethoddevice?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authenticationmethoddevice-list-hardwareoathdevices?view=graph-rest-beta) | [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) collection | List all hardware OATH tokens in the inventory. |
| [Create](https://learn.microsoft.com/en-us/graph/api/authenticationmethoddevice-post-hardwareoathdevices?view=graph-rest-beta) | [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) | Create a new hardwareOathTokenAuthenticationMethodDevice object. |
| [Create one or more objects](https://learn.microsoft.com/en-us/graph/api/authenticationmethoddevice-update?view=graph-rest-beta) | [authenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethoddevice?view=graph-rest-beta) | Create one or more [authenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethoddevice?view=graph-rest-beta) objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/hardwareoathtokenauthenticationmethoddevice-get?view=graph-rest-beta) | [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) | Read the properties and relationships of a [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/hardwareoathtokenauthenticationmethoddevice-update?view=graph-rest-beta) | [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) | Update the properties of a [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/authenticationmethoddevice-delete-hardwareoathdevices?view=graph-rest-beta) | None | Delete an [authenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethoddevice?view=graph-rest-beta) object. Token needs to be unassigned first. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | User the token is assigned to. Nullable. Supports `$filter` \(`eq`\). |
| displayName | String | Name that can be provided to the hardware OATH token. Inherited from [authenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethoddevice?view=graph-rest-beta). |
| hashFunction | hardwareOathTokenHashFunction | Hash function of the hardrware token. The possible values are: `hmacsha1` or `hmacsha256`. Default value is: `hmacsha1`. Supports `$filter` \(`eq`\). |
| id | String | Unique identifier of the hardware OATH token. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastUsedDateTime | DateTimeOffset | The date and time the authentication method was last used by the user. Read-only. Optional. This optional value is `null` if the authentication method doesn't populate it. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| manufacturer | String | Manufacturer name of the hardware token. Supports `$filter` \(`eq`\). |
| model | String | Model name of the hardware token. Supports `$filter` \(`eq`\). |
| secretKey | String | Secret key of the specific hardware token, provided by the vendor. |
| serialNumber | String | Serial number of the specific hardware token, often found on the back of the device. Supports `$select` and `$filter` \(`eq`\). |
| status | hardwareOathTokenStatus | Status of the hardware OATH token.The possible values are: `available`, `assigned`, `activated`, `failedActivation`. Supports `$filter`\(`eq`\). |
| timeIntervalInSeconds | Int32 | Refresh interval of the 6-digit verification code, in seconds. The possible values are: 30 or 60. Supports `$filter` \(`eq`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignTo | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) | Assign the hardware OATH token to a user. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.hardwareOathTokenAuthenticationMethodDevice",
  "id": "String (identifier)",
  "lastUsedDateTime": "String (timestamp)",
  "displayName": "String",
  "serialNumber": "String",
  "manufacturer": "String",
  "model": "String",
  "secretKey": "String",
  "timeIntervalInSeconds": "Integer",
  "status": "String",
  "assignedTo": {
    "@odata.type": "microsoft.graph.identity"
  },
  "hashFunction": "String"
}
```
