<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applepushnotificationcertificate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# applePushNotificationCertificate resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Apple push notification certificate.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get applePushNotificationCertificate](https://learn.microsoft.com/en-us/graph/api/intune-devices-applepushnotificationcertificate-get?view=graph-rest-1.0) | [applePushNotificationCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applepushnotificationcertificate?view=graph-rest-1.0) | Read properties and relationships of the [applePushNotificationCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applepushnotificationcertificate?view=graph-rest-1.0) object. |
| [Update applePushNotificationCertificate](https://learn.microsoft.com/en-us/graph/api/intune-devices-applepushnotificationcertificate-update?view=graph-rest-1.0) | [applePushNotificationCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applepushnotificationcertificate?view=graph-rest-1.0) | Update the properties of a [applePushNotificationCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applepushnotificationcertificate?view=graph-rest-1.0) object. |
| [downloadApplePushNotificationCertificateSigningRequest function](https://learn.microsoft.com/en-us/graph/api/intune-devices-applepushnotificationcertificate-downloadapplepushnotificationcertificatesigningrequest?view=graph-rest-1.0) | String | Download Apple push notification certificate signing request |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the certificate |
| appleIdentifier | String | Apple Id of the account used to create the MDM push certificate. |
| topicIdentifier | String | Topic Id. |
| lastModifiedDateTime | DateTimeOffset | Last modified date and time for Apple push notification certificate. |
| expirationDateTime | DateTimeOffset | The expiration date and time for Apple push notification certificate. |
| certificateUploadStatus | String | The certificate upload status. |
| certificateUploadFailureReason | String | The reason the certificate upload failed. |
| certificateSerialNumber | String | Certificate serial number. This property is read-only. |
| certificate | String |  |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.applePushNotificationCertificate",
  "id": "String (identifier)",
  "appleIdentifier": "String",
  "topicIdentifier": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "certificateUploadStatus": "String",
  "certificateUploadFailureReason": "String",
  "certificateSerialNumber": "String",
  "certificate": "String"
}
```
