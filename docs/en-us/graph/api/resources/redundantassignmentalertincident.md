<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redundantassignmentalertincident?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-20 -->

# redundantAssignmentAlertIncident resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an alert incident that is triggered if a user goes over a specified number of days without activating a role. Assigning users privileged roles that they don't need increases the risks of a security attack. It's also easier for security threats to remain unnoticed in accounts that aren't actively used.

The threshold that triggers this incident when it's reached is defined in the [redundantAssignmentAlertConfiguration resource type](https://learn.microsoft.com/en-us/graph/api/resources/redundantassignmentalertconfiguration?view=graph-rest-beta).

Inherits from [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assigneeDisplayName | String | Display name of the subject that the incident applies to. |
| assigneeId | String | The identifier of the subject that the incident applies to. |
| assigneeUserPrincipalName | String | User principal name of the subject that the incident applies to. Applies to user principals only. |
| id | String | The identifier for an alert incident. For example, it could be a role assignment ID if the incident represents a role assignment. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |
| lastActivationDateTime | DateTimeOffset | Date and time of the last activation of the eligible assignment. |
| roleDefinitionId | String | The identifier for the [directory role definition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) that's in scope of this incident. |
| roleDisplayName | String | The display name for the [directory role](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta). |
| roleTemplateId | String | The globally unique identifier for the [directory role](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redundantAssignmentAlertIncident",
  "id": "String (identifier)",
  "roleTemplateId": "String",
  "roleDefinitionId": "String",
  "roleDisplayName": "String",
  "assigneeId": "String",
  "assigneeDisplayName": "String",
  "assigneeUserPrincipalName": "String",
  "lastActivationDateTime": "String (timestamp)"
}
```
