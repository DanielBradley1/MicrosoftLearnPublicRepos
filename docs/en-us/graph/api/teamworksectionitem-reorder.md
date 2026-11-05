<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworksectionitem-reorder?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# teamworkSectionItem: reorder

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Reorder the items in a user-defined section in a user's teamwork. The section must have **sortType** set to `userDefinedCustomOrder`, and the **itemsOrder** collection must contain every item ID returned by [List items](https://learn.microsoft.com/en-us/graph/api/teamworksection-list-items?view=graph-rest-beta), exactly once.

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
POST /me/teamwork/sections/{teamworkSection-id}/items/reorder
POST /users/{user-id}/teamwork/sections/{teamworkSection-id}/items/reorder
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameter that is required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| itemsOrder | String collection | The complete ordered list of item IDs in the section. Include every ID returned by [List items](https://learn.microsoft.com/en-us/graph/api/teamworksection-list-items?view=graph-rest-beta), exactly once. Required. |

## Response

If successful, this action returns a `200 OK` response code and a [teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) collection in the response body, in the requested order.

The following errors are possible.

| Response code | Message |
| :--- | :--- |
| `400 Bad Request` | The **itemsOrder** property is missing, empty, exceeds the supported maximum, or contains null, empty, or duplicate IDs. |
| `400 Bad Request` | The reorder list doesn't contain every item in the section exactly once, or it contains an item ID that isn't in the section. |
| `403 Forbidden` | This section is system-generated and can't be modified. Reorder items only in user-defined sections. |
| `404 Not Found` | The specified section wasn't found. |
| `409 Conflict` | Reordering is only supported when the section **sortType** is `userDefinedCustomOrder`. [Update the section](https://learn.microsoft.com/en-us/graph/api/teamworksection-update?view=graph-rest-beta) to use this sort type, then retry. |
| `409 Conflict` | The items can't be reordered because of a concurrent change, such as the deletion of the target section. [List items](https://learn.microsoft.com/en-us/graph/api/teamworksection-list-items?view=graph-rest-beta) in the section again and retry. |

## Examples

### Request

The following example reorders three items in the "Project Alpha" section.

```http
POST https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items/reorder
Content-Type: application/json

{
  "itemsOrder": [
    "19:meeting_MTUxMjg0OGItZTY3MC00NTkyLTg1NzMtZTVkZTcyZDU5ZGVi@thread.v2",
    "19:978e3806-38a4-4104-a07f-57abfa8cdf9a_bdf9c93b-12ea-4e8f-8383-d0ca66d5ff48@unq.gbl.spaces",
    "19:94961b6eacc04e2392e34709c66cb610@thread.v2"
  ]
}
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
      "@odata.type": "#microsoft.graph.teamworkSectionItem",
      "@odata.etag": "\"1742515210\"",
      "id": "19:meeting_MTUxMjg0OGItZTY3MC00NTkyLTg1NzMtZTVkZTcyZDU5ZGVi@thread.v2",
      "itemType": "meeting",
      "lastModifiedDateTime": "2026-08-06T14:40:00Z"
    },
    {
      "@odata.type": "#microsoft.graph.teamworkSectionItem",
      "@odata.etag": "\"1742515210\"",
      "id": "19:978e3806-38a4-4104-a07f-57abfa8cdf9a_bdf9c93b-12ea-4e8f-8383-d0ca66d5ff48@unq.gbl.spaces",
      "itemType": "channel",
      "lastModifiedDateTime": "2026-08-06T14:40:00Z"
    },
    {
      "@odata.type": "#microsoft.graph.teamworkSectionItem",
      "@odata.etag": "\"1742515210\"",
      "id": "19:94961b6eacc04e2392e34709c66cb610@thread.v2",
      "itemType": "chat",
      "lastModifiedDateTime": "2026-08-06T14:40:00Z"
    }
  ]
}
```
