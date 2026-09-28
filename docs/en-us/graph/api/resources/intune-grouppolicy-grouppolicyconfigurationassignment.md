<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyConfigurationAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The group policy configuration assignment entity assigns one or more AAD groups to a specific group policy configuration.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyConfigurationAssignments](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfigurationassignment-list?view=graph-rest-beta) | [groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta) objects. |
| [Get groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfigurationassignment-get?view=graph-rest-beta) | [groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta) object. |
| [Create groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfigurationassignment-create?view=graph-rest-beta) | [groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta) | Create a new [groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta) object. |
| [Delete groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfigurationassignment-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta). |
| [Update groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfigurationassignment-update?view=graph-rest-beta) | [groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta) | Update the properties of a [groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The type of groups targeted the group policy configuration. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyConfigurationAssignment",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String",
    "targetType": "String",
    "entraObjectId": "String"
  }
}
```
