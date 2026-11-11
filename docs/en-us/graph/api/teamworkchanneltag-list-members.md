<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-list-members?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-07 -->

# List channel tag members

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) objects assigned to a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by the specified channel.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkTag.Read | TeamworkTag.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkTag.Read.All | TeamworkTag.ReadWrite.All |

## HTTP request

```http
GET /teams/{team-id}/channels/{channel-id}/tags/{teamworkChannelTag-id}/members
```

> **Note:** Use the team that hosts the channel and a tag ID returned for that channel.

## Optional query parameters

This method supports the `$select`, `$filter`, `$top`, and `$skiptoken` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters). The default and maximum page size is 100.

For example, use `$filter=userId eq '8c1e6b52-3d4a-4f97-b0e8-5a2c7f9d1e36'` to filter members by user.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) objects in the response body.

If the response includes **@odata.nextLink**, use that URL unchanged to request the next page. A page can contain fewer results than requested, including no results, and still include a next-page link. Continue until **@odata.nextLink** is absent.

This method also returns a `400 Bad Request` response if the value of the `$top` OData query parameter is greater than 100.

Use the returned member IDs with [Get channel tag member](https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-get-members?view=graph-rest-beta) and [Delete channel tag member](https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-delete-members?view=graph-rest-beta). Don't substitute channel membership IDs from other APIs.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/teams/6f2c8b4e-91d3-4a7f-b5e2-0c8d3a9f1e67/channels/19%3Ae3a7c8d14b2f4f6e9a0d5c71b8e2f945%40thread.tacv2/tags/ZDRmNmExYjgtMmM5My00ZTU3LThhMGQtNmIxZjNlOWMyYTc0IyMxOTplM2E3YzhkMTRiMmY0ZjZlOWEwZDVjNzFiOGUyZjk0NUB0aHJlYWQudGFjdjIjI2tQN3ZYbTJRYQ/members
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
      "@odata.type": "#microsoft.graph.teamworkTagMember",
      "id": "MCMjMiMjZDRmNmExYjgtMmM5My00ZTU3LThhMGQtNmIxZjNlOWMyYTc0IyMxOTplM2E3YzhkMTRiMmY0ZjZlOWEwZDVjNzFiOGUyZjk0NUB0aHJlYWQudGFjdjIjIzhjMWU2YjUyLTNkNGEtNGY5Ny1iMGU4LTVhMmM3ZjlkMWUzNg",
      "displayName": "Adele Vance",
      "tenantId": "d4f6a1b8-2c93-4e57-8a0d-6b1f3e9c2a74",
      "userId": "8c1e6b52-3d4a-4f97-b0e8-5a2c7f9d1e36"
    }
  ]
}
```
