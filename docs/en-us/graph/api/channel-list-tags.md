<!-- Source: https://learn.microsoft.com/en-us/graph/api/channel-list-tags?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-07 -->

# List tags

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) objects owned by the specified channel.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkTag.Read | TeamworkTag.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkTag.Read.All | TeamworkTag.ReadWrite.All |

## HTTP request

```http
GET /teams/{team-id}/channels/{channel-id}/tags
```

> **Note:** Use the team that hosts the channel, including for shared channels.

## Optional query parameters

This method supports the `$select`, `$filter`, `$top`, and `$skiptoken` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters). The default and maximum page size is 200.

For example, use `$filter=displayName eq 'Project reviewers'` to filter tags by name.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) objects in the response body. This collection doesn't include team-owned tags. For the **General** channel, this method returns an empty collection.

If the response includes **@odata.nextLink**, use that URL unchanged to request the next page. A page can contain fewer results than requested, including no results, and still include a next-page link. Continue until **@odata.nextLink** is absent.

This method also returns a `400 Bad Request` response if the value of the `$top` OData query parameter is greater than 200.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/teams/6f2c8b4e-91d3-4a7f-b5e2-0c8d3a9f1e67/channels/19%3Ae3a7c8d14b2f4f6e9a0d5c71b8e2f945%40thread.tacv2/tags
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
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
  ]
}
```
