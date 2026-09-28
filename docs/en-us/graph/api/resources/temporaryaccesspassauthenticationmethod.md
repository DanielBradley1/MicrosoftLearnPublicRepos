<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-16 -->

# temporaryAccessPassAuthenticationMethod resource type

Namespace: microsoft.graph

Represents a Temporary Access Pass registered to a user. A Temporary Access Pass is a time-limited passcode that serves as a strong credential and allows onboarding of passwordless credentials. The availability and settings that can be configured for the **temporaryAccessPassAuthenticationMethod** depends on the [Temporary Access Pass methods policy](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethodconfiguration?view=graph-rest-1.0).

This is a derived type that inherits from the [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) resource type.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authentication-list-temporaryaccesspassmethods?view=graph-rest-1.0) | [temporaryAccessPassAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0) collection | Retrieve a list of a user's **temporaryAccessPassAuthenticationMethod** objects and their properties. Users can only have one Temporary Access Pass authentication method. |
| [Create](https://learn.microsoft.com/en-us/graph/api/authentication-post-temporaryaccesspassmethods?view=graph-rest-1.0) | [temporaryAccessPassAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0) | Create a user's **temporaryAccessPassAuthenticationMethod** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/temporaryaccesspassauthenticationmethod-get?view=graph-rest-1.0) | [temporaryAccessPassAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0) | Retrieve the properties of the user's **temporaryAccessPassAuthenticationMethod** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/temporaryaccesspassauthenticationmethod-delete?view=graph-rest-1.0) | None | Delete a user's **temporaryAccessPassAuthenticationMethod** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the Temporary Access Pass was created. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0). |
| id | String | The identifier of the Temporary Access Pass registered to this user. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isUsable | Boolean | The state of the authentication method that indicates whether it's currently usable by the user. |
| isUsableOnce | Boolean | Determines whether the pass is limited to a one-time use. If `true`, the pass can be used once; if `false`, the pass can be used multiple times within the Temporary Access Pass lifetime. |
| lifetimeInMinutes | Int32 | The lifetime of the Temporary Access Pass in minutes starting at **startDateTime**. Must be between 10 and 43200 inclusive \(equivalent to 30 days\). |
| methodUsabilityReason | String | Details about the usability state \(**isUsable**\). Reasons can include: `EnabledByPolicy`, `DisabledByPolicy`, `Expired`, `NotYetValid`, `OneTimeUsed`. |
| startDateTime | DateTimeOffset | The date and time when the Temporary Access Pass becomes available to use and when **isUsable** is `true` is enforced. |
| temporaryAccessPass | String | The Temporary Access Pass used to authenticate. Returned only on creation of a new **temporaryAccessPassAuthenticationMethod** object; Hidden in subsequent read operations and returned as `null` with GET. |

## Relationships

None.

The following JSON representation shows the resource type. The following is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.temporaryAccessPassAuthenticationMethod",
  "id": "String (identifier)",
  "temporaryAccessPass": "String",
  "createdDateTime": "String (timestamp)",
  "startDateTime": "String (timestamp)",
  "lifetimeInMinutes": "Integer",
  "isUsableOnce": "Boolean",
  "isUsable": "Boolean",
  "methodUsabilityReason": "String"
}
```
