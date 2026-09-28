<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/shiftsrolepermission?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# shiftsRolePermission resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents permissions for a role in a Shifts schedule.

Note

This API is used to grant Shifts app capabilities to frontline managers on their teams; it doesn't grant permissions to access Microsoft Graph endpoints.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedResourceActions | String collection | The permissions that are allowed for a role. Permissions that aren't in this collection are disabled. |

### Supported allowedResourceActions values

| Value | Description |
| :--- | :--- |
| `CanModifyShiftRequestsCapabilities` | Roles with this permission have the capability to modify the settings to enable or disable open shifts, swap shifts, and request and offer shifts for their team. |
| `CanModifyTimeClockCapabilities` | Roles with this permission enabled have the capability to modify the settings to enable or disable time clock setting for their team. |
| `CanModifyTimeClockGeoFencingSettings` | Roles with this permission enabled have the capability to enable or disable time clock location detection setting for their team. |
| `CanModifyTimeOffRequestsCapabilities` | Roles with this permission enabled have the capability to enable or disable time off requests setting for their team. |
| `CanModifyTimeOffReasons` | Roles with this permission enabled have the capability to add, edit, and delete time off reasons for their team. |
| `CanModifySchedulingGroups` | Roles with this permission enabled have the capability to add, edit, and delete groups in Shifts. Regardless of the value of this permission, users that have an owner role have the capability to add and delete team members on the groups. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.shiftsRolePermission",
  "allowedResourceActions": [
    "String"
  ]
}
```
