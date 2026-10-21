<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannerchatmessage-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Get plannerChatMessage

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the properties and relationships of [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /me/planner/plans_v2/{planId}/tasks/{taskId}/messages/{plannerChatMessageId}
GET /users/{usersId}/planner/plans_v2/{planId}/tasks/{taskId}/messages/{plannerChatMessageId}
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

If successful, this method returns a `200 OK` response code and a [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/me/planner/plans_v2/{planId}/tasks/{taskId}/messages/{plannerChatMessageId}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.plannerChatMessage",
    "id": "260e1d70-6d06-3014-ceb0-4b020aa33c89",
    "messageType": "String",
    "content": "String",
    "properties": {
      "@odata.type": "microsoft.graph.chatMessageProperties"
    },
    "createdBy": {
      "@odata.type": "microsoft.graph.identitySet"
    },
    "createdDateTime": "String (timestamp)",
    "threadType": "String",
    "parentEntityId": "String",
    "isDeleted": "Boolean",
    "deletedTime": "String (timestamp)",
    "isEdited": "Boolean",
    "editedTime": "String (timestamp)"
  }
}
```
