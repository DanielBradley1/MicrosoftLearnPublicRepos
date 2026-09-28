<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalert?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRoleManagementAlert resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details of a security alert in [Privileged Identity Management \(PIM\) for Microsoft Entra roles](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-beta). The alert information includes the related alert [definition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta), [configuration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta), and [incident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) collection in the tenant.

Each security alert in PIM for Microsoft Entra roles is of one of several types described in [Get security alerts for Microsoft Entra roles](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-beta#security-alerts-for-microsoft-entra-roles). You can [list](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalert-list-alertincidents?view=graph-rest-beta) details of the actual incidents of an alert using the **incidents** relationship. An alert and its related incidents are always of the same type. For example, an alert about too many global administrators in the tenant relates to incidents of the type [tooManyGlobalAdminsAssignedToTenantAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/toomanyglobaladminsassignedtotenantalertincident?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

For more information about working with security alerts for Microsoft Entra roles using PIM APIs, see [Manage security alerts for Microsoft Entra roles using PIM APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/how-to-pim-alerts).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rolemanagementalert-list-alerts?view=graph-rest-beta) | [unifiedRoleManagementAlert](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalert?view=graph-rest-beta) collection | Get a list of the [unifiedRoleManagementAlert](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalert?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalert-get?view=graph-rest-beta) | [unifiedRoleManagementAlert](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalert?view=graph-rest-beta) | Read the properties and relationships of an [unifiedRoleManagementAlert](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalert?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalert-update?view=graph-rest-beta) | [unifiedRoleManagementAlert](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalert?view=graph-rest-beta) | Update the properties of an [unifiedRoleManagementAlert](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalert?view=graph-rest-beta) object. |
| [Refresh](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalert-refresh?view=graph-rest-beta) | None | Refresh incidents on all alerts or on a single alert for Privileged Identity Management \(PIM\) for Microsoft Entra roles. |
| [Get long running operation](https://learn.microsoft.com/en-us/graph/api/longrunningoperation-get?view=graph-rest-beta) | None | Get the status of the refresh operation if it returned a **Location** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alertDefinitionId | String | The identifier of an [alert definition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |
| id | String | The identifier of the [alert configuration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta). Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| incidentCount | Int32 | The number of incidents triggered in the tenant and relating to the alert. Can only be a positive integer. |
| isActive | Boolean | `false` by default. `true` if the alert is active. |
| lastModifiedDateTime | DateTimeOffset | The date time when the alert configuration was updated or new incidents generated. |
| lastScannedDateTime | DateTimeOffset | The date time when the tenant was last scanned for incidents that trigger this alert. |
| scopeId | String | The identifier of the scope where the alert is related. `/` is the only supported one for the tenant. Supports `$filter` \(`eq`, `ne`\). |
| scopeType | String | The type of scope where the alert is created. `DirectoryRole` is the only currently supported scope type for Microsoft Entra roles. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| alertConfiguration | [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta) | The configuration of the alert in PIM for Microsoft Entra roles. Alert configurations are pre-defined and cannot be created or deleted, but some configurations can be modified. Supports `$filter` for the **isEnabled** property and `$expand`. |
| alertDefinition | [unifiedRoleManagementAlertDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta) | Contains the description, impact, and measures to mitigate or prevent the security alert from being triggered in your tenant. Supports `$expand`. |
| alertIncidents | [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) collection | Represents the incidents of this type of alert that have been triggered in Privileged Identity Management \(PIM\) for Microsoft Entra roles in the tenant. Supports `$expand`. |

The following JSON representation shows the resource type. The following is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleManagementAlert",
  "id": "String (identifier)",
  "alertDefinitionId": "String",
  "scopeId": "String",
  "scopeType": "String",
  "incidentCount": "Integer",
  "isActive": "Boolean",
  "lastModifiedDateTime": "String (timestamp)",
  "lastScannedDateTime": "String (timestamp)"
}
```

## Related content

- [Manage security alerts for Microsoft Entra roles using PIM APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/how-to-pim-alerts).
