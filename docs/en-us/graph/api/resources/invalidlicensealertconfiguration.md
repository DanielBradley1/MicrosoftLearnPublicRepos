<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/invalidlicensealertconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-20 -->

# invalidLicenseAlertConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an alert configuration that's triggered if the tenant doesn't have a valid Microsoft Entra ID P2 license required to use the PIM for Microsoft Entra roles feature.

Inherits from [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alertDefinitionId | String | The identifier of an alert definition. Inherited from [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |
| id | String | The identifier of the alert configuration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isEnabled | Boolean | `true` if the alert is enabled. Setting it to `false` disables PIM scanning the tenant to identify instances that trigger this alert. Inherited from [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta). |
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
  "@odata.type": "#microsoft.graph.invalidLicenseAlertConfiguration",
  "id": "String (identifier)",
  "alertDefinitionId": "String",
  "scopeType": "String",
  "scopeId": "String",
  "isEnabled": "Boolean"
}
```
