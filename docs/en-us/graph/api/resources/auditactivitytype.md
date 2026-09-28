<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/auditactivitytype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-01 -->

# auditActivityType resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit activity type that includes the associated Microsoft Entra service and category for a specific activity. The audit activities in the tenant are available through the [directoryAudit resource type](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-beta) and its related APIs.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/auditlogroot-list-auditactivitytypes?view=graph-rest-beta) | [auditActivityType](https://learn.microsoft.com/en-us/graph/api/resources/auditactivitytype?view=graph-rest-beta) collection | Get a list of the auditActivityType objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activity | String | Indicates the activity name or the operation name \(for example "Create User", "Add member to group"\). For a list of activities logged, refer to [Microsoft Entra audit log categories and activities](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/reference-audit-activities). Supports `$filter` \(`eq`\). |
| category | String | Indicates which resource category that's targeted by the activity. For example: `UserManagement`, `GroupManagement`, `ApplicationManagement`, `RoleManagement`. For a list of categories for activities logged, refer to [Microsoft Entra audit log categories and activities](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/reference-audit-activities). Supports `$filter` \(`eq`\). |
| id | String | The unique ID for the given audit activity type. |
| service | String | Indicates information on which service initiated the activity. For example: Self-service Password Management, Core Directory, B2C, Invited Users, Microsoft Identity Manager, Privileged Identity Management. Supports `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.auditActivityType",
  "id": "String (identifier)",
  "category": "String",
  "service": "String",
  "activity": "String"
}
```
