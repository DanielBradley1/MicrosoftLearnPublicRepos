<!-- Source: https://learn.microsoft.com/en-us/graph/api/userassignment-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Update userAssignment

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a userAssignment object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /me/planner/plans_v2/{planId}/tasks/{taskId}/userAssignments/{userAssignmentId}
PATCH /users/{usersId}/planner/plans_v2/{planId}/tasks/{taskId}/userAssignments/{userAssignmentId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| user | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | Identity of the user assigned to the task. Required. |
| assignedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) that made the assignment. Optional. |
| assignedDateTime | DateTimeOffset | Date and time the assignment was made. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [userAssignment](https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/me/planner/plans_v2/{planId}/tasks/{taskId}/userAssignments/{userAssignmentId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.userAssignment",
  "user": {
    "@odata.type": "microsoft.graph.identity"
  },
  "assignedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "assignedDateTime": "2026-06-10T08:00:00Z"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.userAssignment",
  "id": "aec6cd49-aa47-7b42-5079-0a5b5197edd1",
  "user": {
    "@odata.type": "microsoft.graph.identity"
  },
  "assignedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "assignedDateTime": "String (timestamp)",
  "capabilities": {
    "@odata.type": "microsoft.graph.userAssignmentCapability"
  }
}
```
