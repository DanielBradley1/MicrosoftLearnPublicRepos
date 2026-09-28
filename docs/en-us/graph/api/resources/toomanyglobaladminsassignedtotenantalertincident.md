<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/toomanyglobaladminsassignedtotenantalertincident?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-20 -->

# tooManyGlobalAdminsAssignedToTenantAlertIncident resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details of an alert incident that is triggered if there are too many accounts assigned the Global Administrator role in the tenant. [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#global-administrator) is the highest privileged role in Microsoft Entra ID. If an account with global administrator privileges is compromised, the malicious actor has permissions for almost all actions in the tenant, which puts the entire tenant at risk.

The threshold that triggers this incident when its reached is defined in the [tooManyGlobalAdminsAssignedToTenantAlertConfiguration resource type](https://learn.microsoft.com/en-us/graph/api/resources/toomanyglobaladminsassignedtotenantalertconfiguration?view=graph-rest-beta).

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
| id | String | The identifier for the alert incident. For example, it could be a role assignment ID if the incident represents a role assignment. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
  "id": "String (identifier)",
  "assigneeId": "String",
  "assigneeDisplayName": "String",
  "assigneeUserPrincipalName": "String"
}
```
