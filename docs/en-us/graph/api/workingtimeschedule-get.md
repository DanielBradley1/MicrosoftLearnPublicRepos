<!-- Source: https://learn.microsoft.com/en-us/graph/api/workingtimeschedule-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# Get workingTimeSchedule

Namespace: microsoft.graph

Read the properties and relationships of a [workingTimeSchedule](https://learn.microsoft.com/en-us/graph/api/resources/workingtimeschedule?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule-WorkingTime.ReadWrite.All | Not available. |

## HTTP request

```http
GET /users/{usersId}/solutions/schedule
```

## Optional query parameters

This method doesn't support [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [workingTimeSchedule](https://learn.microsoft.com/en-us/graph/api/resources/workingtimeschedule?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/users/ccdf8279-8a3f-4c10-af1a-4a7f46b1489f/solutions/schedule
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.teams.workingTime.workingTimeSchedule",
    "id": "da5f72af-450e-56fc-10d7-afc9acb40cc0"
  }
}
```
