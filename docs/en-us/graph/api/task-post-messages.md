<!-- Source: https://learn.microsoft.com/en-us/graph/api/task-post-messages?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Create plannerChatMessage

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new plannerChatMessage object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /users/{usersId}/planner/plans_v2/{planId}/tasks/{taskId}/messages
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) object.

You can specify the following properties when creating a **plannerChatMessage**.

| Property | Type | Description |
| :--- | :--- | :--- |
| messageType | plannerChatMessageType | Format of the message content. The possible values are: `richTextHtml`, `plainText`, `unknownFutureValue`. Optional. |
| content | String | Body content of the chat message. Optional. |
| properties | [chatMessageProperties](https://learn.microsoft.com/en-us/graph/api/resources/chatmessageproperties?view=graph-rest-beta) | @mentions and reactions associated with the message. Optional. |
| threadType | plannerChatThreadType | Indicates whether the message belongs to a task-level or plan-level conversation. The possible values are: `task`, `plan`, `unknownFutureValue`. Optional. |
| parentEntityId | String | ID of the task or plan the message belongs to. Optional. |
| isDeleted | Boolean | Indicates whether the message was deleted. Optional. |
| deletedTime | DateTimeOffset | Date and time the message was deleted. Optional. |
| isEdited | Boolean | Indicates whether the message was edited after it was sent. Optional. |
| editedTime | DateTimeOffset | Date and time the message was last edited. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/users/{usersId}/planner/plans_v2/{planId}/tasks/{taskId}/messages
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plannerChatMessage",
  "messageType": "plainText",
  "content": "Great progress on this task!",
  "properties": {
    "@odata.type": "microsoft.graph.chatMessageProperties"
  },
  "threadType": "task",
  "parentEntityId": "7e2b4a9d-3c61-4f8e-9a52-8d3c6f9b1a24",
  "isDeleted": false,
  "deletedTime": "2026-06-15T09:30:00Z",
  "isEdited": false,
  "editedTime": "2026-06-16T14:20:00Z"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
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
```
