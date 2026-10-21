<!-- Source: https://learn.microsoft.com/en-us/graph/api/checklistitemv4-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Get checklistItemV4

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the properties and relationships of [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /me/planner/plans_v2/{planId}/tasks/{taskId}/checklist/{checklistItemV4Id}
GET /users/{usersId}/planner/plans_v2/{planId}/tasks/{taskId}/checklist/{checklistItemV4Id}
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/me/planner/plans_v2/{planId}/tasks/{taskId}/checklist/{checklistItemV4Id}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.checklistItemV4",
    "id": "0d03366e-da38-ca6d-a60b-f3f6d8a68345",
    "displayName": "String",
    "isChecked": "Boolean",
    "createdBy": {
      "@odata.type": "microsoft.graph.identitySet"
    },
    "lastModifiedBy": {
      "@odata.type": "microsoft.graph.identitySet"
    },
    "lastModifiedDateTime": "String (timestamp)",
    "completedBy": {
      "@odata.type": "microsoft.graph.identitySet"
    },
    "completedDateTime": "String (timestamp)",
    "capabilities": {
      "@odata.type": "microsoft.graph.checklistCapability"
    },
    "extensions": {
      "@odata.type": "microsoft.graph.extensionFieldCollection"
    }
  }
}
```
