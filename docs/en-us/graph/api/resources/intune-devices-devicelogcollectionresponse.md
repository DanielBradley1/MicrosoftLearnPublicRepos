<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceLogCollectionResponse resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Log Collection request entity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceLogCollectionResponses](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicelogcollectionresponse-list?view=graph-rest-1.0) | [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) collection | List properties and relationships of the [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) objects. |
| [Get deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicelogcollectionresponse-get?view=graph-rest-1.0) | [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) | Read properties and relationships of the [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) object. |
| [Create deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicelogcollectionresponse-create?view=graph-rest-1.0) | [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) | Create a new [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) object. |
| [Delete deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicelogcollectionresponse-delete?view=graph-rest-1.0) | None | Deletes a [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0). |
| [Update deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicelogcollectionresponse-update?view=graph-rest-1.0) | [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) | Update the properties of a [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) object. |
| [createDownloadUrl action](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicelogcollectionresponse-createdownloadurl?view=graph-rest-1.0) | String |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier in the form of tenantId\_deviceId\_requestId. |
| status | [appLogUploadState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-apploguploadstate?view=graph-rest-1.0) | Indicates the status for the app log collection request if it is pending, completed or failed, Default is pending. The possible values are: `pending`, `completed`, `failed`, `unknownFutureValue`. |
| managedDeviceId | Guid | Indicates Intune device unique identifier. |
| requestedDateTimeUTC | DateTimeOffset | The DateTime of the request. |
| receivedDateTimeUTC | DateTimeOffset | The DateTime the request was received. |
| initiatedByUserPrincipalName | String | The UPN for who initiated the request. |
| expirationDateTimeUTC | DateTimeOffset | The DateTime of the expiration of the logs. |
| sizeInKB | Double | The size of the logs in KB. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| enrolledByUser | String | The User Principal Name \(UPN\) of the user that enrolled the device. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceLogCollectionResponse",
  "id": "String (identifier)",
  "status": "String",
  "managedDeviceId": "Guid",
  "requestedDateTimeUTC": "String (timestamp)",
  "receivedDateTimeUTC": "String (timestamp)",
  "initiatedByUserPrincipalName": "String",
  "expirationDateTimeUTC": "String (timestamp)",
  "sizeInKB": "4.2",
  "enrolledByUser": "String"
}
```
