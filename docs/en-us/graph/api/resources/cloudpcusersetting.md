<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# cloudPcUserSetting resource type

Namespace: microsoft.graph

Represents a Cloud PC user setting.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-usersettings?view=graph-rest-1.0) | [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) collection | Get a list of [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-usersettings?view=graph-rest-1.0) | [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) | Create a new [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudpcusersetting-get?view=graph-rest-1.0) | [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) | Read the properties and relationships of a [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/cloudpcusersetting-update?view=graph-rest-1.0) | [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) | Update the properties of a [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/cloudpcusersetting-delete?view=graph-rest-1.0) | None | Delete a [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) object. |
| [Assign](https://learn.microsoft.com/en-us/graph/api/cloudpcusersetting-assign?view=graph-rest-1.0) | None | Assign a [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) to user groups. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the setting was created. The timestamp type represents the date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | The setting name displayed in the user interface. |
| id | String | Unique identifier for the Cloud PC user setting. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the setting was last modified. The timestamp type represents the date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| localAdminEnabled | Boolean | Indicates whether the local admin option is enabled. The default value is `false`. To enable the local admin option, change the setting to `true`. If the local admin option is enabled, the end user can be an admin of the Cloud PC device. |
| resetEnabled | Boolean | Indicates whether an end user is allowed to reset their Cloud PC. When `true`, the user is allowed to reset their Cloud PC. When `false`, end-user initiated reset is not allowed. The default value is `false`. |
| restorePointSetting | [cloudPcRestorePointSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcrestorepointsetting?view=graph-rest-1.0) | Defines how frequently a restore point is created that is, a snapshot is taken\) for users' provisioned Cloud PCs \(default is 12 hours\), and whether the user is allowed to restore their own Cloud PCs to a backup made at a specific point in time. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [cloudPcUserSettingAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingassignment?view=graph-rest-1.0) collection | Represents the set of Microsoft 365 groups and security groups in Microsoft Entra ID that have **cloudPCUserSetting** assigned. Returned only on `$expand`. For an example, see [Get cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/cloudpcusersetting-get?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcUserSetting",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",  
  "lastModifiedDateTime": "String (timestamp)",
  "localAdminEnabled": "Boolean",
  "resetEnabled": "Boolean",
  "restorePointSetting": {"@odata.type": "microsoft.graph.cloudPcRestorePointSetting"}
}
```
