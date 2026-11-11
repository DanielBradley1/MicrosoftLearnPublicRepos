<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-07 -->

# Update teamworkChannelTag

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the display name or description of a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by the specified channel.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkTag.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkTag.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /teams/{team-id}/channels/{channel-id}/tags/{teamworkChannelTag-id}
```

> **Note:** Use the team that hosts the channel and a tag ID returned for that channel.

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
| description | String | Optional. The description of the tag. Set the value to `null` to clear the description. |
| displayName | String | Optional. A nonblank tag name with a maximum length of 40 characters. |

## Response

If successful, this method returns a `200 OK` response code and an updated [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/teams/6f2c8b4e-91d3-4a7f-b5e2-0c8d3a9f1e67/channels/19%3Ae3a7c8d14b2f4f6e9a0d5c71b8e2f945%40thread.tacv2/tags/ZDRmNmExYjgtMmM5My00ZTU3LThhMGQtNmIxZjNlOWMyYTc0IyMxOTplM2E3YzhkMTRiMmY0ZjZlOWEwZDVjNzFiOGUyZjk0NUB0aHJlYWQudGFjdjIjI2tQN3ZYbTJRYQ
Content-Type: application/json

{
  "displayName": "Design reviewers",
  "description": null
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.teamworkChannelTag",
  "id": "ZDRmNmExYjgtMmM5My00ZTU3LThhMGQtNmIxZjNlOWMyYTc0IyMxOTplM2E3YzhkMTRiMmY0ZjZlOWEwZDVjNzFiOGUyZjk0NUB0aHJlYWQudGFjdjIjI2tQN3ZYbTJRYQ",
  "teamId": "6f2c8b4e-91d3-4a7f-b5e2-0c8d3a9f1e67",
  "displayName": "Design reviewers",
  "description": null,
  "memberCount": 1,
  "tagType": "standard",
  "channelId": "19:e3a7c8d14b2f4f6e9a0d5c71b8e2f945@thread.tacv2"
}
```
