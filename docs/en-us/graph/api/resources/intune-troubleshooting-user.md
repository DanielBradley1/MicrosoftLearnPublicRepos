<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-user?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# user resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List users](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-user-list?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-user?view=graph-rest-1.0) collection | List properties and relationships of the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-user?view=graph-rest-1.0) objects. |
| [Get user](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-user-get?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-user?view=graph-rest-1.0) | Read properties and relationships of the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-user?view=graph-rest-1.0) object. |
| [Create user](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-user-create?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-user?view=graph-rest-1.0) | Create a new [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-user?view=graph-rest-1.0) object. |
| [Delete user](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-user-delete?view=graph-rest-1.0) | None | Deletes a [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-user?view=graph-rest-1.0). |
| [Update user](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-user-update?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-user?view=graph-rest-1.0) | Update the properties of a [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-user?view=graph-rest-1.0) object. |
| [getManagedDevicesWithAppFailures function](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-user-getmanageddeviceswithappfailures?view=graph-rest-1.0) | String collection | Retrieves the list of devices with failed apps |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the user |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deviceManagementTroubleshootingEvents | [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) collection | The list of troubleshooting events for this user. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.user",
  "id": "String (identifier)"
}
```
