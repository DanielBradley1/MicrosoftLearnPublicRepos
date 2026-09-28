<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-applevpptokentroubleshootingevent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# appleVppTokenTroubleshootingEvent resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Event representing an Apple Vpp Token Troubleshooting Event.

Inherits from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List appleVppTokenTroubleshootingEvents](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-applevpptokentroubleshootingevent-list?view=graph-rest-beta) | [appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-applevpptokentroubleshootingevent?view=graph-rest-beta) collection | List properties and relationships of the [appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-applevpptokentroubleshootingevent?view=graph-rest-beta) objects. |
| [Get appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-applevpptokentroubleshootingevent-get?view=graph-rest-beta) | [appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-applevpptokentroubleshootingevent?view=graph-rest-beta) | Read properties and relationships of the [appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-applevpptokentroubleshootingevent?view=graph-rest-beta) object. |
| [Create appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-applevpptokentroubleshootingevent-create?view=graph-rest-beta) | [appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-applevpptokentroubleshootingevent?view=graph-rest-beta) | Create a new [appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-applevpptokentroubleshootingevent?view=graph-rest-beta) object. |
| [Delete appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-applevpptokentroubleshootingevent-delete?view=graph-rest-beta) | None | Deletes a [appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-applevpptokentroubleshootingevent?view=graph-rest-beta). |
| [Update appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-applevpptokentroubleshootingevent-update?view=graph-rest-beta) | [appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-applevpptokentroubleshootingevent?view=graph-rest-beta) | Update the properties of a [appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-applevpptokentroubleshootingevent?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | UUID for the object Inherited from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-beta) |
| eventDateTime | DateTimeOffset | Time when the event occurred . Inherited from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-beta) |
| correlationId | String | Id used for tracing the failure in the service. Inherited from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-beta) |
| troubleshootingErrorDetails | [deviceManagementTroubleshootingErrorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingerrordetails?view=graph-rest-beta) | Object containing detailed information about the error and its remediation. Inherited from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-beta) |
| eventName | String | Event Name corresponding to the Troubleshooting Event. It is an Optional field Inherited from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-beta) |
| additionalInformation | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-keyvaluepair?view=graph-rest-beta) collection | A set of string key and string value pairs which provides additional information on the Troubleshooting event Inherited from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-beta) |
| tokenId | String | Apple Volume Purchase Program Token Identifier. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.appleVppTokenTroubleshootingEvent",
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
  "tokenId": "String"
}
```
