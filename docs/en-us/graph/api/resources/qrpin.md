<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/qrpin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-13 -->

# qrPin resource type

Namespace: microsoft.graph

Represents the PIN credential associated with a [qrCodePinAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethod?view=graph-rest-1.0). The PIN is a memorized secret that users enter after successful QR code verification.

The PIN must be between 8-20 digits, with a minimum default length of 8 digits as per NIST standards. When a PIN is created by an admin or reset, it's a temporary PIN that requires the user to change it on their next sign-in. The PIN code value is only returned at the time of creation or reset.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Reset PIN](https://learn.microsoft.com/en-us/graph/api/qrpin-updatepin?view=graph-rest-1.0) | [qrPin](https://learn.microsoft.com/en-us/graph/api/resources/qrpin?view=graph-rest-1.0) | Reset a user's PIN to a new temporary PIN that must be changed on next sign-in. |
| [Update PIN](https://learn.microsoft.com/en-us/graph/api/qrpin-update?view=graph-rest-1.0) | [qrPin](https://learn.microsoft.com/en-us/graph/api/resources/qrpin?view=graph-rest-1.0) | Update a user's PIN. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The PIN code value. This property is only returned at the time of creating or resetting the PIN. For GET operations, this property returns `null`. The PIN must be between 8-20 digits. |
| createdDateTime | DateTimeOffset | The date and time when the PIN was created. Read-only. |
| forceChangePinNextSignIn | Boolean | Indicates whether the user must change the PIN on their next sign-in. This is `true` when an admin creates or resets the PIN, and `false` after the user changes it. |
| id | String | The unique identifier for the PIN. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |
| updatedDateTime | DateTimeOffset | The date and time when the PIN was last updated. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.qrPin",
  "id": "String (identifier)",
  "code": "String",
  "createdDateTime": "String (timestamp)",
  "forceChangePinNextSignIn": "Boolean",
  "updatedDateTime": "String (timestamp)"
}
```

## Related content

- [qrCodePinAuthenticationMethod resource type](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethod?view=graph-rest-1.0)
