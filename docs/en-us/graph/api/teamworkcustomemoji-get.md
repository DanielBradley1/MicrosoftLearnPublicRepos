<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworkcustomemoji-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Get teamworkCustomEmoji

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a single [custom emoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) or the raw image content of a custom emoji by display name from the teamwork messaging of the organization.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkCustomEmoji.Read | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkCustomEmoji.Read.All | Not available. |

## HTTP request

```http
GET /teamwork/messaging/customEmojis/{displayName}
GET /teamwork/messaging/customEmojis/{displayName}/$value
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

If successful, this method returns a `200 OK` response code and a [teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) object or the binary content of the custom emoji in the response body.

## Examples

### Example 1: Get a custom emoji

The following example shows how to get a custom emoji by display name.

#### Request

The following example shows a request.

```msgraph
GET https://graph.microsoft.com/beta/teamwork/messaging/customEmojis/low-battery
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#teamwork/messaging/customEmojis/$entity",
    "id": "01ZPGUWVOZAD7SNI6IYPC3QOQWMDMZQO6U",
    "displayName": "low-battery",
    "contentBytes": "iVBORw0KGgoAAAANSUhEUgAAA...",
    "contentType": "image/png",
    "createdDateTime": "2024-12-11T20:25:18.4809Z",
    "createdBy": {
        "user": {
            "id": "670374fa-3b0e-4a3b-9d33-0e1bc5ff1956",
            "displayName": "Adele Vance"
        }
    }
}
```

### Example 2: Get the raw image content of a custom emoji

The following example shows how to get the raw image content of a custom emoji by display name.

#### Request

The following example shows a request.

```msgraph
GET https://graph.microsoft.com/beta/teamwork/messaging/customEmojis/low-battery/$value
```

#### Response

The following example shows the response. The `Content-Type` response header specifies the media type.

```http
HTTP/1.1 200 OK
Content-Type: image/png

...binary data...
```

## Related content

- [List customEmojis](https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-list-customemojis?view=graph-rest-beta)
- [Create teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-post-customemojis?view=graph-rest-beta)
- [Delete teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/teamworkcustomemoji-delete?view=graph-rest-beta)
- [teamworkCustomEmoji resource type](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta)
