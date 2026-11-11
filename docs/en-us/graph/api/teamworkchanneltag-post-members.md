<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-post-members?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-07 -->

# Create channel tag member

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) object, which assigns a user to a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by the specified channel. A tag can have up to 200 members.

Warning

Avoid adding a member while another request renames or deletes the tag. Concurrent operations can cause the member assignment to affect a different tag in the same channel.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkTag.ReadWrite.All | Not available. |

This API supports application permissions only. To create a tag with initial members by using delegated permissions, use [Create teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/channel-post-tags?view=graph-rest-beta).

## HTTP request

```http
POST /teams/{team-id}/channels/{channel-id}/tags/{teamworkChannelTag-id}/members
```

> **Note:** Use the team that hosts the channel and a tag ID returned for that channel.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) object.

The following table shows the properties that you can use when you create a **teamworkTagMember**.

| Property | Type | Description |
| :--- | :--- | :--- |
| tenantId | String | Optional. The ID of the tenant that hosts the channel. If not specified, defaults to the tenant of the request. Cross-tenant members aren't supported. |
| userId | String | Required. The user identifier, expressed as a GUID. The user must be a member of the channel. |

## Response

If successful, this method returns a `201 Created` response code and a [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) object in the response body.

This method also returns a `400 Bad Request` response code if the specified **userId** isn't a member of the channel.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/teams/6f2c8b4e-91d3-4a7f-b5e2-0c8d3a9f1e67/channels/19%3Ae3a7c8d14b2f4f6e9a0d5c71b8e2f945%40thread.tacv2/tags/ZDRmNmExYjgtMmM5My00ZTU3LThhMGQtNmIxZjNlOWMyYTc0IyMxOTplM2E3YzhkMTRiMmY0ZjZlOWEwZDVjNzFiOGUyZjk0NUB0aHJlYWQudGFjdjIjI2tQN3ZYbTJRYQ/members
Content-Type: application/json

{
  "userId": "8c1e6b52-3d4a-4f97-b0e8-5a2c7f9d1e36"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.teamworkTagMember",
  "id": "MCMjMiMjZDRmNmExYjgtMmM5My00ZTU3LThhMGQtNmIxZjNlOWMyYTc0IyMxOTplM2E3YzhkMTRiMmY0ZjZlOWEwZDVjNzFiOGUyZjk0NUB0aHJlYWQudGFjdjIjIzhjMWU2YjUyLTNkNGEtNGY5Ny1iMGU4LTVhMmM3ZjlkMWUzNg",
  "displayName": "Adele Vance",
  "tenantId": "d4f6a1b8-2c93-4e57-8a0d-6b1f3e9c2a74",
  "userId": "8c1e6b52-3d4a-4f97-b0e8-5a2c7f9d1e36"
}
```
