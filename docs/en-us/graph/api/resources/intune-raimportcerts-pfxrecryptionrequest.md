<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxrecryptionrequest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# pfxRecryptionRequest resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List pfxRecryptionRequests](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-pfxrecryptionrequest-list?view=graph-rest-beta) | [pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxrecryptionrequest?view=graph-rest-beta) collection | List properties and relationships of the [pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxrecryptionrequest?view=graph-rest-beta) objects. |
| [Get pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-pfxrecryptionrequest-get?view=graph-rest-beta) | [pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxrecryptionrequest?view=graph-rest-beta) | Read properties and relationships of the [pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxrecryptionrequest?view=graph-rest-beta) object. |
| [Create pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-pfxrecryptionrequest-create?view=graph-rest-beta) | [pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxrecryptionrequest?view=graph-rest-beta) | Create a new [pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxrecryptionrequest?view=graph-rest-beta) object. |
| [Delete pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-pfxrecryptionrequest-delete?view=graph-rest-beta) | None | Deletes a [pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxrecryptionrequest?view=graph-rest-beta). |
| [Update pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-pfxrecryptionrequest-update?view=graph-rest-beta) | [pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxrecryptionrequest?view=graph-rest-beta) | Update the properties of a [pfxRecryptionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-pfxrecryptionrequest?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| tenantId | Guid |  |
| userId | Guid |  |
| deviceId | Guid |  |
| profileId | Guid |  |
| thumbprint | String |  |
| deviceKeyThumbprint | String |  |
| status | Int32 |  |
| sourceType | Int32 |  |
| createdTime | DateTimeOffset |  |
| lastModifiedTime | DateTimeOffset |  |
| isDeleted | Boolean |  |
| eTag | String |  |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.pfxRecryptionRequest",
  "tenantId": "Guid",
  "userId": "Guid",
  "deviceId": "Guid",
  "profileId": "Guid",
  "thumbprint": "String",
  "deviceKeyThumbprint": "String",
  "status": 1024,
  "sourceType": 1024,
  "createdTime": "String (timestamp)",
  "lastModifiedTime": "String (timestamp)",
  "isDeleted": true,
  "eTag": "String"
}
```
