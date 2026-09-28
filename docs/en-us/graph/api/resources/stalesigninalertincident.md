<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/stalesigninalertincident?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-20 -->

# staleSignInAlertIncident resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an alert incident that is triggered if there are accounts in a privileged role that haven't signed into Microsoft Entra ID within a specified time period.

The threshold that triggers this alert when it's reached is defined in the [staleSignInAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/stalesigninalertconfiguration?view=graph-rest-beta) resource type.

Inherits from [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assigneeDisplayName | String | Display name of the subject that the incident applies to. |
| assigneeId | String | The identifier of the subject that the incident applies to. |
| assigneeUserPrincipalName | String | User principal name of the subject that the incident applies to. Applies to user principals. |
| assignmentCreatedDateTime | DateTimeOffset | Date and time of assignment creation. |
| id | String | The identifier for an alert incident. For example, it could be a role assignment id if the incident represents a role assignment Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |
| lastSignInDateTime | DateTimeOffset | Date and time of last sign in. |
| roleDefinitionId | String | The identifier for the [directory role definition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) that's in scope of this incident. |
| roleDisplayName | String | The display name for the [directory role](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta). |
| roleTemplateId | String | The globally unique identifier for the [directory role](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.staleSignInAlertIncident",
  "id": "String (identifier)",
  "roleTemplateId": "String",
  "roleDisplayName": "String",
  "roleDefinitionId": "String",
  "assigneeId": "String",
  "assigneeDisplayName": "String",
  "assigneeUserPrincipalName": "String",
  "assignmentCreatedDateTime": "String (timestamp)",
  "lastSignInDateTime": "String (timestamp)"
}
```
