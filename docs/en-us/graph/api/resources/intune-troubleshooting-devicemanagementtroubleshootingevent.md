<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementTroubleshootingEvent resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Event representing an general failure.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementTroubleshootingEvents](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-devicemanagementtroubleshootingevent-list?view=graph-rest-1.0) | [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) collection | List properties and relationships of the [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) objects. |
| [Get deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-devicemanagementtroubleshootingevent-get?view=graph-rest-1.0) | [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) | Read properties and relationships of the [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) object. |
| [Create deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-devicemanagementtroubleshootingevent-create?view=graph-rest-1.0) | [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) | Create a new [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) object. |
| [Delete deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-devicemanagementtroubleshootingevent-delete?view=graph-rest-1.0) | None | Deletes a [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0). |
| [Update deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-devicemanagementtroubleshootingevent-update?view=graph-rest-1.0) | [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) | Update the properties of a [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | UUID for the object |
| eventDateTime | DateTimeOffset | Time when the event occurred . |
| correlationId | String | Id used for tracing the failure in the service. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementTroubleshootingEvent",
  "id": "String (identifier)",
  "eventDateTime": "String (timestamp)",
  "correlationId": "String"
}
```
