<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# deviceManagementConfigurationPolicyAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The DeviceManagementConfigurationPolicyAssignment entity assigns a specific DeviceManagementConfigurationPolicy to an AAD group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementConfigurationPolicyAssignments](https://learn.microsoft.com/en-us/graph/api/api/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment-list.md?view=graph-rest-beta) | [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) objects. |
| [Get deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/api/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment-get.md?view=graph-rest-beta) | [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) object. |
| [Create deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/api/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment-create.md?view=graph-rest-beta) | [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) | Create a new [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) object. |
| [Delete deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/api/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment-delete.md?view=graph-rest-beta) | None | Deletes a [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta). |
| [Update deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/api/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment-update.md?view=graph-rest-beta) | [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) | Update the properties of a [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key of the assignment. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The assignment target for the DeviceManagementConfigurationPolicy. |
| source | [deviceAndAppManagementAssignmentSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmentsource?view=graph-rest-beta) | The assignment source for the device compliance policy, direct or parcel/policySet. The possible values are: `direct`, `policySets`. |
| sourceId | String | The identifier of the source of the assignment. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationPolicyAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String",
    "targetType": "String",
    "entraObjectId": "String"
  },
  "source": "String",
  "sourceId": "String"
}
```
