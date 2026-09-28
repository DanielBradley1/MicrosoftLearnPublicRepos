<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceComplianceActionItem resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Scheduled Action Configuration

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceComplianceActionItems](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceactionitem-list?view=graph-rest-1.0) | [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0) collection | List properties and relationships of the [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0) objects. |
| [Get deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceactionitem-get?view=graph-rest-1.0) | [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0) | Read properties and relationships of the [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0) object. |
| [Create deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceactionitem-create?view=graph-rest-1.0) | [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0) | Create a new [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0) object. |
| [Delete deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceactionitem-delete?view=graph-rest-1.0) | None | Deletes a [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0). |
| [Update deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceactionitem-update?view=graph-rest-1.0) | [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0) | Update the properties of a [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| gracePeriodHours | Int32 | Number of hours to wait till the action will be enforced. Valid values 0 to 8760 |
| actionType | [deviceComplianceActionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactiontype?view=graph-rest-1.0) | What action to take. The possible values are: `noAction`, `notification`, `block`, `retire`, `wipe`, `removeResourceAccessProfiles`, `pushNotification`. |
| notificationTemplateId | String | What notification Message template to use |
| notificationMessageCCList | String collection | A list of group IDs to speicify who to CC this notification message to. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceComplianceActionItem",
  "id": "String (identifier)",
  "gracePeriodHours": 1024,
  "actionType": "String",
  "notificationTemplateId": "String",
  "notificationMessageCCList": [
    "String"
  ]
}
```
