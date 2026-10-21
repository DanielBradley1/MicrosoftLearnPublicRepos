<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resourceaccountkeyauthenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-14 -->

# resourceAccountKeyAuthenticationMethod resource type

Namespace: microsoft.graph

Represents a resource account key credential registered on a shared device \(such as a Teams Meeting Room or Teams phone\) for passwordless authentication. Resource account keys enable shared devices to silently sign in to Microsoft Entra ID without user interaction.

Inherits from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authentication-list-resourceaccountkeyauthenticationmethods?view=graph-rest-1.0) | [resourceAccountKeyAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/resourceaccountkeyauthenticationmethod?view=graph-rest-1.0) collection | Get a list of the resourceAccountKeyAuthenticationMethod objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/resourceaccountkeyauthenticationmethod-get?view=graph-rest-1.0) | [resourceAccountKeyAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/resourceaccountkeyauthenticationmethod?view=graph-rest-1.0) | Read the properties and relationships of a resourceAccountKeyAuthenticationMethod object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/resourceaccountkeyauthenticationmethod-delete?view=graph-rest-1.0) | None | Delete a resourceAccountKeyAuthenticationMethod object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the resource account key was registered. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0). |
| displayName | String | The display name of the resource account key credential as shown in the Teams Room interface. |
| id | String | A unique identifier for this instance of an authentication method. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isUsable | Boolean | Indicates whether the method is usable for sign-in. **Returned by default.** |
| lastUsedDateTime | DateTimeOffset | The date and time when this authentication method was last used for sign-in. **Requires `$select`.** Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0). |
| methodUsabilityReason | String | The reason for the usability state. Possible values are: `EnabledByPolicy`, `DisabledByPolicy`. **Returned by default.** |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| device | [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) | The registered device on which this resource account key resides. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.resourceAccountKeyAuthenticationMethod",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "isUsable": "Boolean",
  "lastUsedDateTime": "String (timestamp)",
  "methodUsabilityReason": "String"
}
```
