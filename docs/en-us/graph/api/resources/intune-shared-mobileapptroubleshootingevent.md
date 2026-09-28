<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# mobileAppTroubleshootingEvent resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Event representing a users device application install status for device management and troubleshooting event workflows.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileAppTroubleshootingEvents](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapptroubleshootingevent-list?view=graph-rest-beta) | [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta) collection | List properties and relationships of the [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta) objects. |
| [Get mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapptroubleshootingevent-get?view=graph-rest-beta) | [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta) | Read properties and relationships of the [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta) object. |
| [Create mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapptroubleshootingevent-create?view=graph-rest-beta) | [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta) | Create a new [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta) object. |
| [Delete mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapptroubleshootingevent-delete?view=graph-rest-beta) | None | Deletes a [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta). |
| [Update mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapptroubleshootingevent-update?view=graph-rest-beta) | [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta) | Update the properties of a [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | UUID for the object. |
| **Troubleshooting** |  |  |
| additionalInformation | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keyvaluepair?view=graph-rest-beta) collection | A set of string key and string value pairs which provides additional information on the Troubleshooting event Inherited from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-beta) |
| applicationId | String | Intune application identifier. |
| correlationId | String | ID used for tracing the failure in the service. |
| eventDateTime | DateTimeOffset | Time when the event occurred . |
| eventName | String | Event Name corresponding to the Troubleshooting Event. Optional |
| history | [mobileAppTroubleshootingHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileapptroubleshootinghistoryitem?view=graph-rest-beta) collection | Intune Mobile Application Troubleshooting History Item |
| managedDeviceIdentifier | String | Device identifier created or collected by Intune. |
| troubleshootingErrorDetails | [deviceManagementTroubleshootingErrorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingerrordetails?view=graph-rest-beta) | Object containing detailed information about the error and its remediation. Inherited from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-beta) |
| userId | String | Identifier for the user that tried to enroll the device. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| **Device management** |  |  |
| appLogCollectionRequests | [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-beta) collection | The collection property of AppLogUploadRequest. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppTroubleshootingEvent",
  "id": "String (identifier)",
  "eventDateTime": "String (timestamp)",
  "correlationId": "String",
  "troubleshootingErrorDetails": {
    "@odata.type": "microsoft.graph.deviceManagementTroubleshootingErrorDetails",
    "context": "String",
    "failure": "String",
    "failureDetails": "String",
    "remediation": "String",
    "resources": [
      {
        "@odata.type": "microsoft.graph.deviceManagementTroubleshootingErrorResource",
        "text": "String",
        "link": "String"
      }
    ]
  },
  "eventName": "String",
  "additionalInformation": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "String",
      "value": "String"
    }
  ],
  "managedDeviceIdentifier": "String",
  "userId": "String",
  "applicationId": "String",
  "history": [
    {
      "@odata.type": "microsoft.graph.mobileAppTroubleshootingHistoryItem",
      "occurrenceDateTime": "String (timestamp)"
    }
  ]
}
```
