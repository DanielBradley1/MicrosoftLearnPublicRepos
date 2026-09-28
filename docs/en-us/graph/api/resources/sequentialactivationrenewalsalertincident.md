<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sequentialactivationrenewalsalertincident?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-20 -->

# sequentialActivationRenewalsAlertIncident resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an alert incident that is triggered if a user activates the same privileged role multiple times within the last 30 days. The threshold that triggers this alert when it's reached is defined in the [sequentialActivationRenewalsAlertConfiguration resource type](https://learn.microsoft.com/en-us/graph/api/resources/sequentialactivationrenewalsalertconfiguration?view=graph-rest-beta).

Inherits from [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activationCount | Int32 | The length of sequential activation of the same role. |
| assigneeDisplayName | String | Display name of the subject that the incident applies to. |
| assigneeId | String | The identifier of the subject that the incident applies to. |
| assigneeUserPrincipalName | String | User principal name of the subject that the incident applies to. Applies to user principals. |
| id | String | The identifier for an alert incident. For example, it could be a role assignment id if the incident represents a role assignment Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |
| roleDefinitionId | String | The identifier for the [directory role definition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) that's in scope of this incident. |
| roleDisplayName | String | The display name for the [directory role](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta). |
| roleTemplateId | String | The globally unique identifier for the [directory role](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta). |
| sequenceEndDateTime | DateTimeOffset | End date time of the sequential activation event. |
| sequenceStartDateTime | DateTimeOffset | Start date time of the sequential activation event. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sequentialActivationRenewalsAlertIncident",
  "id": "String (identifier)",
  "roleTemplateId": "String",
  "roleDisplayName": "String",
  "roleDefinitionId": "String",
  "assigneeId": "String",
  "assigneeDisplayName": "String",
  "assigneeUserPrincipalName": "String",
  "activationCount": "Integer",
  "sequenceStartDateTime": "String (timestamp)",
  "sequenceEndDateTime": "String (timestamp)"
}
```
