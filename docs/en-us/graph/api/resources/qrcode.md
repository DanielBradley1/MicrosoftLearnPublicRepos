<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/qrcode?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-13 -->

# qrCode resource type

Namespace: microsoft.graph

Represents a QR code credential used with the [qrCodePinAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethod?view=graph-rest-1.0). A QR code contains a unique identifier \(GUID\), a private key, and the user's UPN. The private key is only returned once at the time of creation and isn't stored on the server.

There are two types of QR codes:

- **Standard QR code**: A long-lived QR code intended to be printed on a user's badge. The default lifetime is 365 days, with a maximum of 395 days \(13 months\). The expiration date can be edited after creation.
- **Temporary QR code**: A short-lived QR code \(1-12 hours\) created when a user forgets their badge. Temporary QR codes can't be edited after creation.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create or update](https://learn.microsoft.com/en-us/graph/api/qrcode-update?view=graph-rest-1.0) | [qrCode](https://learn.microsoft.com/en-us/graph/api/resources/qrcode?view=graph-rest-1.0) | Create a new standard QR code or update the expiration date of an existing one. |
| [Get](https://learn.microsoft.com/en-us/graph/api/qrcode-get?view=graph-rest-1.0) | [qrCode](https://learn.microsoft.com/en-us/graph/api/resources/qrcode?view=graph-rest-1.0) | Read the properties of a user's QR code. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/qrcode-delete?view=graph-rest-1.0) | None | Delete a QR code. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the QR code was created. Read-only. |
| expireDateTime | DateTimeOffset | The date and time when the QR code expires. For standard QR codes, the lifetime is in days with a maximum of 395 days \(13 months\) and a default of 365 days. For temporary QR codes, the lifetime must be between 1-12 hours. The **expireDateTime** can be edited for standard QR codes but not for temporary QR codes. |
| id | String | The unique identifier \(GUID\) of the QR code. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |
| image | [qrCodeImageDetails](https://learn.microsoft.com/en-us/graph/api/resources/qrcodeimagedetails?view=graph-rest-1.0) | The QR code image data. This property is only returned at the time of creating or resetting the QR code because the private key isn't stored on the server. |
| lastUsedDateTime | DateTimeOffset | The date and time when the QR code was last successfully used for authentication. Read-only. |
| startDateTime | DateTimeOffset | The date and time when the QR code becomes available for use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.qrCode",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "expireDateTime": "String (timestamp)",
  "image": {"@odata.type": "microsoft.graph.qrCodeImageDetails"},
  "lastUsedDateTime": "String (timestamp)",
  "startDateTime": "String (timestamp)"
}
```

## Related content

- [qrCodePinAuthenticationMethod resource type](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethod?view=graph-rest-1.0)
- [qrCodeImageDetails resource type](https://learn.microsoft.com/en-us/graph/api/resources/qrcodeimagedetails?view=graph-rest-1.0)
