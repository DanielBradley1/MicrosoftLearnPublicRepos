<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# unifiedRoleManagementAlertConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that exposes the tenant-specific configurations of a [security alert](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalert?view=graph-rest-beta) that can be updated or modified in [Privileged Identity Management \(PIM\) for Microsoft Entra roles](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-beta).

This abstract type is inherited by the following derived types:

- [invalidLicenseAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/invalidlicensealertconfiguration?view=graph-rest-beta)
- [noMfaOnRoleActivationAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/nomfaonroleactivationalertconfiguration?view=graph-rest-beta)
- [redundantAssignmentAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redundantassignmentalertconfiguration?view=graph-rest-beta)
- [rolesAssignedOutsidePrivilegedIdentityManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/rolesassignedoutsideprivilegedidentitymanagementalertconfiguration?view=graph-rest-beta)
- [sequentialActivationRenewalsAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/sequentialactivationrenewalsalertconfiguration?view=graph-rest-beta)
- [staleSignInAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/stalesigninalertconfiguration?view=graph-rest-beta)
- [tooManyGlobalAdminsAssignedToTenantAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/toomanyglobaladminsassignedtotenantalertconfiguration?view=graph-rest-beta)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

For more information about working with security alerts for Microsoft Entra roles using PIM APIs, see [Manage security alerts for Microsoft Entra roles using PIM APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/how-to-pim-alerts).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rolemanagementalert-list-alertconfigurations?view=graph-rest-beta) | [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta) collection | Get a list of the [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalertconfiguration-get?view=graph-rest-beta) | [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta) | Read the properties and relationships of an [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalertconfiguration-update?view=graph-rest-beta) | [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta) | Update the properties of an [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alertDefinitionId | String | The identifier of an alert definition. Supports `$filter` \(`eq`, `ne`\). |
| id | String | The identifier of the alert configuration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isEnabled | Boolean | `true` if the alert is enabled. Setting it to `false` disables PIM scanning the tenant to identify instances that trigger the alert. |
| scopeId | String | The identifier of the scope to which the alert is related. Only `/` is supported to represent the tenant scope. Supports `$filter` \(`eq`, `ne`\). |
| scopeType | String | The type of scope where the alert is created. `DirectoryRole` is the only currently supported scope type for Microsoft Entra roles. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| alertDefinition | [unifiedRoleManagementAlertDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta) | The definition of the alert that contains its description, impact, and measures to mitigate or prevent it. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleManagementAlertConfiguration",
  "id": "String (identifier)",
  "alertDefinitionId": "String",
  "scopeType": "String",
  "scopeId": "String",
  "isEnabled": "Boolean"
}
```

## Related content

- [Manage security alerts for Microsoft Entra roles using PIM APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/how-to-pim-alerts).
