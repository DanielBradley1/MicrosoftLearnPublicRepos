<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworksection-reorder?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-04 -->

# teamworkSection: reorder

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Reorder the sections in a user's teamwork. The **sectionsOrder** collection must contain every section ID returned by [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta), exactly once. If the collection contains the *QuickViews* system section, that section must be first.

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
POST /me/teamwork/sections/reorder
POST /users/{user-id}/teamwork/sections/reorder
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
| sectionsOrder | String collection | The complete ordered list of section IDs. Include every section ID returned by [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta), exactly once. If the *QuickViews* system section is included, it must be the first ID. Required. |

## Response

If successful, this action returns a `200 OK` response code and a [teamworkSection](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) collection in the response body, in the requested order.

The following errors are possible.

| Response code | Message |
| :--- | :--- |
| `400 Bad Request` | The **sectionsOrder** property is missing, empty, exceeds the supported maximum, or contains null, empty, or duplicate IDs. |
| `400 Bad Request` | The reorder list doesn't contain every current section exactly once, contains an unknown section ID, or doesn't place the *QuickViews* system section first. |
| `404 Not Found` | The specified user wasn't found. |
| `409 Conflict` | The sections can't be reordered because of a concurrent change, such as the deletion of a section in the reorder list. [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta) again and retry with the current section IDs. |

## Examples

### Request

The following example reorders three sections for a user.

```http
POST https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/reorder
Content-Type: application/json

{
  "sectionsOrder": [
    "ce274158-f4f5-4ba7-bd18-0b2204dc1691~10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f~QuickViews",
    "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "b2c3d4e5-f6a7-8901-bcde-f12345678901"
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
      "@odata.type": "#microsoft.graph.teamworkSection",
      "@odata.etag": "\"1742515210\"",
      "id": "ce274158-f4f5-4ba7-bd18-0b2204dc1691~10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f~QuickViews",
      "displayName": "QuickViews",
      "sectionType": "systemDefined",
      "sortType": "nameAlphabetical"
    },
    {
      "@odata.type": "#microsoft.graph.teamworkSection",
      "@odata.etag": "\"1742515210\"",
      "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "displayName": "Project Alpha",
      "sectionType": "userDefined",
      "sortType": "userDefinedCustomOrder"
    },
    {
      "@odata.type": "#microsoft.graph.teamworkSection",
      "@odata.etag": "\"1742515210\"",
      "id": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
      "displayName": "Customer Escalations",
      "sectionType": "userDefined",
      "sortType": "mostRecent"
    }
  ]
}
```
