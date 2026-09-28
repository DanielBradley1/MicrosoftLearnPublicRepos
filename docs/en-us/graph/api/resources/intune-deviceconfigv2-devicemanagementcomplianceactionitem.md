<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactionitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementComplianceActionItem resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Scheduled Action for Rule

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementComplianceActionItems](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcomplianceactionitem-list?view=graph-rest-beta) | [deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactionitem?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactionitem?view=graph-rest-beta) objects. |
| [Get deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcomplianceactionitem-get?view=graph-rest-beta) | [deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactionitem?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactionitem?view=graph-rest-beta) object. |
| [Create deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcomplianceactionitem-create?view=graph-rest-beta) | [deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactionitem?view=graph-rest-beta) | Create a new [deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactionitem?view=graph-rest-beta) object. |
| [Delete deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcomplianceactionitem-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactionitem?view=graph-rest-beta). |
| [Update deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcomplianceactionitem-update?view=graph-rest-beta) | [deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactionitem?view=graph-rest-beta) | Update the properties of a [deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactionitem?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of this setting within the policy which contains it. Automatically generated. |
| gracePeriodHours | Int32 | Number of hours to wait till the action will be enforced. Valid values 0 to 8760 |
| actionType | [deviceManagementComplianceActionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactiontype?view=graph-rest-beta) | What action to take. Possible values are: `noAction`, `notification`, `block`, `retire`, `wipe`, `removeResourceAccessProfiles`, `pushNotification`, `remoteLock`. |
| notificationTemplateId | String | What notification Message template to use |
| notificationMessageCCList | String collection | A list of group IDs to speicify who to CC this notification message to. This collection can contain a maximum of 100 elements. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementComplianceActionItem",
  "id": "String (identifier)",
  "gracePeriodHours": 1024,
  "actionType": "String",
  "notificationTemplateId": "String",
  "notificationMessageCCList": [
    "String"
  ]
}
```
