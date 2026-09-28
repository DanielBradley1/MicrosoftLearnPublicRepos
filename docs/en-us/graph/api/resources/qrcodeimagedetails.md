<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/qrcodeimagedetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-13 -->

# qrCodeImageDetails resource type

Namespace: microsoft.graph

Contains the QR code image representation data. This complex type is returned as part of the [qrCode](https://learn.microsoft.com/en-us/graph/api/resources/qrcode?view=graph-rest-1.0) resource when a QR code is created. The image data is only returned at creation time because the private key embedded in the QR code isn't stored on the server.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| binaryValue | Binary | The binary representation of the QR code image. |
| errorCorrectionLevel | [errorCorrectionLevel](#errorcorrectionlevel-values) | The error correction level of the QR code, which determines how much of the QR code can be damaged while still being readable. The possible values are: `l`, `m`, `q`, `h`, `unknownFutureValue`. |
| rawContent | Binary | The raw encoded content embedded in the QR code. |
| version | Int32 | The version number of the QR code, which determines its size and data capacity. |

### errorCorrectionLevel values

QR code error correction levels, which determine how much of the QR code can be damaged while still being readable.

| Member | Description |
| --- | --- |
| l | Low error correction level, approximately 7% data recovery capability. |
| m | Medium error correction level, approximately 15% data recovery capability. |
| q | Quartile error correction level, approximately 25% data recovery capability. |
| h | High error correction level, approximately 30% data recovery capability. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.qrCodeImageDetails",
  "binaryValue": "Binary",
  "errorCorrectionLevel": "String",
  "rawContent": "Binary",
  "version": "Integer"
}
```

## Related content

- [qrCode resource type](https://learn.microsoft.com/en-us/graph/api/resources/qrcode?view=graph-rest-1.0)
