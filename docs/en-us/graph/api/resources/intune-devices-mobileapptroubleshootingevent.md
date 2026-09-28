<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# mobileAppTroubleshootingEvent resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

MobileAppTroubleshootingEvent Entity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileAppTroubleshootingEvents](https://learn.microsoft.com/en-us/graph/api/intune-devices-mobileapptroubleshootingevent-list?view=graph-rest-1.0) | [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0) collection | List properties and relationships of the [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0) objects. |
| [Get mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-devices-mobileapptroubleshootingevent-get?view=graph-rest-1.0) | [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0) | Read properties and relationships of the [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0) object. |
| [Create mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-devices-mobileapptroubleshootingevent-create?view=graph-rest-1.0) | [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0) | Create a new [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0) object. |
| [Delete mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-devices-mobileapptroubleshootingevent-delete?view=graph-rest-1.0) | None | Deletes a [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0). |
| [Update mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-devices-mobileapptroubleshootingevent-update?view=graph-rest-1.0) | [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0) | Update the properties of a [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appLogCollectionRequests | [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0) collection | Indicates collection of App Log Upload Request. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppTroubleshootingEvent",
  "id": "String (identifier)"
}
```
