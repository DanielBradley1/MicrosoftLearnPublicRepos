<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceComplianceScheduledActionForRule resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Scheduled Action for Rule

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceComplianceScheduledActionForRules](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancescheduledactionforrule-list?view=graph-rest-1.0) | [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-1.0) collection | List properties and relationships of the [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-1.0) objects. |
| [Get deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancescheduledactionforrule-get?view=graph-rest-1.0) | [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-1.0) | Read properties and relationships of the [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-1.0) object. |
| [Create deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancescheduledactionforrule-create?view=graph-rest-1.0) | [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-1.0) | Create a new [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-1.0) object. |
| [Delete deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancescheduledactionforrule-delete?view=graph-rest-1.0) | None | Deletes a [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-1.0). |
| [Update deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancescheduledactionforrule-update?view=graph-rest-1.0) | [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-1.0) | Update the properties of a [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| ruleName | String | Name of the rule which this scheduled action applies to. Currently scheduled actions are created per policy instead of per rule, thus RuleName is always set to default value PasswordRequired. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| scheduledActionConfigurations | [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem?view=graph-rest-1.0) collection | The list of scheduled action configurations for this compliance policy. Compliance policy must have one and only one block scheduled action. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceComplianceScheduledActionForRule",
  "id": "String (identifier)",
  "ruleName": "String"
}
```
