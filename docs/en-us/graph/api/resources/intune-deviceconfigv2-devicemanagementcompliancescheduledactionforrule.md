<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementComplianceScheduledActionForRule resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Scheduled Action for Rule

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementComplianceScheduledActionForRules](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule-list?view=graph-rest-beta) | [deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta) objects. |
| [Get deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule-get?view=graph-rest-beta) | [deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta) object. |
| [Create deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule-create?view=graph-rest-beta) | [deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta) | Create a new [deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta) object. |
| [Delete deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta). |
| [Update deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule-update?view=graph-rest-beta) | [deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta) | Update the properties of a [deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of this setting within the policy which contains it. Automatically generated. |
| ruleName | String | Name of the rule which this scheduled action applies to. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| scheduledActionConfigurations | [deviceManagementComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactionitem?view=graph-rest-beta) collection | The list of scheduled action configurations for this compliance policy. This collection can contain a maximum of 100 elements. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementComplianceScheduledActionForRule",
  "id": "String (identifier)",
  "ruleName": "String"
}
```
