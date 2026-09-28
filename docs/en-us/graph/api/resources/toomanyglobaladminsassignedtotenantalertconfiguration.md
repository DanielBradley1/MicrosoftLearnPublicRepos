<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/toomanyglobaladminsassignedtotenantalertconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-20 -->

# tooManyGlobalAdminsAssignedToTenantAlertConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an alert configuration that is triggered if too many accounts in the tenant are assigned the Global Administrator Microsoft Entra role. [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#global-administrator) is the highest privileged role in Microsoft Entra ID. If an account with global administrator privileges is compromised, the malicious actor has permissions for almost all actions in the tenant, which puts the whole system at risk.

Triggered if two different criteria are met, and you can configure both of them. First, you need to reach a certain threshold of Global administrator role assignments. Second, a certain percentage of your total role assignments must be Global administrators. If you only meet one of these measurements, the alert doesn't appear.

Inherits from [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alertDefinitionId | String | The identifier of an alert definition. Inherited from [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |
| globalAdminCountThreshold | Int32 | The threshold for the number of accounts assigned the Global Administrator role in the tenant. Triggers an alert if the number of global administrators in the tenant reaches or crosses this threshold value. |
| id | String | The identifier of the alert configuration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isEnabled | Boolean | `true` if the alert is enabled. Setting it to `false` disables PIM scanning the tenant to identify instances that trigger this alert. Inherited from [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta). |
| percentageOfGlobalAdminsOutOfRolesThreshold | Int32 | Threshold of the percentage of global administrators out of all the role assignments in the tenant. Triggers an alert if the percentage in the tenant reaches or crosses this threshold value. |
| scopeId | String | The identifier of the scope to which the alert is related. Only `/` is supported to represent the tenant scope. Inherited from [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |
| scopeType | String | The type of scope where the alert is created. `DirectoryRole` is the only currently supported scope type for Microsoft Entra roles. Inherited from [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| alertDefinition | [unifiedRoleManagementAlertDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta) | The definition of the alert that contains its description, impact, and measures to mitigate or prevent it. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration",
  "id": "String (identifier)",
  "alertDefinitionId": "String",
  "scopeType": "String",
  "scopeId": "String",
  "isEnabled": "Boolean",
  "globalAdminCountThreshold": "Integer",
  "percentageOfGlobalAdminsOutOfRolesThreshold": "Integer"
}
```
