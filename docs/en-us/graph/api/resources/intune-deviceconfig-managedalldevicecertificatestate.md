<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedAllDeviceCertificateState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedAllDeviceCertificateStates](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-managedalldevicecertificatestate-list?view=graph-rest-beta) | [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta) collection | List properties and relationships of the [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta) objects. |
| [Get managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-managedalldevicecertificatestate-get?view=graph-rest-beta) | [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta) | Read properties and relationships of the [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta) object. |
| [Create managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-managedalldevicecertificatestate-create?view=graph-rest-beta) | [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta) | Create a new [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta) object. |
| [Delete managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-managedalldevicecertificatestate-delete?view=graph-rest-beta) | None | Deletes a [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta). |
| [Update managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-managedalldevicecertificatestate-update?view=graph-rest-beta) | [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta) | Update the properties of a [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| certificateRevokeStatus | [certificateRevocationStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-certificaterevocationstatus?view=graph-rest-beta) | Revoke status. Possible values are: `none`, `pending`, `issued`, `failed`, `revoked`. |
| certificateRevokeStatusLastChangeDateTime | DateTimeOffset | The time the revoke status was last changed |
| managedDeviceDisplayName | String | Device display name |
| userPrincipalName | String | User principal name |
| certificateExpirationDateTime | DateTimeOffset | Certificate expiry date |
| certificateIssuerName | String | Issuer |
| certificateThumbprint | String | Thumbprint |
| certificateSerialNumber | String | Serial number |
| certificateSubjectName | String | Certificate subject name |
| certificateKeyUsages | Int32 | Key Usage |
| certificateExtendedKeyUsages | String | Enhanced Key Usage |
| certificateIssuanceDateTime | DateTimeOffset | Issuance date |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAllDeviceCertificateState",
  "id": "String (identifier)",
  "certificateRevokeStatus": "String",
  "certificateRevokeStatusLastChangeDateTime": "String (timestamp)",
  "managedDeviceDisplayName": "String",
  "userPrincipalName": "String",
  "certificateExpirationDateTime": "String (timestamp)",
  "certificateIssuerName": "String",
  "certificateThumbprint": "String",
  "certificateSerialNumber": "String",
  "certificateSubjectName": "String",
  "certificateKeyUsages": 1024,
  "certificateExtendedKeyUsages": "String",
  "certificateIssuanceDateTime": "String (timestamp)"
}
```
