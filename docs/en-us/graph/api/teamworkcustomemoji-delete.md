<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworkcustomemoji-delete?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Delete teamworkCustomEmoji

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Delete a [custom emoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) by display name from the teamwork messaging of the organization.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkCustomEmoji.Create | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkCustomEmoji.Create.All | Not available. |

## HTTP request

```http
DELETE /teamwork/messaging/customEmojis/{displayName}
```

## Path parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The unique display name of the custom emoji. |

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```msgraph
DELETE https://graph.microsoft.com/beta/teamwork/messaging/customEmojis/low-battery
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

## Related content

- [List customEmojis](https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-list-customemojis?view=graph-rest-beta)
- [Create teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-post-customemojis?view=graph-rest-beta)
- [Get teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/teamworkcustomemoji-get?view=graph-rest-beta)
- [teamworkCustomEmoji resource type](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta)
