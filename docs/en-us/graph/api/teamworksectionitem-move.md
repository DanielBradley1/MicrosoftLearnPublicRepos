<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworksectionitem-move?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-04 -->

# teamworkSectionItem: move

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Move an [item](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) from one user-defined [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) to another user-defined section in a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta). Each item can belong to only one section at a time. This action removes the item from its current section and adds it to the target section.

Note

To move an item to a different user-defined section, we recommend that you use the [Add teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/teamworksection-post-items?view=graph-rest-beta) API. The **add** request moves the item if it's in another user-defined section.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkSection.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkSection.ReadWrite.All | Teamwork.Migrate.All |

## HTTP request

```http
POST /users/{user-id}/teamwork/sections/{teamworkSection-id}/items/{teamworkSectionItem-id}/move
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| targetSectionId | String | The ID of the section to move the item to. Required. |

## Response

If successful, this action returns a `200 OK` response code and a [teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) in the response body that represents the item in the target section.

The following errors are possible.

| Response code | Message |
| :--- | :--- |
| `400 Bad Request` | The **targetSectionId** property is required and must not be empty. |
| `400 Bad Request` | The source and target sections must be different. |
| `403 Forbidden` | This section is system-generated and can't be modified. Items can't be moved into or out of system-defined sections by using this action. |
| `404 Not Found` | The specified section wasn't found, or the specified item wasn't found in this section. |
| `409 Conflict` | The section can't be updated because of a concurrent change. Retry the request. |

## Examples

### Request

The following example shows a request to move a chat from the "Favorites" section to the "Project Alpha" section.

```http
POST https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items/19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2/move
Content-type: application/json

{
  "targetSectionId": "c3d4e5f6-a7b8-9012-cdef-123456789012"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.teamworkSectionItem",
  "@odata.etag": "\"1742515210\"",
  "id": "19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2",
  "itemType": "chat",
  "createdDateTime": "2026-03-08T10:30:00Z",
  "lastModifiedDateTime": null
}
```
