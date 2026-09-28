<!-- Source: https://learn.microsoft.com/en-us/graph/api/shiftsroledefinition-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-22 -->

# Update shiftsRoleDefinition

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update a [shiftsRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/shiftsroledefinition?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | SchedulePermissions.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | SchedulePermissions.ReadWrite.All |

## HTTP request

```http
PATCH /team/{teamId}/schedule/shiftsRoleDefinitions/{roleId}
```

## Path parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| teamId | string | Team ID to set the role definitions. |
| roleId | string | The affected role. Current supported values are `teamowner` and `scheduleowner`. |

### Supported values for roleId

| Name | Description |
| :--- | :--- |
| scheduleOwner | Sets definitions for a schedule owner. |
| teamOwner | Sets definitions for a team owner. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, supply a JSON representation of the [shiftsRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/shiftsroledefinition?view=graph-rest-beta) object.

You can specify the following properties when creating/updating a **shiftsRoleDefinition**.

| Property | Type | Description |
| :--- | :--- | :--- |
| shiftsRolePermissions | [microsoft.graph.shiftsRolePermission](https://learn.microsoft.com/en-us/graph/api/resources/shiftsrolepermission?view=graph-rest-beta) collection | Contains the definition for role permissions within a role. Required. |

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Examples

### Example 1: Set permissions for schedule owner

#### Request

The following example shows a request that enables the modification of scheduling groups and time off reasons by schedule owners.

```http
PATCH https://graph.microsoft.com/beta/team/10c2c1cc-6384-48f6-aeba-ef7486344550/schedule/shiftsRoleDefinitions/scheduleowner
Content-Type: application/json

{
  "shiftsRolePermissions": [
    {
      "allowedResourceActions": [
        "CanModifySchedulingGroups",
        "CanModifyTimeOffReasons"
      ]
    }
  ]
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Disable all permissions for schedule owner

#### Request

The following example shows a request that disables all permissions by passing an empty collection as the value for `allowedResourceActions`.

```http
PATCH https://graph.microsoft.com/beta/team/10c2c1cc-6384-48f6-aeba-ef7486344550/schedule/shiftsRoleDefinitions/scheduleowner
Content-Type: application/json

{
  "shiftsRolePermissions": [
    {
      "allowedResourceActions": []
    }
  ]
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
