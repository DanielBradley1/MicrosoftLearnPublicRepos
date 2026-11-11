<!-- Source: https://learn.microsoft.com/en-us/graph/api/channel-post-tags?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-07 -->

# Create teamworkChannelTag

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by a channel and assign its initial members.

The **General** channel doesn't support the creation of channel-owned tags; use the [Create teamworkTag](https://learn.microsoft.com/en-us/graph/api/teamworktag-post?view=graph-rest-beta) instead.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkTag.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkTag.ReadWrite.All | Not available. |

The creation of a tag with initial members supports both delegated and application permissions. To add members after you create the tag, use [Create channel tag member](https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-post-members?view=graph-rest-beta), which supports application permissions only.

## HTTP request

```http
POST /teams/{team-id}/channels/{channel-id}/tags
```

> **Note:** Use the team that hosts the channel, including for shared channels.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) object.

The following table shows the properties that are required when you create a **teamworkChannelTag**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Optional. The description of the tag. |
| displayName | String | Required. A nonblank tag name with a maximum length of 40 characters. |
| members | [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) collection | Required. Between 1 and 25 initial members. Each member requires a **userId**, expressed as a GUID, and must be a member of the channel. The **tenantId** is optional; if specified, it must be the ID of the tenant that hosts the channel. Cross-tenant members aren't supported. |

## Response

If successful, this method returns a `201 Created` response code and a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) object in the response body.

This method also returns a `400 Bad Request` response code if a specified **userId** isn't a member of the channel.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/teams/6f2c8b4e-91d3-4a7f-b5e2-0c8d3a9f1e67/channels/19%3Ae3a7c8d14b2f4f6e9a0d5c71b8e2f945%40thread.tacv2/tags
Content-Type: application/json

{
  "displayName": "Project reviewers",
  "description": "Reviewers for the channel's project",
  "members": [
    {
      "userId": "8c1e6b52-3d4a-4f97-b0e8-5a2c7f9d1e36"
    }
  ]
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.teamworkChannelTag",
  "id": "ZDRmNmExYjgtMmM5My00ZTU3LThhMGQtNmIxZjNlOWMyYTc0IyMxOTplM2E3YzhkMTRiMmY0ZjZlOWEwZDVjNzFiOGUyZjk0NUB0aHJlYWQudGFjdjIjI2tQN3ZYbTJRYQ",
  "teamId": "6f2c8b4e-91d3-4a7f-b5e2-0c8d3a9f1e67",
  "displayName": "Project reviewers",
  "description": "Reviewers for the channel's project",
  "memberCount": 1,
  "tagType": "standard",
  "channelId": "19:e3a7c8d14b2f4f6e9a0d5c71b8e2f945@thread.tacv2"
}
```
