<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-13 -->

# qrCodePinAuthenticationMethod resource type

Namespace: microsoft.graph

Represents a QR code and PIN authentication method registered to a user. This single-factor authentication method is designed for frontline workers and combines a QR code \(equivalent to something you have\) with a PIN \(something you know\). Users enter the PIN only after successful QR code verification.

Each user can have only one active QR code PIN authentication method. The method requires both a standard QR code and a PIN to be created. Standard QR codes are intended for badges and have a configurable lifetime \(default 365 days, maximum 395 days\). Temporary QR codes can be created for situations when a user forgot their badge and have a short lifetime \(1-12 hours\).

Inherits from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/qrcodepinauthenticationmethod-get?view=graph-rest-1.0) | [qrCodePinAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethod?view=graph-rest-1.0) | Read the properties of a user's QR code PIN authentication method. |
| [Create](https://learn.microsoft.com/en-us/graph/api/authentication-put-qrcodepinmethod?view=graph-rest-1.0) | [qrCodePinAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethod?view=graph-rest-1.0) | Create a new QR code PIN authentication method for a user. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/qrcodepinauthenticationmethod-delete?view=graph-rest-1.0) | None | Delete a user's QR code PIN authentication method. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when this authentication method was created. Inherited from [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0). Read-only. |
| id | String | The unique identifier for this authentication method. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| pin | [qrPin](https://learn.microsoft.com/en-us/graph/api/resources/qrpin?view=graph-rest-1.0) | The PIN associated with this QR code authentication method. |
| standardQRCode | [qrCode](https://learn.microsoft.com/en-us/graph/api/resources/qrcode?view=graph-rest-1.0) | The standard \(long-lived\) QR code credential, typically printed on a user's badge. |
| temporaryQRCode | [qrCode](https://learn.microsoft.com/en-us/graph/api/resources/qrcode?view=graph-rest-1.0) | A temporary \(short-lived\) QR code credential, created when a user forgets their badge. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.qrCodePinAuthenticationMethod",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)"
}
```

## Related content

- [QR code PIN authentication method overview](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-authentication-methods#qr-code-pin)
- [authenticationMethod resource type](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0)
